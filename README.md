<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Достопримечательности Саратовской области</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.css">
<style>
    :root {
        --primary-color: #004d9e;
        --secondary-color: #1a75cc;
        --text-color: #333;
        --bg-light: #f5f7fa;
    }

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: 'Arial', sans-serif;
    }

    body {
        line-height: 1.6;
        color: var(--text-color);
        background-color: #dbeaf7;
        background-image:
            url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='120' height='24' viewBox='0 0 120 24'%3E%3Cpath d='M0 12 Q15 0 30 12 T60 12 T90 12 T120 12' fill='none' stroke='%23004080' stroke-opacity='0.07' stroke-width='2'/%3E%3C/svg%3E"),
            linear-gradient(180deg, #cfe6f7 0%, #eaf3fa 45%, #f7f1e3 100%);
        background-attachment: fixed;
    }

    header {
        background: linear-gradient(135deg, var(--primary-color), #003366);
        color: white;
        padding: 2rem 1rem;
        text-align: center;
    }

    header h1 {
        font-size: 2.5rem;
        margin-bottom: 0.5rem;
        text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
    }

    header p {
        font-size: 1.2rem;
        opacity: 0.9;
    }

    nav {
        background: rgba(245,247,250,0.95);
        padding: 1rem 0;
        position: sticky;
        top: 0;
        z-index: 1000;
        border-bottom: 1px solid #ddd;
    }

    .nav-container {
        display: flex;
        justify-content: center;
        gap: 2rem;
        flex-wrap: wrap;
    }

    .nav-container a {
        text-decoration: none;
        color: var(--text-color);
        font-weight: bold;
        transition: color 0.3s;
    }

    .nav-container a:hover {
        color: var(--primary-color);
    }

    main {
        max-width: 1200px;
        margin: 0 auto;
        padding: 2rem;
    }

    .intro {
        text-align: center;
        margin: 0 auto 3rem;
        font-size: 1.1rem;
        line-height: 1.8;
        max-width: 800px;
        background: rgba(255,255,255,0.85);
        padding: 1.5rem 2rem;
        border-radius: 12px;
        box-shadow: 0 4px 15px rgba(0,0,0,0.08);
    }

    .attractions-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 2rem;
    }

    .card {
        background: white;
        border-radius: 10px;
        overflow: hidden;
        box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        transition: transform 0.3s, box-shadow 0.3s;
        display: flex;
        flex-direction: column;
        height: 100%;
    }

    .card:hover {
        transform: translateY(-5px);
        box-shadow: 0 8px 25px rgba(0,0,0,0.15);
    }

    .card img {
        width: 100%;
        height: 200px;
        object-fit: cover;
        background: #e9edf2;
    }

    .card-content {
        padding: 1.5rem;
        flex-grow: 1;
        display: flex;
        flex-direction: column;
    }

    .tag {
        display: inline-block;
        align-self: flex-start;
        font-size: 0.75rem;
        font-weight: bold;
        text-transform: uppercase;
        letter-spacing: 0.04em;
        color: var(--secondary-color);
        background: #e6f0fa;
        padding: 0.15rem 0.6rem;
        border-radius: 20px;
        margin-bottom: 0.6rem;
    }

    .card h3 {
        color: var(--primary-color);
        margin-bottom: 0.5rem;
        font-size: 1.3rem;
    }

    .card p {
        flex-grow: 1;
        font-size: 0.95rem;
        color: #555;
    }

    .card-buttons {
        display: flex;
        gap: 0.6rem;
        margin-top: 1rem;
        flex-wrap: wrap;
    }

    .btn {
        display: inline-block;
        padding: 0.5rem 1rem;
        background: var(--primary-color);
        color: white;
        text-decoration: none;
        border: 2px solid var(--primary-color);
        border-radius: 5px;
        text-align: center;
        font-weight: bold;
        font-size: 0.9rem;
        cursor: pointer;
    }

    .btn:hover {
        background: var(--secondary-color);
        border-color: var(--secondary-color);
    }

    .btn.outline {
        background: transparent;
        color: var(--primary-color);
    }

    .btn.outline:hover {
        background: var(--primary-color);
        color: white;
    }

    /* Окно с подробной информацией */
    dialog {
        border: none;
        border-radius: 12px;
        width: min(760px, 94vw);
        max-height: 90vh;
        padding: 0;
        margin: auto;
        overflow: hidden;
        box-shadow: 0 10px 40px rgba(0,0,0,0.35);
    }

    dialog::backdrop {
        background: rgba(0,0,0,0.55);
    }

    .dlg-scroll {
        max-height: 90vh;
        overflow-y: auto;
    }

    .dlg-img {
        width: 100%;
        height: 260px;
        object-fit: cover;
        background: #e9edf2;
        display: block;
    }

    .dlg-body {
        padding: 1.5rem 2rem 2rem;
    }

    .dlg-body h2 {
        color: var(--primary-color);
        font-size: 1.7rem;
        margin: 0.3rem 0 1rem;
    }

    .dlg-body h4 {
        color: var(--primary-color);
        margin: 1.4rem 0 0.5rem;
        font-size: 1.1rem;
    }

    .dlg-body p {
        margin-bottom: 0.8rem;
        color: #444;
    }

    .dlg-body ul {
        margin-left: 1.3rem;
        color: #444;
    }

    .dlg-body li {
        margin-bottom: 0.3rem;
    }

    .info-table {
        width: 100%;
        border-collapse: collapse;
        font-size: 0.95rem;
    }

    .info-table th,
    .info-table td {
        text-align: left;
        vertical-align: top;
        padding: 0.5rem 0.6rem;
        border-bottom: 1px solid #e3e7ec;
    }

    .info-table th {
        width: 32%;
        color: var(--primary-color);
    }

    .dlg-close {
        position: absolute;
        top: 10px;
        right: 12px;
        width: 38px;
        height: 38px;
        border: none;
        border-radius: 50%;
        background: rgba(0,0,0,0.55);
        color: white;
        font-size: 1.4rem;
        line-height: 1;
        cursor: pointer;
        z-index: 2;
    }

    .dlg-close:hover {
        background: rgba(0,0,0,0.8);
    }

    .dlg-actions {
        margin-top: 1.5rem;
        display: flex;
        gap: 0.6rem;
        flex-wrap: wrap;
    }

    .note {
        font-size: 0.85rem;
        color: #777;
        margin-top: 1rem;
    }

    .map-section {
        background: rgba(255,255,255,0.8);
        padding: 3rem 2rem;
        margin-top: 3rem;
        border-radius: 10px;
        text-align: center;
        box-shadow: 0 4px 15px rgba(0,0,0,0.08);
    }

    .map-section h2 {
        margin-bottom: 1.5rem;
        color: var(--primary-color);
    }

    .placeholder-map {
        width: 100%;
        height: 500px;
        border-radius: 10px;
        z-index: 1;
    }

    .leaflet-control-attribution {
        font-size: 10px;
        background: rgba(255,255,255,0.6) !important;
        padding: 0 5px;
    }

    .leaflet-popup-content h4 {
        color: var(--primary-color);
        margin-bottom: 0.3rem;
    }

    .leaflet-popup-content p {
        margin: 0 0 0.5rem;
        font-size: 0.9rem;
        text-align: left;
    }

    .popup-btn {
        padding: 0.3rem 0.8rem;
        background: var(--primary-color);
        color: white;
        border: none;
        border-radius: 4px;
        font-weight: bold;
        cursor: pointer;
    }

    footer {
        text-align: center;
        padding: 2rem;
        background: var(--primary-color);
        color: white;
        margin-top: 3rem;
    }

    footer .credit {
        font-size: 0.8rem;
        opacity: 0.8;
        margin-top: 0.5rem;
    }

    @media (max-width: 600px) {
        .dlg-body { padding: 1.2rem; }
        .dlg-img { height: 190px; }
        header h1 { font-size: 2rem; }
        .intro { padding: 1.2rem; }
    }
</style>
</head>
<body>

<header>
    <h1>Саратовская область</h1>
    <p>Волга, меловые горы, родники, легенды и места, с которых начался путь в космос</p>
</header>

<nav>
    <div class="nav-container">
        <a href="#attractions">Достопримечательности</a>
        <a href="#map">Карта</a>
    </div>
</nav>

<main>
    <p class="intro">
        Саратовская область раскинулась по берегам Волги. Здесь можно увидеть
        старинные музеи, лесистые горы национального парка, сельские мельницы и родники,
        утёсы с разбойничьими легендами и памятные места, связанные с первым полётом
        человека в космос.
    </p>

    <section id="attractions" class="attractions-grid"></section>

    <section id="map" class="map-section">
        <h2>Карта достопримечательностей</h2>
        <div id="map-canvas" class="placeholder-map"></div>
    </section>
</main>

<footer>
    <p>&copy; 2026 Путеводитель по Саратовской области</p>
    <p class="credit">Фотографии: Wikimedia Commons (свободные лицензии) и авторы изображений</p>
</footer>

<dialog id="details">
    <button class="dlg-close" id="dlg-close" aria-label="Закрыть">&times;</button>
    <div class="dlg-scroll" id="dlg-content"></div>
</dialog>

<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.js"></script>
<script>
    // ===== ДАННЫЕ =====
    // coords: [широта, долгота] — если известны.
    // geocode: строка для поиска координат в OpenStreetMap, если coords нет.
    // approx: true — метка показывает ближайший населённый пункт, а не точное место.
    const places = [
        {
            name: "Парк Победы на Соколовой горе",
            img: "images/park-pobedy.jpg",
            type: "Мемориал · Саратов",
            short: "Мемориал с монументом «Журавли» и панорамой на Волгу и город Саратов.",
            coords: [51.5423, 46.0616],
            history: [
                "Парк Победы расположен на Соколовой горе — одной из самых высоких точек над Волгой. Отсюда открывается широкая панорама: река, город, острова и Энгельс на левом берегу. Парк создавался как мемориал в память о подвиге народа в Великой Отечественной войне и стал одним из главных мест, куда саратовцы приходят в День Победы.",
                "Символом комплекса считается монумент «Журавли». Журавлиная стая — образ, знакомый по поэзии военных лет: птицы напоминают о тех, кто не вернулся с войны. На территории парка работает музей боевой славы, а рядом с ним под открытым небом представлена военная техника."
            ],
            highlights: [
                "Монумент «Журавли»",
                "Музей боевой славы",
                "Экспозиция военной техники под открытым небом",
                "Смотровые площадки с видом на Волгу и Энгельс"
            ],
            info: [
                ["Где находится", "Саратов, Соколовая гора"],
                ["Когда ехать", "В тёплое время года; особенно красиво на закате"],
                ["Совет", "На горе часто ветрено — возьмите куртку. Часы работы музея уточняйте заранее"]
            ]
        },
        {
            name: "Музей имени Радищева",
            img: "images/radishchev-museum.jpg",
            type: "Музей · Саратов",
            short: "Один из старейших художественных музеев России с богатой коллекцией живописи.",
            coords: [51.5337, 46.0168],
            history: [
                "Саратовский государственный художественный музей имени А. Н. Радищева был основан в 1885 году по инициативе художника Алексея Боголюбова — внука писателя Александра Радищева, чьё имя носит музей. Это один из старейших художественных музеев России за пределами столиц, расположенный в историческом здании конца XIX века.",
                "В собрании представлены русская живопись XVIII–XX веков, западноевропейское искусство, древнерусская иконопись и декоративно-прикладное искусство. Отдельный интерес для гостей — работы художников, связанных с Саратовским краем: Виктора Борисова-Мусатова, родившегося в Саратове, и Кузьмы Петрова-Водкина, уроженца Хвалынска."
            ],
            highlights: [
                "Русская живопись XVIII–XX веков",
                "Западноевропейское искусство",
                "Древнерусская иконопись",
                "Работы Борисова-Мусатова и Петрова-Водкина",
                "Историческое здание музея"
            ],
            info: [
                ["Адрес", "Саратов, ул. Радищева, 39"],
                ["Сколько времени нужно", "Около 1,5–2 часов на осмотр основных залов"],
                ["Совет", "Режим работы, цены и временные выставки смотрите на официальном сайте музея"]
            ]
        },
        {
            name: "Саратовская консерватория",
            img: "images/conservatory.jpg",
            type: "Архитектура и музыка · Саратов",
            short: "Историческое здание с концертным залом, одна из музыкальных жемчужин города.",
            coords: [51.5316, 46.0176],
            history: [
                "Саратовская государственная консерватория имени Л. В. Собинова открылась в 1912 году и по праву считается одной из старейших консерваторий России. Она носит имя прославленного русского тенора Леонида Собинова. Здание в центре города — заметный архитектурный памятник, часть культурного ядра Саратова.",
                "Консерватория — не только учебное заведение, но и действующая концертная площадка: в Большом зале регулярно выступают студенты, преподаватели и приглашённые артисты. Попасть на концерт — хороший способ почувствовать музыкальную атмосферу города."
            ],
            highlights: [
                "Историческое здание в центре города",
                "Концертный зал с регулярными выступлениями",
                "Студенческие и преподавательские концерты",
                "Прогулка по соседним улицам центра"
            ],
            info: [
                ["Адрес", "Саратов, проспект Кирова, 1"],
                ["Как попасть внутрь", "Проще всего — купить билет на концерт; афишу смотрите на сайте консерватории"],
                ["Совет", "Совместите визит с прогулкой по центру и набережной"]
            ]
        },
        {
            name: "Парк покорителей космоса им. Гагарина",
            img: "images/gagarin-landing.jpg",
            type: "Мемориал · близ Энгельса",
            short: "Мемориальный парк на месте приземления первого космонавта, в 16 км от Энгельса.",
            coords: [51.2835, 46.8175],
            history: [
                "12 апреля 1961 года Юрий Гагарин, совершив первый в истории орбитальный полёт, приземлился в Саратовской области — в поле близ села Смеловка в окрестностях Энгельса. По воспоминаниям очевидцев, первыми, кого он встретил, были местная жительница Анна Тахтарова и её внучка Рита.",
                "С Саратовом судьба Гагарина связана и раньше: здесь он учился в индустриальном техникуме и сделал первые шаги в авиации, занимаясь в аэроклубе. Поэтому для региона эта история особенно значима. На месте приземления создан Парк покорителей космоса, а в самом Саратове есть Набережная Космонавтов, названная в честь этого события."
            ],
            highlights: [
                "Мемориальный парк на месте приземления",
                "Открытое пространство и вид на степные окрестности",
                "Связанные места: Набережная Космонавтов в Саратове",
                "Рассказ о первом полёте человека в космос"
            ],
            info: [
                ["Где находится", "Окрестности села Смеловка, неподалёку от Энгельса"],
                ["Как добраться", "Автобусом из Энгельса или Саратова, на автомобиле либо с экскурсией; актуальные маршруты уточняйте заранее"],
                ["Совет", "Территория открытая и малотенистая: летом берите воду и головной убор, зимой одевайтесь теплее"]
            ]
        },
        {
            name: "Национальный парк «Хвалынский»",
            img: "images/khvalynsk-park.jpg",
            type: "Природа · Хвалынск",
            short: "Лесистые склоны Приволжской возвышенности, живописные виды и тропы для прогулок.",
            coords: [52.4933, 48.1003],
            history: [
                "Национальный парк «Хвалынский» создан в 1994 году в Хвалынском районе на правом берегу Волги. Его территорию занимают лесистые холмы Приволжской возвышенности, овраги, луга и меловые склоны. Здесь встречаются дубовые и липовые леса, а также редкие для региона виды растений и птиц.",
                "Рядом находится город Хвалынск — один из самых уютных городов Саратовской области: старинные улицы, волжские виды и знаменитые яблоневые сады. Здесь родился художник Кузьма Петров-Водкин, и в городе есть музей, посвящённый его жизни и творчеству."
            ],
            highlights: [
                "Пешие прогулки по лесным и холмистым тропам",
                "Виды на Волгу с высоких склонов",
                "Меловые склоны и разнообразная природа",
                "Город Хвалынск и музей Петрова-Водкина"
            ],
            info: [
                ["Где находится", "Хвалынский район, около 200 км от Саратова"],
                ["Когда ехать", "Конец весны, лето и начало осени"],
                ["Совет", "Дорога займёт несколько часов, поэтому лучше планировать поездку с ночёвкой. Правила посещения парка уточняйте у администрации"]
            ]
        },
        {
            name: "Меловые горы в Вольске",
            img: "images/volsk-chalk-mountains.jpg",
            type: "Природа и история · Вольск",
            short: "Белые склоны над Волгой и старые карьеры, связанные с историей цементной промышленности.",
            coords: [52.0390, 47.3830],
            history: [
                "Вольск — старый волжский город, известный меловыми горами и цементной промышленностью. Белые склоны над рекой — результат залегания мела, образовавшегося в меловом периоде, когда на месте этих земель было море. Контраст белого мела, зелени и синей Волги делает пейзаж необычным и фотогеничным.",
                "Добыча мела и производство цемента десятилетиями определяли облик города. Следы этой истории видны в старых карьерах и на склонах гор. В самом городе стоит заглянуть в краеведческий музей, чтобы лучше понять, как складывалась жизнь Вольска."
            ],
            highlights: [
                "Белые меловые склоны над Волгой",
                "Виды на реку и окрестности",
                "Старые карьеры (смотреть только издалека)",
                "Краеведческий музей и прогулка по городу"
            ],
            info: [
                ["Где находится", "Город Вольск, около 150 км от Саратова"],
                ["Когда ехать", "Тёплый сезон; для фото лучше ясная погода"],
                ["Безопасность", "Не спускайтесь в заброшенные карьеры и не подходите к краю обрывов: склоны могут осыпаться"]
            ]
        },

        // ===== НОВЫЕ МЕСТА =====
        {
            name: "Село Лох",
            img: "https://i.imgur.com/wvqjZkU.png",
            type: "История · Новобурасский район",
            short: "Старинное село с восстановленной водяной мельницей и легендой о разбойнике Кудеяре.",
            geocode: "село Лох, Новобурасский район, Саратовская область",
            history: [
                "Село основано в 1698 году. До революции оно процветало, в советское время пришло в упадок. Примерно с середины 2000-х энтузиасты из Саратова начали возрождать исторические места, а в 2020-х Лох стал известен любителям экологического туризма.",
                "Происхождение названия до сих пор вызывает споры: его связывают с растением лох, с рыбой и с немецким словом Loch («яма»). Сами жители шутливо расшифровывают его как «Людей Объединяет Хорошее». Указатель с названием на въезде туристы регулярно увозят на память, и власти района закупают запасные знаки.",
                "С окрестностями связана легенда о разбойнике Кудеяре: по преданию, он жил в пещере и прятал там награбленные сокровища. Сегодня эта территория — памятник природы «Кудеярова пещера»."
            ],
            highlights: [
                "Водяная мельница — единственная отреставрированная в регионе",
                "Храм Михаила Архангела: его возрождают сами жители",
                "Кудеярова пещера и Симов родник",
                "Буквы «ЛОХ» в центре села, гончарная мастерская и сувенирная лавка",
                "Местные продукты, в том числе сыр"
            ],
            info: [
                ["Где находится", "Новобурасский район, примерно полтора часа езды от Саратова"],
                ["Сколько времени нужно", "Основные места можно обойти пешком за несколько часов; многие приезжают на целый день"],
                ["Важно", "В конце октября 2026 года возле села горел лес на территории памятника природы «Кудеярова пещера». Перед поездкой уточните, открыт ли маршрут"]
            ]
        },
        {
            name: "Дунина гора",
            img: "images/dunina-gora.jpg",
            type: "Геология · у реки Медведицы",
            short: "Геологический останец у реки Медведицы — место силы природы.",
            history: [
                "Геологический останец у реки Медведицы — место силы природы."
            ],
            highlights: [],
            info: [
                ["Где находится", "Окрестности реки Медведицы (точное место уточните перед поездкой)"]
            ]
        },
        {
            name: "Утёс Степана Разина",
            img: "images/utyos-razina.jpg",
            type: "Легенды · Белогорское",
            short: "Крутой обрыв над Волгой, окружённый легендами о Степане Разине.",
            geocode: "село Белогорское, Красноармейский район, Саратовская область",
            approx: true,
            history: [
                "Утёс Степана Разина — высокий обрыв над правым берегом Волги у села Белогорское, на границе Саратовской и Волгоградской областей. Сегодня это одно из самых популярных мест области: маршрут «Саратов — Утёс Степана Разина» входит в число самых востребованных автомобильных.",
                "Утёс рассекает глубокий Невольничий овраг: по преданию, атаман держал в нём пленников. С этими местами связывают лагерь разбойников, нападения на проходящие корабли и историю с персидской княжной. Это народные предания, а не доказанные факты."
            ],
            highlights: [
                "Вид на Волгу с высокого берега",
                "Невольничий овраг",
                "Степные склоны и каменистый берег у подножия",
                "Легенды о Стеньке Разине"
            ],
            info: [
                ["Где находится", "Село Белогорское, Красноармейский район, около 120 км от Саратова"],
                ["Как добраться", "На автомобиле: общественный транспорт к утёсу не ходит"],
                ["Совет", "Дороги бывают плохими, а кафе, магазинов и гостиниц рядом мало — берите воду и еду. К краю обрыва не подходите"]
            ]
        },
        {
            name: "Серебряный родник",
            img: "https://i.imgur.com/xgKJrQl.png",
            type: "Природа · Базарный Карабулак",
            short: "Родник среди лесного массива у села Алексеевка, который местные турбазы относят к лучшим в области.",
            geocode: "село Алексеевка, Базарно-Карабулакский район, Саратовская область",
            approx: true,
            history: [
                "Родник «Серебряный» находится недалеко от Базарного Карабулака, у села Алексеевка, среди большого лесного массива с папоротниковой зоной. Местные турбазы называют его одним из лучших и самых чистых родников области.",
                "Название «Серебряный» носят и другие родники, поэтому перед поездкой убедитесь, что вы едете именно к этому."
            ],
            highlights: [
                "Родниковая вода среди леса",
                "Тишина и удалённость от трасс и городов",
                "Прогулки по лесу рядом с родником"
            ],
            info: [
                ["Где находится", "Окрестности села Алексеевка, Базарно-Карабулакский район, около 80 км от Саратова"],
                ["Совет", "Для питья используйте воду только после проверки: ориентируйтесь на свежие данные анализов и рекомендации местных жителей"]
            ]
        }
    ];

    // ===== КАРТОЧКИ =====
    const grid = document.getElementById('attractions');
    places.forEach((p, i) => {
        const hasMap = !!(p.coords || p.geocode);
        const card = document.createElement('div');
        card.className = 'card';
        card.innerHTML =
            '<img src="' + p.img + '" alt="' + p.name + '" loading="lazy">' +
            '<div class="card-content">' +
                '<span class="tag">' + p.type + '</span>' +
                '<h3>' + p.name + '</h3>' +
                '<p>' + p.short + '</p>' +
                '<div class="card-buttons">' +
                    '<button class="btn" data-details="' + i + '">Подробнее</button>' +
                    (hasMap ? '<a class="btn outline" href="#map" data-place="' + i + '">На карте</a>' : '') +
                '</div>' +
            '</div>';
        grid.appendChild(card);
    });

    // ===== ФОТО =====
    // Строка — поиск главного фото статьи в Википедии.
    // Объект {commons, article} — поиск файлов на Wikimedia Commons, затем статьи.
    // null — автоподбор не нужен (останется заглушка, если файла нет).
    const photoQueries = [
        "Парк Победы Саратов Соколовая гора",
        "Саратовский художественный музей имени Радищева",
        "Саратовская консерватория имени Собинова",
        { commons: "Парк покорителей космоса Гагарина", article: "Парк покорителей космоса" },
        "Хвалынский национальный парк",
        "Вольск меловые горы",
        "Лох село Саратовская область",
        null,
        { commons: "Утёс Степана Разина", article: "Утёс Степана Разина" },
        null
    ];

    function placeholder(text) {
        const svg =
            '<svg xmlns="http://www.w3.org/2000/svg" width="600" height="400">' +
            '<rect width="100%" height="100%" fill="#eef0f2"/>' +
            '<text x="50%" y="50%" fill="#8a94a0" font-family="Arial" font-size="28" ' +
            'text-anchor="middle" dominant-baseline="middle">' + text + '</text></svg>';
        return 'data:image/svg+xml;charset=utf-8,' + encodeURIComponent(svg);
    }

    async function wikiPhoto(query) {
        const url = 'https://ru.wikipedia.org/w/api.php?action=query&format=json&origin=*' +
            '&generator=search&gsrlimit=3&prop=pageimages&piprop=thumbnail&pithumbsize=900' +
            '&gsrsearch=' + encodeURIComponent(query);
        const data = await (await fetch(url)).json();
        const pages = Object.values((data.query || {}).pages || {})
            .sort((a, b) => a.index - b.index);
        const hit = pages.find(p => p.thumbnail);
        return hit ? hit.thumbnail.source : null;
    }

    async function commonsPhoto(query) {
        const url = 'https://commons.wikimedia.org/w/api.php?action=query&format=json&origin=*' +
            '&generator=search&gsrnamespace=6&gsrlimit=8&prop=imageinfo&iiprop=url&iiurlwidth=900' +
            '&gsrsearch=' + encodeURIComponent(query);
        const data = await (await fetch(url)).json();
        const pages = Object.values((data.query || {}).pages || {})
            .sort((a, b) => a.index - b.index);
        const hit = pages.find(p => p.imageinfo && /\.(jpe?g|png)$/i.test(p.title));
        return hit ? hit.imageinfo[0].thumburl : null;
    }

    function setPhoto(i, url) {
        places[i].img = url; // подхватится и в окне «Подробнее»
        document.querySelectorAll('.card')[i].querySelector('img').src = url;
    }

    places.forEach((p, i) => {
        const probe = new Image();
        // Если файл не загрузился — ищем фото онлайн, иначе ставим заглушку
        probe.onerror = async () => {
            try {
                const q = photoQueries[i];
                let photo = null;
                if (q) {
                    photo = (typeof q === 'object')
                        ? (await commonsPhoto(q.commons)) || (await wikiPhoto(q.article))
                        : await wikiPhoto(q);
                }
                setPhoto(i, photo || placeholder(p.name));
            } catch (e) {
                setPhoto(i, placeholder(p.name));
            }
        };
        probe.src = p.img;
    });

    // ===== КАРТА =====
    const map = L.map('map-canvas');
    map.attributionControl.setPrefix(false);

    L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
        maxZoom: 18,
        attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>'
    }).addTo(map);

    const markers = [];

    function addMarker(i) {
        const p = places[i];
        if (!p.coords || markers[i]) return;
        markers[i] = L.marker(p.coords)
            .addTo(map)
            .bindPopup(
                '<h4>' + p.name + '</h4>' +
                '<p>' + p.short + '</p>' +
                (p.approx ? '<p><i>Метка показывает ближайший населённый пункт.</i></p>' : '') +
                '<button class="popup-btn" data-details="' + i + '">Подробнее</button>'
            );
    }

    function fitAll() {
        const pts = places.filter(p => p.coords).map(p => p.coords);
        if (pts.length) map.fitBounds(L.latLngBounds(pts).pad(0.15));
    }

    places.forEach((p, i) => addMarker(i));
    fitAll();

    // Поиск координат по названию (OpenStreetMap Nominatim) для мест без coords
    const sleep = ms => new Promise(r => setTimeout(r, ms));

    async function geocode(q) {
        const url = 'https://nominatim.openstreetmap.org/search?format=json&limit=1&accept-language=ru&q=' +
            encodeURIComponent(q);
        const data = await (await fetch(url)).json();
        return data[0] ? [Number(data[0].lat), Number(data[0].lon)] : null;
    }

    (async () => {
        for (let i = 0; i < places.length; i++) {
            const p = places[i];
            if (p.coords || !p.geocode) continue;
            try {
                const c = await geocode(p.geocode);
                if (c) {
                    p.coords = c;
                    addMarker(i);
                    fitAll();
                }
            } catch (e) { /* без метки, если поиск не сработал */ }
            await sleep(1100); // не чаще одного запроса в секунду
        }
    })();

    function showOnMap(i) {
        document.getElementById('map').scrollIntoView({ behavior: 'smooth' });
        if (!markers[i]) return;
        map.flyTo(places[i].coords, places[i].approx ? 12 : 13);
        markers[i].openPopup();
    }

    // ===== ОКНО С ПОДРОБНОСТЯМИ =====
    const dlg = document.getElementById('details');
    const dlgContent = document.getElementById('dlg-content');

    function openDetails(i) {
        const p = places[i];
        const hasMap = !!(p.coords || p.geocode);
        dlgContent.innerHTML =
            '<img class="dlg-img" src="' + p.img + '" alt="' + p.name + '">' +
            '<div class="dlg-body">' +
                '<span class="tag">' + p.type + '</span>' +
                '<h2>' + p.name + '</h2>' +
                p.history.map(t => '<p>' + t + '</p>').join('') +
                (p.highlights.length
                    ? '<h4>Что посмотреть</h4><ul>' + p.highlights.map(h => '<li>' + h + '</li>').join('') + '</ul>'
                    : '') +
                (p.info.length
                    ? '<h4>Практическая информация</h4><table class="info-table">' +
                        p.info.map(r => '<tr><th>' + r[0] + '</th><td>' + r[1] + '</td></tr>').join('') +
                      '</table>'
                    : '') +
                '<p class="note">Режим работы, цены, условия посещения и состояние дорог могут меняться — проверяйте актуальные данные перед поездкой.</p>' +
                '<div class="dlg-actions">' +
                    (hasMap ? '<button class="btn" data-map="' + i + '">Показать на карте</button>' : '') +
                    '<button class="btn outline" data-close>Закрыть</button>' +
                '</div>' +
            '</div>';
        dlgContent.scrollTop = 0;
        if (!dlg.open) dlg.showModal();
    }

    document.getElementById('dlg-close').addEventListener('click', () => dlg.close());

    dlg.addEventListener('click', e => {
        if (e.target === dlg) dlg.close();
    });

    // ===== ОБРАБОТЧИКИ КЛИКОВ =====
    document.addEventListener('click', e => {
        const detailsBtn = e.target.closest('[data-details]');
        if (detailsBtn) {
            map.closePopup();
            openDetails(Number(detailsBtn.dataset.details));
            return;
        }

        const mapBtn = e.target.closest('[data-map]');
        if (mapBtn) {
            dlg.close();
            showOnMap(Number(mapBtn.dataset.map));
            return;
        }

        if (e.target.closest('[data-close]')) {
            dlg.close();
            return;
        }

        const placeLink = e.target.closest('[data-place]');
        if (placeLink) {
            e.preventDefault();
            showOnMap(Number(placeLink.dataset.place));
        }
    });
</script>

</body>
</html>
