---
layout: post.html
title: "Путь радуги: Алгоритм распознавания движений пальцев рук на основе цветовой диффференциации (Driven by LISP)"
datetime: 12 Aug 2010 15:38
tags: [ lisp, computer-vision, functional-programming ]
---

Я немного безумный и в свободное время занялся изучением LISP'а и, чтобы сделать обучение немного интереснее, попробовал реализовать самоизобретённый алгоритм. "Алгоритм" - это, конечно, громко сказано, в нём нет ни перемножений матриц, ни сортировки массивов, ни пузырьков, ни долгой работы над оптимизацией (ни даже калибровки цветов, оправдываюсь тем, что версия учебная). И да, в статье много картинок, а в конце даже будет видео.

[Заранее ссылка на исходники](http://code.google.com/p/nijiato)

Цель проста: Определять положение всех десяти пальцев в пространстве (координаты положения и угол наклона каждого пальца в дискретный момент), выдавать эти данные через `stdout` или по сокету другой программе, а та сможет делать предположения о "гесчурах", которые совершает пользователь и соответственно им реагировать на пользовательском интерфейсе. Вдохновлением для идеи послужил ролик на хабре [про будущее интерфейсов](http://habrahabr.ru/blogs/ui_design_and_usability/95590/) и то что, как нельзя кстати, под руку попались [биндинги video4linux для Common Lisp](http://www.cliki.net/CL-V4L2) от Виталия Маяцких. Здесь я представляю вам первую часть - программу, которая определяет координаты и угол наклона пальцев. Не знаю, дойдут ли руки до написания остальных и приведения в энтерпрайзное состояние этой, если никто не сподобится поучаствовать.

Особенность этого способа в том, что он, при должной смелости, воспроизводим в домашних условиях. Для определения положений пальцев в пространстве не используется датчиков, эвристических алгоритмов и паттерн-матчинга как в OpenCV. Используются:

* Linux
* Lisp-интерпретатор, предпочтительно SBCL
* [Куча Common-Lilsp-овых пакетов](http://code.google.com/p/nijiato/wiki/RequiredCLpackages ) (хотя многие из них у вас могут быть уже установлены, если вы работаете с Lisp)
* Драйвер video4linux (`v4l2convert.so`) и поддержка GTK
* Любая веб-камера, совместимая с video4linux (у меня - Genius iSlim 300)
* Десять разноцветных бумажек, которые можно надеть на пальцы: по две красных, оранжевых, жёлтых, зелёных и голубых.

Эти бумажки и есть основа этого безумного алгоритма, без остальных частей его можно реализовать на любом языке прораммирования и на любом окружении. [Исходный код алгоритма расположен здесь](http://code.google.com/p/nijiato/source/browse/nijiato-recognition.lisp), можно следить за описанием и кодом одновременно. Lisp считается самодокументируемым языком, так что, надеюсь, всё будем понятно :).

### Ку. Исходные данные

Вначале необходимо определить цвета, при обнаружении которых программа будет понимать, что _возможно_ в этом месте находится палец. Точные цвета задавать бессмысленно, необходимо ввести какую-то дельту, узкий размах возможных значений, чтобы при необходимости в "подозрительный" регион попала и немного затенённая область и немного осветлённая, примерно того же цвета. Я задавал для каждого цвета свою собственную дельту, поскольку каждый из них обычно ведёт себя по-разному. Все мои значения "захардкожены" - определены опытным путём для определённого освещения в определённое время суток (программа хорошо работает у меня дома, при включенном свете с 20 часов до глубокой ночи, при яркости камеры по умолчанию - как раз когда я возвращаюсь с работы). Будем считать, что это учебная версия и это оправдывает меня. Можно добавить предварительную калибровку или анализирование общей освещённости кадра и "подправку" цветов в соответствии с этим значением, но сами бумажки в любом случае будут у всех разных оттенков, если только не начинать завтра же их массовое производство с идентичными цветами, привитыми им на заводе.

Итак, надеваем на каждый палец по бумажке.

![Color values](../assets/ru/nijiato-detection-of-fingers-motion-algorithm/colors.png)

На картинке RGB-компоненты представлены в диапазонах от нуля до единицы, overflow при сложении/вычитании дельты не учитывается. Кроме того, эти цвета индивидуальны для моего случая, поэтому так непохожи на идеальные.

### Ку. Первый проход. Определение участков возможного нахождения пальцев

В программе используется массив `*fingers-values*` длиной (ширина кадра * высоту кадра), каждая ячейка которого соответствует одному пикселю кадра и будет содержать число от `0` до `200`. На каждом следующем кадре этот массив полностью заполняется новыми значениями на основе проанализированных RGB-компонентов пикселей.

Так, в процессе работы алгоритма в массиве `*fingers-values*` будут находиться значения:

* Значение `0` - несоответствие пикселя ни одному из цветов плюс-минус дельта
* Значения от `1` до `49` - это значения для предполагаемых областей нахождения пальцев левой руки, по `9-10` на каждый палец.
* Значения от `50` до `99` -это значения для предполагаемых областей нахождения пальцев правой руки, по `10` на каждый палец.
* Значения больше `100` и меньше `200` - точное нахождение соответсвующего пальца, для того чтобы узнать какого - надо вычесть `100`.

Теперь можно вернуться к алгоритму, запускаем первый проход - попиксельно анализируем текущий кадр изображения.

Если пиксель не раскрашен ни одним цветом из определённых выше плюс-минус дельта, в ячейку массива `*fingers-values*` записывается `0`. Если это _предположительно_ какой-то конкретный палец (цвет пикселя совпадает с одним из предопределённых цветов), в массив записывается соответствующее число - `1-9` для большого пальца, `10-19` для указательного, `20-29` для среднего, `30-39` для безымянного и `40-49` для мизинца. Сейчас в ячейки записываются только значения `9`,`19`, `29`, `39`, `49` - я рассчитывал сделать дополнительную градацию в зависимости от того, насколько близко к "среднему" цвету оказалось значение, но это оказалось не нужно (однако диапазоны по 10 сильно помогают в дальнейшем). По умолчанию считается, что найдены пальцы левой руки. Количество найденых участков одного цвета на этом этапе никак не контролируется и не регулируется.

![Сorrespondence of colors and fingers](../assets/ru/nijiato-detection-of-fingers-motion-algorithm/values.png)

Это всё, кадр просканирован, массив заполнен, однако это только первый этап, _в массиве значения меньше `50`_.

### Ку. Второй проход. Определение координат и углов

Перед вторым проходом кадра создаётся временный массив из 10 булевых переменных `hits`, в нём мы контролируем, какие пальцы уже были определены. Теперь мы поочерёдно проходим по каждой ячейке главного массива `*fingers-values*`. Если значение текущей ячейки главного массива больше нуля и меньше `100`, то мы проверяем, не был ли такой палец уже определён, если был - то пропускаем ячейку, если нет - пытаемся сделать предположение о том, какая это может быть рука на основе координаты `x` для этой ячейки - если уже был найден такой же палец левой руки и его координата `x` оказалась больше чем текущая (но не на слишком близком расстоянии, у меня - не менее `80px`), то похоже, мы имеем дело с правой рукой, тогда мы прибавляем к текущему значению `50` и работаем с уже обновлённым.

![Distance between fingers](../assets/ru/nijiato-detection-of-fingers-motion-algorithm/distance.png)

Теперь у мы знаем руку и предположительную область нахождения пальца, осталось определить его координаты. Для этого запоминаем координаты `x` и `y` текущей точки, в цикле по углам от `0` до `pi`, с шагом, например, `pi / 20`, вычисляем координаты пикселей для каждого из лучей с соответсвующим углом, простирающихся из этой точки (в не-учебной версии заранее вычисленные относительные координаты можно и закэшировать), длина лучей равна заранее установленному числу, у меня это `31px` (включая текущий пискель, вверх и вниз по 15), а их центр расположен в текущей точке.

![Angles detection algorythm](../assets/ru/nijiato-detection-of-fingers-motion-algorithm/angles.png)

Координаты пикселей каждого из лучей однозначно соответствуют индексам соответсвующих соседних ячеек в массиве `*fingers-values*`. Оставаясь курсором на текущей точке, мы подсчитываем попиксельно для каждого из лучей количество совпавших значений (те, которые от `1` до `50`, прибавляя `50` если это правая рука), если это количество является допустимым для такой длины луча (я разрешаю ошибку в 4 пикселя, то есть совпасть должны 27 пикслей из 31-го), то бинго - **мы определили угол и положение пальца**: координаты пальца (условные) - это начальная и конечная координаты луча, угол наклона пальца - это угол луча, который совпал. Можно записать в `*hits*`, что палец найден и вывести на экран (или в `stdout`) данные.

![Smile](../assets/ru/nijiato-detection-of-fingers-motion-algorithm/smile.png)

### Ку. Возможные применения

Когда есть координаты пальцев и углы их наклона, можно анализировать практически любые "гесчуры". Правда, от анализатора будет требоваться умение "предсказывать" положения на основе предыдущих состояний - если палец скрылся из вида, то может быть рука была сжата в кулак или было совершено быстрое движение вовне кадра. Есть решаемая проблема с определением какой руке принадлежит палец, её можно решить засчёт дополнительных маркеров на ладонях рук (если не видно маркера, а пальцы идут в кадре в обратном порядке - то это тыльная сторона), как раз остаются синий и фиолетовый цвета (я их добавил на картинки для наглядности), или можно вообще не принимать во внимание для "гесчурсов", какая это рука, если недостаточно данных (в камеру видно только два пальца). Эти "гесчуры" можно использовать для управления интерфейсами как в [упомянутой статье](http://habrahabr.ru/blogs/ui_design_and_usability/95590/ ) - переноса окон, перебора картинок в альбомах, вообще управления интерфейсом, чтобы всё было как в Minority Report, при этом нужна только камера и преодоление психологического барьера, чтобы вырезать и надеть на пальцы цветные бумажки (или подобные контроллеры). Это пока что дешевле чем датчики и пока что веселее чем существующие применения Microsoft Kinect :).

**Upd.** Люди поделились со мной [этим видео](http://blog.makezine.com/archive/2010/07/gestural_interface_via_flamboyant_g.html), идея очень похожа, но у меня более чердачная версия всё равно :). И время прошло и Microsoft Kinect стал делать намного более интересные вещи, так что извини меня Microsoft Kinect :)

### Ку. Что улучшить

* Добавить калибровку, оценивать уровень освещения, ввести девайс "цветная бумажка Nijiato" в массовое производство
* Более разумно определять какую руку видно в камеру, например по дополнительной бумажке на ладони и на основе расположения пальцев (если нет бумажки - это тыльная сторона рук
* Много оптимизации:
  * можно кэшировать относительные координаты лучей
  * сделать вычисления поточными
  * можно сканировать не каждый кадр, а каждый десятый, быстрые движения при этом "додумывать" на этапе анализирования "гесчурсов"
  * ...

### Ку. Пояснения по программе

На данный момент необходимо установить и зарегистрировать в ADSF пакеты из [этого списка](http://code.google.com/p/nijiato/source/browse/requirements) (там указаны репозитории и необходимые команды), установить пакет `libv4l-dev` и `libgtkglext`. Также можно установить `rlwrap` для более удобной работы с интерпретатором. Если система 64-битная, нужно будет убрать хак из биндингов CL-V4L2, это также описано в [requirements](http://code.google.com/p/nijiato/source/browse/requirements).

После выполнения этих операций запуск прост:

    $ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so [rlwrap] sbcl
    * (load "nijiato-demo-load.lisp")

(`.so`-файл может лежать в другом месте, в зависимости от устройства и битности вашей операционной системы)

Программа использует для запуска переработанный демо-пример из `CL-V4L2`, который показывает GTK-окно и проецирует на него OpenGL-текстуру с изображением с камеры, а также позволяет считывать пиксели на каждом фрейме. FASL-версия может не запуститься, с этой проблемой я борюсь.

### Ку. Видео

И наконец видео с работой программы, при старте загружается много библиотек, можно промотать первые секунд 30. "Определённые" положения пальцев отображаются тонкой однопиксельной чёрной линией (те самые совпавшие лучи) и выводятся в консоль в читаемом виде. В середине видео не определяется два больших пальца разных рук, это из-за того, что они расстояние между ними меньше 80 пикселей, которые я задал как минимальную ширину между руками. Окно, которое берётся из камеры намеренно маленькое, чтобы программа не так сильно тормозила :).

[![Link to Vimeo video](../assets/ru/nijiato-detection-of-fingers-motion-algorithm/vimeo-video-frame.png)](http://vimeo.com/14073181)
