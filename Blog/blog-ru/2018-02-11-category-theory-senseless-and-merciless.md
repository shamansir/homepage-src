# Теория категорий — бессмысленная и беспощадная!

Вульгарус ИндефинициатусFebruary 11, 2018

  

_По каким законам развивается человек? Я — приверженец теории, что информация усваивается и раскладывается по категориям в мозгу бесконечно, всю жизнь, вслед за чередой случайных событий, мы накапливаем знания, данные — которые впредь можем применять, совершать над ними мозговые операции, преобразования — и получать посредством них новые данные. Да, есть иллюзия, что какие-то данные забываются — какие-то привычки, кажется, остаются за бортом жизненных перепетий, но на самом деле весь этот информационный груз оставляет свой след в наших кишащих серым веществом извилинах — исходные данные потеряны, но они послужили жертвенным множителем, хэшем если хотите, солью при получении новых данных — и повлияли на то, что мы сейчас из себя представляем._

  

Осмелился бы я заявить, что знаю теорию категорий? Нет, я делал множество подходов — ударялся о терминологию, которая практически нигде больше не применяется, и делал шаг назад. Много шагов, чур меня! Я открывал википедию и естественно — наблюдая пассажи про эндофункторы, бороздящие вселенную, а так же безумные формулы с символами из тех закромов юникодной таблицы, куда даже эмодзи не заходят — испытывал отвращение, которое всегда чувствовал к воинам, сражающимся на конкурсе самых скучных учебников, и закрывал не читая.

  

Сегодня, мне кажется, я сделал огромный шаг для того человечества, которое не понимает смысла теорката (вальяжно теперь его называю), и уложил всё туда, где ему и должно быть. "Это невозможно сделать за один день" — скажете вы, и будете правы. Этому дню предшествовало множество других дней, в течении которых неслучайные знания откладывались на далёкой потаённой полочке мозга и до сегодняшнего дня не очень-то и использовались. Именно сегодня сработал триггер на хранимую процедуру, всё вылезло откуда должно было — и вычисление прошло удачно. Да, может быть результаты вычисления неверны — не может же один середнячковый [подставьте нужное оскорбление] постичь за один раз то, на что у других уходят годы, — но в глобально потеплевшем океане я нашёл вершину единственного выжившего айсберга, — благодаря знанию о его местонахождении, можно понять, где же именно находится его опасное, тяжёлое и неповоротливое дно. И я, конечно же, безусловно, неоспоримо, безропотно, не первый, — но может быть я именно тот, кто мог — и хотел бы — поделиться знаниями так, как умею делиться довольно хорошо — интересной статьёй. По крайней мере есть энная монадическая вероятность, что она интересна. Без картинок — вот это беда.

  

![](https://telegra.ph/file/db7364c591029ac5d48e4.png)

  

Люди, которые работают в IT, обычно любят изучать новое, если оно подано интересно. Если эти люди работали в IT ещё и много лет назад — или просто любознательны — они замечали, как часто в индустрию приходили новые, крайне интересные взгляды на всё что угодно в этой сфере, а чуть позже они поглощались более новыми, и даже более интересными взглядами. Могло даже показаться, что весь этот старый хайп не имел смысла перед величием нового хайпа, но как и указано во вступлении статьи — для меня нет ничего, что проходило бы бесследно — и действительно, если взглянуть обобщённым взглядом — предыдущие хайпы всегда играют роль в становлении новых — что-то переосмысляется, и если бы не было чего-то предыдущего — не было бы и нового. И новое — это лишь нечто, идущее параллельно с нами по времени.

  

Если вы не замечали такого — не страшно, я попозже поясню.

  

Даже хуже, может быть у меня своё кривое неправильное видение на всё, о чём я здесь пишу — настолько, что мне придётся его вам навязать — и это важно. Ещё важно, что я всё ещё _вообще_ не знаю теории категорий, так что буду нагло перевирать и передёргивать. Имею право, я же неизвестный автор. Выигрыш для вас в том, что единственное, что я знаю теперь — это как к теоркату подойти — так что ваши ложные знания потом легче, как по маслу, заменятся на настоящие и единственно верные. А если нужные знания с маслом у вас уже есть, то эта статья точно не для вас! Лонгрид, который обогатит вас на полтора лонгрида!

  

Отвлёкся.

  

### Обобщения

  

В мире программирования, как и в мире науки, да и вообще для человека, нужно выделять общие паттерны. Чтобы что-то изучить — мы находим общности, сортируем их, раскладываем по полкам, и стараемся меньше думать об исключениях (или приводить таковые к правилам, а на крайняк применяем этот противный метод запоминания — _заучивание_). Говорят, для нашего мозга такой процесс очень удобен и естественен, говорят — он так делает с начала времён. Не соврут, однако, упомянув, что такое некритичное поведение иногда приводит к ошибкам — _страшным_ ошибкам, но так как это случается очень редко, а страх обычно служит средством для сжигания неверной связи, — постараемся не сильно ковыряться в негативе. Хотя, если вдуматься, ошибки и отрицательные числа являются неотъемлемой частью жизни, обучения и вселенной вообще, ха-ха.

  

Аналогично, в IT неизбежно появлялись (и продолжают появляться) концепции, которые относительно легко ложатся на наши синапсы — в чём-то благодаря тому, что их придумывали люди, которые умели хорошо находить и категоризировать общности и сводить исключения к минимуму.

  

![](https://telegra.ph/file/143e1ca1249c3184ff5ab.png)

####   

#### Список

Только вспомните LISP — всё суть список. И функция — как это ни удивительно — тоже список. Имя функции (её идентификатор и тэг), в качестве головы списка, а затем в хвосте списка аргументы ползут за головой по одиночке — только такой список не просто сцепляет аргументы, а при обнаружении каждого нового элемента-аргумента выполняет некий код и в результате _поэтапно_ «сворачивает» исходный список к одному значению — возвращаемому. Если вы знали что такое _каррирование_ — то это оно, а если не знали — то теперь знаете. Не благодарите. Более привычный нам список, также в широких кругах известный как массив, тоже можно «свернуть» в одно значение — объединив его элементы: если это числа, то к примеру их можно просуммировать, а если строки — не мудрствуя лукаво, склеить в одну. Главное, чтобы все элементы такого списка имели одинаковый тип. И это отнюдь не значит, что запрещено смешивать числа и строки в одном списке: прямо так вот, в чистом виде, и число и строку положить в один список действительно нельзя, но есть трюк — числа и строки можно обобщить, если найти общее для них свойство — например, _складываемость_ — и тогда можно складывать (упс, тавтология... или нет?) в такой список _складываемые сущности_, а именно — _складываемые числа_ и _складываемые строки_ (и может что-нибудь ещё, что внезапно окажется _складываемым_). И это не отступление, это важно.

  

#### Файл

Если теперь взглянуть на Plan 9 (грубо говоря, из него появился UNIX) — то там мы тоже заметим общую концепцию — всё суть файл: даже принтер, пусть он и внешнее устройство — концепция абстрагирует его до понятия файла. И действительно, зачем же вводить лишнюю сущность «распечатать» — если можно направить поток данных в некий файл, который по случайному стечению обстоятельств (мы так сказали, это всё случайность!) оказывается принтером? Пользователю этот процесс прозрачен и понятен — ведь точно так же он ежедневно, рутинно, отправляет данные в "обычные" файлы. Как и в прошлом абзаце, это тоже результат поиска общего свойства и подбора для неё подходящего имени — отныне _файл_ это не только байты на жёстком диске, но и то, что течёт по проводам вовне (тогда не так много было "беспроводного", но чудесным образом и беспроводное хорошо ложится в концепцию) — пусть передача данных проходит не моментально и успешный результат не гарантирован — на том конце разберутся — файл из мяса, то есть байтов, ведь тоже не всегда успешно сохраняется.

####   

#### Функция

Ладно, а что же функциональное программирование? Функциональное программирование сводит всё к функции, где наоборот: и список — тоже «функция». То есть это как бы вывернутая наизнанку концепция LISP’а — но и она работает!

####   

#### Сигнал

Не утихла ещё популярность реактивного программирования, где всё есть поток, или сигнал — как бы список, но растянутый во времени, не доступный целиком за один момент, но каждое новое его значение становится в какой-то [непредсказуемый, с точки зрения программиста] момент известно. Такой сигнал может срабатывать на действия пользователя или любые внешние для программы воздействия — сайд-эффекты. Если простой список можно было представить в виде змеи, а функцию в виде змеи со способностями хамелеона, то сигнал — это змея, с непредсказуемой скоростью выползающая из-за угла. Или из коробки с котом. Мы не знаем её длины пока она вся целиком не вылезет, если вообще Зенон разрешит ей когда либо в обозримом временном промежутке целиком вылезти... А вы задумывались о том, что каждая змея может сворачиваться в клубок!?. Желательно (В JavaScript'е — желательно, в более чётких языках — требуется), чтобы события, проходящие через сигнал, были одного типа (обобщения допускаются, как и ранее), и приводились к сигналам другого типа только через трансформации.

  

#### Спред

V vизуальном языке программирования VVVV существует такое понятие, как _спред_ — последовательность неких элементов, собранная v результате операций над переплетением нод. Нода символизирует операцию над vходными данными, происходит операция — готовится суп — и vжух — мы получили vкусный результат из казалось бы банальных морковок и картофана. Отдельный элемент такой последовательности может быть не vсегда доступен из-за ошибок, произошедших где-то в начале сети, но это не страшно — vедь можно его пропустить и забыть. Сжечь мосты. Vажно, однако, знать, что ошибка возможна и нужно к ней подготовиться, её предусмотреть — изолировать от распространения дальше, устранить vирус — и ни v коем случае не делать так, как делают это в JS, где без зазрения совести позволяют этому vирусу заразить и предательски подкосить ноги vсей программе целиком. Vизуальное программирование могло бы быть отдельной vеткой развития нарратива нашей статьи, но я предпочёл бы оставить vам эту тему на сладкое, сядете vечером за чай с печеньем — и задумаетесь.

  

#### Компонент

Особенно свеж в нашей памяти React — всё есть компонент, а компонент — в идеале — _чистая_ функция. Тут даже добавить нечего после подробных описаний выше, конечно вы уже в курсе. Танграм компонентов, складывающийся в структуру DOM'а.

  

![](https://telegra.ph/file/740c8b50d4649965cb390.png)

###   

### Абстракции

  

Странно и глупо бы было предполагать, что занимаются такими играми в концепции только айтишники. Если взглянуть шире, окажется что это не только физики, главные концептологи науки, но и лингвисты, и даже искусствоведы. Не во всякой школе (или даже институте) упоминают, что математики давно подсели на крючок обобщений, ну просто потому что без азарта нахождения порядка не постичь мир. Только они называют это «общей алгеброй». Если уйти в начало времён, то вообще сложно сказать, кто начал первым составлять каталоги и словари — философы или практики.

  

То, что я перечислил в прошлой главе — абстракции — но вы можете и сейчас выделить в них что-то общее. Попробуйте — это полезный процесс, а я подожду. Время истекло. _Списки, цепи, сигналы, функции, потоки данных, спреды, пайпы в UNIX-шелле, музыкальные произведения, модулярные синтезаторы изнутри, может быть даже струны и суперструны, как их не назови — это последовательности сущностей (данных и операций над ними), которые могут либо быть пустыми_ (мы ожидали чего-то грядущего, а в результате ничего не было, ничего не произошло, зияющая чапаевская пустота — всё как в жизни)_, либо состоять из одного или нескольких элементов-сущностей до обозримой бесконечности._ Вернее — концом считается тот момент, когда нам в последний раз о них что-то было известно.

  

Так вот, если что-то может быть либо _пустым_, либо существовать в виде некой _последовательности_, пусть даже из одного элемента, пусть даже размазано по конечному или бесконечному _времени_ — это **Монада**. Вот так просто и неожиданно — я сам удивился нашей прыти — мы добрались до ключевого момента статьи.

  

Если сейчас вы пытаетесь привязать монаду к реальным предметам — трамваям или их отсутствию, прогнозам погоды или лжи метеорологов — да, продолжайте, но сильно не увлекайтесь. Важно не потерять чувство абстракции.  
Да, это именно абстракция — то есть она применяется на практике, конечно же, но обобщает такое невообразимое множество вещей, что становится легче сказать, что не является монадой.

  

Очень абстрактная абстракция, поэтому мы не очень часто употребляем в жизни этот термин, — а ведь на самом деле он есть и в философии, где монада — это _сущность_, _единица_. Не обязательно задумываться, что именно это может быть, — предмет или событие, — это может быть что угодно. Так что всё сказанное выше не значит, что в если в любой статье по теоркату заменить слово «монада» на «трамвай» или (бог упаси!) «буррито» — всё станет очевидно и ночь станет днём, а Иисус вернётся на землю. Если углубиться в структуры понятий теории, то монада, как класс, наследует свои свойства от четырёх других всадников апокалипсиса*, от каждого по кольцу^Wсвойству, — и это только в моей версии. Где-то их два, кто-то отделяет возможность быть _пустым вычислением_ от монады, кто-то нет — как и с фильмами по Звёздным Войнам, есть «канон» и «неканон», имеющий право на существование — как и с политикой, есть законы, но есть и расхождения в том, как их видят их отдельные группы людей, и как результат в каждой стране они немного различны. Может быть монада — это Бог?

  

> 1.Functor — объединяет массив и функцию в одно понятие, позволяет конвертировать элементы последовательностей из одного типа в другой;  
> 2. Applicative — тэгает значение, оборачивает его в нужный тип, обобщает до нужного типа;  
> 3. Bind — объединяет вычисления, об этом ниже;  
> 4. Apply — разворачивает функтор, конвертирует с его помощью значение, заворачивает обратно;

  

Рискнув, вы можете погрузиться в пучину кольц и полукольц (где же Фродо?), групп и полугрупп (что они играют?), монад и комонад (что мы есть?), и собственно категорий — это всё уже без меня. Если я смог передать ощущение открытия, воздержавшись от заумных терминов, детских рисунков и гиперформул — значит цель статьи достигнута, и мне осталось лишь закрепить зачатое.

  

И если, как только вы увидите слова «теория категорий», вы будете зажигать в мозгу световой короб со словом «абстракции» — думаю, будет значительно легче. То есть там, где они пишут «предмет» — это действительно вообще любой предмет, практически никакой конкретики. Там где они пишут «операция» — это действительно вообще любая операция, практически никакой конкретики. Практически — потому что теория старается найти общности в абстракциях, ведь нахождение общностей между абстракциями и приводит к конкретным понятиям. И отсюда вылезают все эти мерзкие (потому что непонятные на первый взгляд) формулы с множеством терминов, не употребляющихся почти нигде вне её. Вся эта напускная элитность сообщества просвещённых. В теории категорий есть даже определение для «категории» — вот уж воистину рекурсивный акроним.

  

![](https://telegra.ph/file/7b3e3ee1a34b1e3cd060c.png)

###   

### Закрепление материала

  

Ясное дело, вы хотели бы спросить, «почему все говорят про буррито или контейнеры, когда говорят о монадах?». И у меня есть ответ — монада это ещё и своеобразная метка, тэг, лейбл — описание того, что лежит (или могло бы лежать) внутри, то есть вы всегда можете с уверенностью сказать что сущности в этой вневременной последовательности однородны. Тем, что вы выделяете общее свойство её элементов — вы маркируете их этим свойством — как мы сделали выше с числами и строками, которые могут _складываться_ — мы пометили их как _складываемые**_.

  

> Если бы мы общались в терминах теории категорий — складываемое может называться полукольцом — за этими красивыми терминами действительно стоят очень простые понятия.

  

Как именно однородны элементы — вы решаете сами — ведь именно вам так будет удобнее каталогизировать мир. Например, это числа. Или события кликов мыши. Или аргументы функции, но только чистой. Или файл, который либо есть либо его нет. Или, побитово, данные в этом файле. Или это каталог, она же папка, может быть пустая. Или ноты в сочинении Ивана Дорна, когда их читают про себя, вслух, или когда они звучат во время исполнения. Или смысл в текстах песен мультфильма «Ну погоди!». Или состояния модели данных. Или одно такое состояние. Или подходящие данные и ошибочные. Или сущности различных алгебраических типов — когда вещь в монаде это либо одно, либо другое, либо третье, либо неизвестный вам вид, но количество этих «либо» конечно — то есть вы всегда знаете к какой группе (пусть даже и к группе неизвестных) принадлежит элемент последовательности. _Или это монада, в которой... лежат другие монады, да что же это такое!!!_

  

А вот здесь можно было бы и закончить, но есть ещё один интересный нам термин, который забывают упомянуть в разговорах о монадах, а ведь он бы мог помочь закрепить материал. Я же этого хочу — хочу убедиться, что уж теперь-то вам всё понятно!

  

![](https://telegra.ph/file/8b2b40e087ef380fca674.png)

  

Теоретик категорий может разделять понятия _данных_ и _операций_ над ними, мы уже пару раз сами так делали. Если уж мы всё обобщаем, давайте приглядимся — может быть и здесь мы сможем развернуться, или наоборот свернуться. Повторим определение монады, каким мы видим его на текущий момент — _последовательность помеченных однородных данных, над которыми можно проводить операции_. Это настолько прекрасное обобщение, что в его распростёртые от внутренней свободы сети попадает одна базовая сущность, о которой говорили, но к ней не присматривались — числа. Данные, которые можно складывать в последовательности, проводить между ними операции и в результате, к примеру — получать другие данные.

  

Если вы считаете на калькуляторе, то как только вы вводите одно из чисел при вычислении — калькулятор, будучи наделён недюжинным разумом, мысленно кладёт число в последовательность предыдущих. Как только вы нажимаете кнопку _операции_ — вы сворачиваете (к концу статьи можно уже не оборачивать это слово в кавычки) часть этой последовательности в новое число — из-за приоритетов у операций калькулятор не может забыть всё, — ему нужно хранить кэш вычисленного ранее. Если вдуматься, то и это сигнал из реактивного программирования, и конечно же монада. Его элементы размазаны по временной шкале (пока мы думаем, какое же число ещё ввести или какую операцию над ними провернуть), и пока мы, как внешний наблюдатель, не послали в этот сигнал элемент «=», призыв к свёртке — конец не наступает. Хотя он и так не наступает — мы же можем продолжить вычисления с полученным числом.

  

Главный вывод отсюда — натуральный ряд чисел — это тоже монада, где данные — целые числа, а операция над ними — прибавление единицы (но сворачивания не происходит). В случае факториала, например, имеет место и сворачивание — по мере накопления чисел в последовательности мы их перемножаем и в результате получаем значение. А парсинг текста — свёртка последовательностей токенов до удобной нам структуры. Если обобщить уже упомянутые и ещё не упомянутые операции между последовательно полученными данными, то может быть на язык попадёт слово **морфизм**, мы же преобразовываем данные — морфируем их в другие. А свёртка списков — это _катаморфизм_, _ката_ — по-гречески движение вниз, и здесь мы тоже не имеем в виду буквальный «низ» в смысле «дно», а скорее некоторую упрощённую, снизведённую, уплощённую структуру. Другие значения слова _ката_ тоже подходят — распределение действия вдоль чего-либо, завершённость. Мы же плаваем в море чётких и чистых абстракций, отдайтесь ему!

  

![](https://telegra.ph/file/cbd3b6f05fdec7793e5f7.png)

  

Отметим, что число может само по себе быть нулём (абстрактная аналогия пустоты для последовательности), либо любым другим числом. Эта способность быть нулём радикально, подрывнически, влияет на операции, которые можно с числами производить. Помните? — умножение на ноль даёт ноль, а делить на него вообще карается законом, прибавление нуля (ничего, пустоты, небытия) — не изменяет другого числа. Если вы посмотрите определение **моноида**, то обнаружите, что он, кроме прочего, описывает пустóты для _данных_. В то время, как монада, кроме прочего: определяет пустоту для _последовательностей_, _операций_, или _контейнеров_, или _контекстов_.

  

Разве не великолепно? А ещё число может быть единицей. Умножение на самого себя, на единицу — _эндоморфизм_. И опять же это не математическое умножение, не нужно представлять знакомые нам символы звёздочки или крестика — притормозите. Это некая абстрактная операция, которая обладает несколькими свойствами (они есть в википедии), мы возьмём одно из них — при проведении такой операции с единичным объектом (единицей, матрицей, конфетой, автомобилем Тесла...) получается равный исходному объект.... И обратно — если мы обнаруживаем, что какая-то операция над однородными объектами, путём глубоких научных исследований удовлетворяет этим свойствам-законам-условиям — мы можем назвать эту операцию умножением. Сейчас вообще бред скажу, но на то она и абстракция, а я — анонимный автор. Если бы секс человека с неким эталонным клоном, как операция над двумя людьми — однородными членами категории (общности) людей, в результате давал точно такого же человека, как и первый из исходных — мы могли бы назвать эту операцию умножением и она бы всё так же свободно легла в теоркат. Ну кто знает, может клонирование так и будет работать. Ведь клонирование — это всего лишь банальный изоморфный гомоморфизм... Если вы работате с матрицами, делаете трёхмерную графику или просто решаете судоку в метро по пути домой с работы, то встречали такое понятие, как _единичная_ матрица. Это единица в _категории_ матриц — она обладает всеми нужными для этого свойствами. И обратная матрица — её часто пишут как A в минус-_первой_ степени. А ещё есть мнимая _единица_ у комплексных чисел, квадрат которой — отрицательно заряженная _единица_. В общем, числа — это тоже последовательности, и им тоже свойственны внутренняя пустота и «единичность», и «всё что больше одного, много», и клонирование, и может быть даже душа...

  

![](https://telegra.ph/file/43ae99c066e113c5545dc.png)

###   

### Вывод

  

И здесь я хотел бы наконец сделать вывод: теория категорий — это наука, которая ищет общности в казалось бы поначалу никак не связанных математических (а значит и программистских тоже) понятиях и их каталогизирует. Помните, как в LISP'е — всё есть список, даже функция. Вот Теория Категорий — это абстракция на уровень выше. Типа, а что если программа на LISP'е — тоже список, состоящий из множества маленьких списков? Может быть такое, что жесткий диск с установленной на него системой UNIX — просто большой файл, распадающийся посредством морфизмов (операций) на более мелкие подфайлы? А вдруг программа с реактивными потоками — сама по себе большой поток, сложенный из множества маленьких потоков? Вот на этом высочайшем уровне всё и происходит, но исключительно там, где рассуждения не переходят в философию — иначе стыдно же, математики философов не очень любят, и в барах рядом не садятся.

  

И поэтому если бы не та педантичная математическая упоротость, с которой теория подаётся, — это возможно была бы самая интересная наука (после логики) для технаря (технарки), немного даже творческая. Впрочем, она похоже такая и есть, просто мы её слишком сильно боимся, а теоркраты не хотят принимать нас, непосвящённых и непросвящённых людей, в свой круг.

  

Q.E.D.

  

### Копилефты

  

Иллюстрации — из книги "More Elm Creek Quilts, 30+ Traditional Blocks" за авторством Jennifer Chiaverini.

  

Report content on this page