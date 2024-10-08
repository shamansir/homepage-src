---
layout: post.html
title: HTML5 — не язык разметки, а мессиво
datetime: Tue 16 Aug 2011 20:05
tags: [ html5 ]
---

Позволю себе, первую в блоге, теоретическую статью. Если вы легко возбудимы, не обращайте на неё внимания. И более того, эта статья — NSFW.

### Вступление

Когда черновик спецификации HTML5 только появился, многие были восхищены. Многие ворчали. Так часто бывает, когда приходит что-то новое. Появляются восхищённые и негативные статьи, практически в равном количестве. Лично я почти никак к этому не относился и скорее заинтересованно ждал, что будет потом, поскольку с чем-то новым и непростым так происходит всегда — всегда есть почти равнозначные плюсы и минусы. Но потом, со временем, что-то превалирует. Плюсы и минусы были в спецификации HTML4. И в спецификации XHTML. Но со временем превалировали плюсы, вернее пользователи их просто душевно приняли (за безысходностью?).

Canvas/WebGL, LocalStorage, встроенная поддержка видео, избавление от устаревших тэгов — очевидные плюсы, с этим глупо спорить. Но только сейчас, совершенно неожиданно для себя, я осознал, что эти *нововведения* сомнительны просто потому, что действительно **введены куда-то не туда**.

![Inserted not there](../assets/ru/html5-not-a-markup-language-but-a-mess/inserted-not-there.png)

(Обращу ваше внимание: я считаю, что по отдельности эти возможности просто прекрасны)

Факт этой хм... *диспозиции* замечают давно, в конце статьи я приведу ссылки на самые популярные статьи по этой теме (тысячи их). Вот [эта][curlybrace-article], например, и вдохновила меня на написание данной. Ну, приведу те, которые найду — это будет не полный список: ведь хуже всего прочего, этот факт имел место и раньше и замечали его раньше тоже.

Вообще, все наблюдения по этому поводу довольно банальны и скорее относятся к категории троллинга, но я вдруг подумал — да, проблема есть ­— *а есть ли решение*? Пусть просто пофантазировать, ведь можно пофантазировать иногда. Революции действительно [не будет][muromec-comment], но ведь мечты никто не отменял.

### Всё же, почему «не туда»?

Не буду разбирать по косточкам историю HTML: старожилы сети помнят как всё было, а молодые не раз про это читали.

Самое главное — *вначале была веб-страница*. Думаю, она задумывалась как *документ + немного интерактива*. Для навигации придумали понятие *ссылки*. Но при этом веб-страницей довольно часто был просто *документ*: сплошным текстом с минимальным оформлением, шрифт Times New Roman. Резюме, статья, обзор фильма, фотография с гик-вечеринки.

В результате (D)HTML и отразил эти требования:

* разметка текста документа: жирный, курсив, шрифт, цвет, таблицы;
* ссылки и якоря (ещё был image map, помните такое?);
* возможность прикрутить динамику;
* базовые стили?;

Может быть уже тогда всё пошло не так? Зачем *внутри* текстового документа динамика? Почему вдруг в документе определяется шрифт и цвет? Последний вопрос решили, когда придумали CSS — и это был правильный ход. Но вопрос с динамикой открыт и сейчас. То есть да, *HyperText* — это и есть, буквально, «текст, но круче чем текст», «супер-текст», «текст-супермэн» — да, **но зачем**, дорогой бобёр?

![Beaver](../assets/ru/html5-not-a-markup-language-but-a-mess/beaver-error.jpg)

Тогда это не было остро заметно, но именно сейчас мы пожинаем плоды. Мы вставляем в документы интерактивные игры, мы меняем части документа на другие части, мы вообще, можно сказать, издеваемся над документами. Пусть так, в этом вроде ничего плохого, но мы продолжаем делать это *внутри них самих*, *внутри их разметки*.

Мы берём то, что называется **язык разметки** и с его помощью делаем то, что совершенно с этим определением не вяжется:

* Интерактивные магазины
* Приложения для прочтения почты и сохранения заметок
* Редакторы кода
* Редакторы графики
* Игры
* Группы обсуждения
* Порно-хабы
* Операционные системы, блять!
* *Впишите ещё 200 вариантов*

![Markup vs Stuff](../assets/ru/html5-not-a-markup-language-but-a-mess/markup-vs-stuff.png)

Теперь в одной спецификации разметки у нас *перемешаны* (сравните с вариантом из прошлого):

* разметка документа (кстати, таблицы всё ещё чрезвычайно сложны и имеют много древних артефактов);
* поддержка Unicode;
* ссылки и якоря;
* возможность прикрутить динамику (стало хорошей традицией выносить вовне);
* CSS-стили (стало хорошей традицией выносить вовне);
* непонятно вообще куда записать: `<head>`, `<nav>`, `<aside>`, ... (насколько я знаю, у этих тэгов до сих пор нет однозначного и короткого определения; при этом ещё открыт вопрос: кто их реально использует?);
* видео/аудио (ну ок, видео и аудио относятся к понятию документа. Но почему тогда нет встроенной поддержки слайдов презентаций?);
* векторная графика;
* улучшенные формы; (форма — это документ?)
* `iframe`; (документ в документе, по сути)
* работа с историей; (что-то для браузера)
* работа с USB и RS232; (*ээээ...*)
* поддержка видеокарт; (**стоп, ЧТО!?**)

> Возьмём термин «Игра на HTML5» и посмотрим цепочку, откуда она такая берётся:

> Игра на HTML5 ← Canvas ← WebGL ← видеокарта ← ничего общего с разметкой

> ![HTML5 ← Canvas](../assets/ru/html5-not-a-markup-language-but-a-mess/html5-canvas-videocard.png)

> Явно видно, что логическая цепочка рвётся уже между понятиями «HTML» и «Canvas»

И это — одна спецификация, один *МНОГОФУНКЦИОНАЛЬНЫЙ-СУКА-ГИПЕРДОКУМЕНТ*!

![Multi-dammit-hyper-document](../assets/ru/html5-not-a-markup-language-but-a-mess/multi-dammit-hyperdocument.png)

Ведь это правда **МЕССИВО**!!

![mess](../assets/ru/html5-not-a-markup-language-but-a-mess/mess.png)

И при этом у нас до сих пор нет унифицированного, легко читаемого формата для книги (`fb2` хорош, но не подходит для книг издательства [O`Reilly][oreilly]!). (Зато есть интерактивные книги: это, кстати, хорошо). Нет поддержки математических формул, до сих пор нет редакторов, которые бы производили *стандартный* результат, одинаковый между ними самими.

Ошибки двигают прогресс, это давно известно. И благодаря HTML у нас появилось куча полезных вещей, кстати как раз *вопреки* — как, например, [Wiki][wikipedia], [Markdown][markdown], [Node.JS][nodejs]. Но источник революционного вдохновения от ошибок когда-то кончается, и тогда настаёт пора эти ошибки *исправлять*.

### Как решить. Метатипы

Я считаю, что основная цель — добиться типизации: отделить мух (разметку документа) от тараканов (блоков аудио/видео/канвас), тараканов от котлет (блочной разметки aside/nav/header). Поэтому требуется *классифицировать* все те варианты, которые сейчас оказались перемешаны в кучу. Выделим пяток основных пунктов:

![Fly-Cockroach-Cutlet](../assets/ru/html5-not-a-markup-language-but-a-mess/fly-cockroach-cutlet.png)

* Простой Текстовый Документ (статья, резюме, обзор, докторская)
* Блог, Вики-портал (набор статей) ([tumblr](http://tumblr.com), [blogspot](http://blogspot.com), ...)
* Презентация (слайды) ([slideshare](http://slideshare.net), [scribd](http://scribd.com), ...)
* Веб-приложение (структура виджетов + локальный storage) ([gmail](http://gmail.com), [evernote](http://evernote.com), ...)
* Игра (интерактивная растровая и векторная графика, работа с видеокартой) ([chain reaction](http://www.yvoschaap.com/chainrxn/), [biolab disaster](http://playbiolab.com/), [torus](http://www.benjoffe.com/code/games/torus/), [angry birds](http://chrome.angrybirds.com/)...)
* Видео, Аудио, Изображение
* и т.п.

Как плавно ввести эти метатипы в современный веб? Например, у нас есть в вооружении такая превосходная вещь как [MIME-типы][mime]. Уже сейчас браузеры умеют сами (через плагины) отображать файлы PDF, видео, XML, RSS, так что путь начат.

Например:

* Вы запрашиваете в браузере адрес `http://steve.jobs/resume`, браузер обнаруживает в заголовке ответа MIME-тип `text/markdown` или `text/extended-markdown`, собственноручно рендерит полученный markdown-текст в нынешний HTML — и всё ок; (в markdown-документе можно использовать параметры в заголовке, например пути к теме-стилю (но ни в коем случае не к скриптам!), как в [jekyll][]). Или, например, он может получить MIME-тип `text/latex` и отрендерить это дело в PDF или HTML. `text/wiki-like-in-wikipedia` тоже подойдёт.
* Вы запрашиваете в браузере адрес `http://idsoftware.org/quake7.game`, браузер обнаруживает в заголовке ответа MIME-тип `game/webgl`, отображает один только `canvas` и отдаёт управление пришедшему WebGL-скрипту. Понятное дело, `game/flash` нужно запретить сразу же.
* Вы запрашиваете в браузере адрес `http://mikashkin/blog`, браузер прищуривается, распознаёт MIME-тип `text/blog`, а внутри (например) YAML-структуру типа

    ``` yaml

    blog:
        author: mikashkin
        sort-by: date
        paging: 20
        style: blog.css
        entries:
            - buildout-lecture.markdown
            - python-is-great.markdown
            - why-gae-is-cool.markdown
            . . .

    ```

   Ну, вы представляете что получится в результате.

* Вы запрашиваете в браузере адрес `http://evernote.app`, браузер получает в ответ структуру виджетов на неком UI-языке, MIME-тип, например: `application/ui-declarative`:

     ``` yaml

    DockLayout:
        north:
            evn-Toolbar
            evn-LoginBlock loggedin=true
        west:
            evn-NotesTree
        center:
            evn-NotepadWidget
        south height=0.1:
            text "copyright © %year"
            link "http://evernote.app"
            input "Feedback" active=true
            button "send"

    ```

   В результате, браузер *сам* парсит этот язык и отображает его как надо. Кстати, такой UI хорошо смасштабруется и на мобильный браузер.

* Вы запрашиваете в браузере адрес `http://chromium.os`, браузер видит MIME-тип `application/os` и редерит полученный ассемблерный код на клиенте

А потом, постепенно, можно заменить в этих сценариях HTML на что-то более вразумительное и строгое: но это будет внутренний формат браузера, обычному веб-разработчику до него не должно будет быть дела: блоггеру нужно будет знать только markdown/latex/wiki, веб-UI-разработчику — декларативный язык виджетов, разработчику игр — только WebGL. Им не нужно будет знать HTML.

![Inserted there: happy](../assets/ru/html5-not-a-markup-language-but-a-mess/inserted-there-happy.png)

Я думаю, вы поняли принцип. По-моему этот подход вполне логичен и оправдан, типы контента *строго разделены* и разработчики и пользователи счастливы, им не нужно знать кучу веб-стандартов.

Правда, после этих манипуляций браузер станет чем-то вроде напичканного плагинами *просмотрщика файлов*, только исключительно по сети. Ну, а к чему мы шли? Разве это не лучше, чем спецификация, у которой внутри одно **мессиво**?

### Ссылки

(Несмотря на скудное разнообразие названий — ручаюсь, это разные статьи)

* [HTML5 — The Goog, The Bad, The Ugly](http://marvinserrano.wordpress.com/2011/05/26/html5-the-good-the-bad-and-the-ugly/)
* [HTML5 — The Good, The Bad, The Ugly](http://channel9.msdn.com/Series/HTML5-Day/HTML5-The-Bad-The-Good-and-the-Ugly) (видео, польский)
* [HTML5 — The Good, The Bad, The Ugly](http://www.slideshare.net/x00mario/html5-preso-rub2010) (слайды)
* [HTML5 Buzz](http://www.whitewallweb.com/blog/2010/05/20/the-html5-buzz/)
* [The Good, The Bad And The Ugly of HTML5](http://www.slideshare.net/CannedTuna/the-good-the-bad-and-the-ugly-of-html-5-presentation) (слайды)
* [Preparing for the Goog and Bad with HTML5](http://www.itworld.com/open-source/113469/preparing-good-and-bad-html5)
* [HTML5 — Bad Idea](http://www.eccnet.com/xmlug/html5)

[muromec-comment]: http://habrahabr.ru/blogs/webdev/125990/#comment_4153164
[curlybrace-article]: http://habrahabr.ru/blogs/webdev/125990/
[oreilly]: http://oreilly.com/
[markdown]: http://daringfireball.net/projects/markdown/
[nodejs]: http://nodejs.org/
[wikipedia]: http://www.wikipedia.org/
[mime]: http://ru.wikipedia.org/wiki/Internet_media_type
[jekyll]: http://jekyllrb.com/
