## Про язык Forth

// текст 2018.05

### I. Язык Forth

Лет двадцать пять назад копался в давно ископанной стопке книг на полке информатики в библиотеке и некоторое время крутил в руках [С.Н. Баранов, Н.Р. Ноздрунов. *Язык Форт и его реализации*. Л.: Машиностроение, 1988]. Покрутил, да и вернул обратно. Школота, интереснее казались другие языки, искал крупицы по Паскалю. Запомнил проходной момент потому, что запала в голову схожесть названия с Фортраном. Фигня же, а зацепилась, да.

Года два назад стояли с тестем в дворике на Плющихе, меланхолично курили в небо и долго обсуждали атипичные языки, на которые соскочили после обсуждения того, как на современных студентов влияют сладенькие песочницы Java и Python. Как-то докурили до ассемблеров, потом до стеков и регистров, ну и дальше по цепочке. И второй раз в жизни цепляющим за извилину эпизодом оказался Forth. Тесть как-то бодро рукой махнул, мол, на Форте можно планету покорить, а по пути ещё и Марс с Венерой на сдачу подмять. Я плечами пожал (толку обсуждать, если ничего не знаешь), но запомнил.

На днях ползаю по статьям о разработке. Бац, Forth. В статье 2016 года. И написано вовсе не про каки мамонтов. Тут уже зацепило за живое. Начал раскручивать, шо то воно такое. И докрутился до трёхчасового чтения перед сном.

Лирическое вступление для того, чтобы сразу стало ясно следующее: я не двигаю Forth в качестве рабочего языка, он применим очень узко. Если не используете, вам и не надо. Даже не топлю за него в теме *"это знать каждому разработчику, желающему стать программистом"*. Причины интереса к нему... да вон выше описаны. А всё-таки интуитивно кажется, что с этим языком и его культурой стоит ознакомиться, если хочется почувствовать атмосферу 70..80-х гг. Да, вы не будете писать на Lisp, на Forth, на Ada и Algol. Зато до сих пор используете решения тех лет, потому полезно узнать, для борьбы с какими проблемами придумалось то или иное. Наконец, тексты программистов 30..40-летней давности — тексты людей, которые учат не использовать фреймворк X или быстрее выходить на рынок с прототипом, но учат быть программистом, который создаст язык, на котором создаст фреймворк, который сам по себе создаст рынок. Милый сердцу олдскул.

Так вот, [Forth](https://en.wikipedia.org/wiki/Forth_(programming_language)) создан [Чарльзом Муром](https://en.wikipedia.org/wiki/Charles_H._Moore) в 1968..1970 годах. Если считать выходом языка выход stable production, получим 1971 год — полноценный Forth был доделан и прикручен к телескопу в National Radio Astronomy Observatory, в которой работал Мур. Ну и понеслось.

В первые минут 10..15 знакомства с синтаксисом умиляешься. Оно такое муси-пуси. Синтаксиса почти нет. Вот всё, что в голову приходит, всё отсутствует. В чистом виде Forth представляет собою метаязык, на котором вы сваяете что-то, что решит ваши проблемы. Описывать не буду, ссылок хватает. Задумываешься, ладно, мол, а куда вот это применять-то? Игры типа крестиков-ноликов клепать? Вы всё-таки походите по ссылкам, посмотрите, как язык выглядит. Тем занятнее будут примеры использования в нашем столетии. Приводить примеры из прошлого не вижу смысла, т.к. в период 1970..90 гг Forth был везде. Думаю, если накатить и начинать собирать яркие примеры из периодики (*"Forth Dimensions"*, *"Journal of Forth Application and Research"*) и литературы (учебники, статьи в научных журналах, каталоги производителей и т.д.), блога не хватит. Ограничусь цитированием Баранова:
> К середине 1980-х гг. Форт выдвинулся на третье место после языков Бейсик и Паскаль в качестве средства программирования для персональных ЭВМ, и рост его применения продолжается. Широкое распространение получили коммерческие программные продукты, написанные на Форте: системы обработки текстов, пакеты машинной графики, трансляторы, видеоигры. Стихийно быстрое распространение Форта и его практический успех обусловили необходимость стандартизации языка. В 1983 г. был опубликован стандарт "Форт-83", в соответствии с которым ведется изложение материала в этой книге.

Вот как-то так это тогда и выглядело, да.

Итак, где нынче живёт Forth.

**Космонавтика**. Главное в этом разделе — микроконтроллер [RTX20x0](https://en.wikipedia.org/wiki/RTX2010), выполняющий код на Forth. Этот микроконтроллер впаивали во [всё](http://web.archive.org/web/20110204160744/http://forth.gsfc.nasa.gov:80/) (список собирался до 2003 года, потому полным не является): миссии IMAGE, ROSETTA, Deep Impact, Shuttle, CASSINI и т.д. Да чего далеко ходить. Помните миссию [Philae](https://en.wikipedia.org/wiki/Philae_(spacecraft)), которая про комету? Так вот там два RTX2010 [зарулили](http://www.cpushack.com/2014/11/12/here-comes-philae-powered-by-an-rtx2010/).

**Embedded**. До сих пор используется во всякой цифровой мелочи. Много точечных ссылок и упоминаний, включу лишь одно интересное. Вот на [этой](http://www.mpeforth.com/sample-page/46-2/) странице отмотать вниз до Partial customer list. Partial потому, что NDA. Интересно тем, что это "покупатели" VFX Forth — от BAE и NASA до Rolls Royce и Saab. Sapienti sat. Сюда же можно добавить и этот [список](https://www.forth.com/resources/forth-apps/). Пролистал также 40+ страниц современных форумов и переписок, выяснил, что (как минимум) в США язык жив не только в заводских условиях. Инженеры его используют для своих поделок и для прототипирования (в чём он знатно силён, как начинаю всё больше понимать).

**Наука**. Научные статьи выходят до сих пор, т.к. стековые машины всё в той же зоне внимания, а Forth прекрасен в своей чистоте реализации идеи. Правда, это ничему не показатель, учёное сообщество по любой давной забытой штуковине статьи сотнями выпускать будет, но всё же.

А и всё, пожалуй. Космос, промышленность, наука — три современных ниши языка. Более ничего не нашёл, хоть искал старательно, уверяю.

С литературой швах. Есть стандарты, есть ворох всего по начало 2000-х, дальше тишина. Варианты Форт-систем спокойно разрабатываются внутри контор, нужды им информацию наружу выплёскивать особой и нет, потребителя, нуждающегося в свежих учебниках / руководствах, тоже нет. Потому голову питаем прошлым.

На данный момент самыми интересными источниками знания про Forth оказались вот эти (либо прочёл, либо читаю, но уже оценил):
* Статьище ["The Evolution of Forth"](https://www.forth.com/resources/forth-programming-language/) — информация из первых рук.
* Журнал ["BYTE, Vol.5, No 8, August, 1980"](https://ia802600.us.archive.org/35/items/byte-magazine-1980-08/1980_08_BYTE_05-08_The_Forth_Language.pdf) (200MB PDF). 2/3 номера в 300+ страниц посвящены языку. А ещё там реклама 26-мегабайтного винта за $5К. Были же времена, а. Даже если не читать, важно отметить то, как массовый журнал для народа выделяет целый номер под одну тему. Этого не бывает с маргинальными разработками, ну и 80-е — начало пика популярности Форт-систем, что BYTE не мог пропустить.
* Книга ["Thinking Forth"](http://thinking-forth.sourceforge.net/). Выпустили в 1984 году, стала бестселлером. Перевыпустили в 1994. Потом в 2004, уже под CC-лицензией. Исправили опечатки, улучшили типографику и т.д. Книга одна из культовых в мире Forth и правильно — читается запойнее художественного романа.
* Статья ["Язык Форт в СССР и России"](http://www.computer-museum.ru/histsoft/fortran_sorucom_2011.htm) — любопытная статья с деталями, из неё же и цитата post scriptum'а.
* Книга ["Язык Форт и его реализации"](https://archive.org/details/Baranov.Forth.language.and.its.implementation) — первая глубокая отечественная книга по Forth. Интересна ещё и тем, что в "Приложении 2" приведён список распространённых в 80-е Форт-систем, но по понятным причинам почти сплошь советские.

Не проработал (даже не полистал, но собираюсь) следующее потенциально интересное:
* [Кладовка](http://pages.cs.wisc.edu/~bolo/forth/) древних ссылок на Forth-ресурсы, половина уже не с нами. Достаточно сказать, что там используется слово webring. ^_^
* Книга [Starting Forth](https://www.forth.com/starting-forth/) того же Броуди. Примечательна и тем, что в СССР вышел её перевод [Лео Броуди. *Начальный курс программирования на языке Форт*. Финансы и статистика, 1990]. Милота: *"Starting"* vs *"Начальный курс программирования"*.
* Стандарт [ANS Forth-1994](http://dl.forth.com/sitedocs/dpans94.pdf) для хардкора.
* [Логово](http://www.forth.org/) фортолюбов. Тоже кладовка ссылок.
* Наконец, [компания](https://www.forth.com/) тех, кто Forth придумал, использовал и продолжает его двигать.

В сумме ссылок хватит, чтобы обеспечить извилины гимнастикой надолго. Ну и вообще есть смысл поискать издания по Forth 80-х, в США их много вышло, хоть коллекцию собирай.

PS. Хотел бы обратить внимание на слова про упомянутую в первом абзаце монографию: *"Первый тираж составил 50 тыс. экземпляров, но затем издательство получило столько запросов с мест, что пришлось допечатать еще 50 тысяч – редкий случай в практике!"*. Современные тиражи IT/CS-книг для профессионалов — 200..3000 экземпляров за редким исключением. Для объективной оценки тиража и допечатки советую прикинуть, сколько в 1988 году в СССР было компьютеров, программистов и людей, которые могли освоить / использовать Forth.

### II. Судьба Forth

Таки *"Как плюсы и джава убили такой чудесный язык?"* ((c) какой-то твиттерский) Что пошло не так?

**Начнём** с начала. Чтобы язык стал массовым, он должен быть понятен массам (целевой аудитории). Чем больше масса (с максимумом в количество людей на планете), тем более массовый и "победивший" язык. Практика показывает, что на вершине этой метрики оказываются языки, в текущий момент наиболее близкие бытовому представлению о программировании. Эти же языки применяются в учёбе, что наращивает инерцию дальнейшего использования людьми.

BASIC разработан Курцем и Кемени в 1964 году как язык для студентов-непрограммистов. Pascal разрабатывался как упрощение Алгола с потенциалом обучения студентов структурному программированию (Вирт [отмечал](http://pascal.hansotten.com/niklaus-wirth/recollections-about-the-development-of-pascal/) успех в этом 30 лет спустя, отметив также отсутствие поддержки индустрией) — да до сих в ряде вузов на Паскале кодят. Python используется сейчас первым языком для начинающих, как и JavaScript (книги *"(Python\|JavaScript) for kids"* популярны). Это четыре сверхпопулярных массовых языка. И это четыре языка, которые могла освоить условная тётя Глаша из отдела инвентаризации столов и стульев. Вот вам и массовость.

У Forth уже его постфиксная нотация превратила массовость в недостижимую Фудзияму. И нужда в понимании стековой машины. Все действительно массовые языки исключают понимание работы памяти, стеков, регистров и т.п. Это слишком круто для тёти Глаши. А упрощать никто и не собирался. Соответственно, пока на всю планету было 17 программистов с тремя физмат высшими образованиями на каждого, Форт чувствовал себя прекрасно. Когда за клавиатуру сели Глаши, мир начал меняться.

**Второе** начало в компенсации человеческого фактора. Иначе говоря, даже лучший в мире программист будет безбожно косячить. От этого устали как сами программисты (ну кому нравится час скармливать стопку перфокарт, чтобы обнаружить непробитую дырочку), так и корпорации (вот весело в масштабах IBM размышлять о том, как твои 10000 программистов половину времени не продукт делают, но баги правят). Потому языки развиваются в стороны *"наиболее раннее обнаружение ошибки на стадии разработки"* (анализаторы, IDE), *"средства языка для обработки ошибок"* (исключения), *"изгнание провоцирующих конструкций"* (война с =/==, например), *"приближение к бытовому мышлению"* (скажем, та же инфиксная нотация, удобная людям, но неудобная парсерам).

Интересным следствием является поддержка кровавым энтерпрайзом расчудесного (шучу, на самом деле скукота) языка Java. Энтерпрайз требует валового производства ремесленного продукта. Если в мире 1M складов, должны быть 100K разработчиков, которые напишут 10K складских программ. Бизнес такой, особенно бизнес взаимоинтеграции этой свалки на уровне государственных тендеров. Так вот Java оказалась идеальна. Язык простой и безопасный, можно нанимать пушечное мясо. Язык достаточно строгий, потому адовая формализация процессов вместе с автоматикой тестирования и прочим компенсирует адочек в финале. Да, внутри кака, но работает. Язык достаточно развит (включая библиотеки), чтобы покрывать нужды энтерпрайза. Ура-ура. Недавно попадалась статья бойца из IBM, разбирались причины факапов. Так вот современный разработческий IBM — это интерфейс к Бангалору. Зато дёшево. Зато работает, если нанять не 10K, но 20K чуваков. Писать будут долго и мучительно, но ЗАТО ДЁШЕВО.

И снова это не про Forth. Язык, в котором вас никто не защищает ни от чего. Что написал, то в лоб и прилетит. Учитывая забавный синтаксис и стековые особенности... Скажем так, пока я осваивал первые 10 страниц учебника, завесил намертво [gforth](https://www.gnu.org/software/gforth/) на Андроиде тоже 10+ раз.

**Третье** начало в универсальности. Универсальность — свойство языка, позволяющее X лет на Y архитектурах решать Z задач. Сюда стреляет всё. И поддержка массами, пишущими сотую библиотеку разбора командной строки. И поддержка корпорациями, решающими языками свои задачи (привет, Go, привет, Swift). И возможность создавать проекты любого масштаба (с каждым годом всё толще и толще). И включение народом или корпорациями поддержки новых явлений вроде цветных дисплеев и виртуальной реальности. Обилие учебной литературы. Включение в программу вузов (SICP на Python, эх). Выявить один решающий фактор невозможно, особенно во времена интернета. Не будь [Райана Даля](https://en.wikipedia.org/wiki/Ryan_Dahl), были бы сейчас Node.js-программисты вместо jQuery-верстальщиков?

C, C++, Java, Python, Fortran — их объединяет также и расположенность к созданию библиотек, фреймворков, модулей, пакетов. Нафигачил, нафигачил, выложил, оно десятки лет живёт и всё ещё тёплое. Культура накопления и распространения. За эти же десятки лет набирается такая огромная гора решений задач на множестве платформ, что чуть ли не любая ваша обычная задача уже решена. Ну или вы можете её решить, подмазав кирпичик маслом, а шурупчик напильником.

Forth в этом контексте чистый лист. Y архитектур — да, хоть в настенной кукушке. X лет — да, он настолько прост, что его левой пяткой портируют из года в год на новое железо и в новые OS. Z задач — нет. Нечем. Forth не для прямого решения задач. Он для создания инструментов, которыми вы будете решать свои задачи. Нюанс, как мне кажется, в том, что отлично решена будет именно ваша задача, а вот сделать из решения "фреймворк"... не на Forth. Утомитесь любой привычный в других языках код писать с нуля. Утомитесь от нужды писать тысячи строк на языке, на котором эти тысячи строк неудобно читать. Forth позволяет за год сделать катану именно под вашу руку и под ваш стиль. C++ позволяет за месяц (допустим) написать завод по производству стандартных офицерских парадных шашек по сто штук в день, а на сдачу киоск Союзпечати. Разница универсальности в этом.

Вообще же у меня возникло впечатление, что авторам Forth и Forth-сообществу это и не требовалось. Массовость? Ну, побыли массовыми, когда программирование компьютеров было программированием микропроцессоров и микроконтроллеров, которым занимались специалисты. Компенсация человечности? А зачем, если фортофил готов каждый символ няшить и тешить до победы? Универсальность? Изначально не закладывалась, к ней не стремились и дальше. Удовольствие и ниша Forth — создание небольших чрезвычайно "ёмких" и "плотных" решений для крохотных (по нынешним меркам, конечно, а так-то IBM System/360 могли и комнату занять целиком) железок. Доить из Forth коммерцию? Как понимаю, и без того во взятых рамках плохо не было, контракты с NASA не копеечные, надеюсь.

Потому я не могу согласиться с тем, что язык убили. Он без борьбы отдал поле, за которое грызлись поколения BASIC (венцом Visual Basic) и Pascal (венцом Delphi), уехал в провинцию и там возделывает грядку.