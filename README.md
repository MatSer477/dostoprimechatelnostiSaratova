<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Достопримечательности Саратовской области</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.css">
<style>
    :root {
        --primary-color: #004080;
        --secondary-color: #0066cc;
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
        /* Фон: узор из волн поверх градиента «небо — берег» */
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
    <p>Волга, меловые горы и места, с которых начался путь в космос</p>
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
        старинные театры и музеи, лесистые горы национального парка и памятные места,
        связанные с первым полётом человека в космос.
    </p>

    <section id="attractions" class="attractions-grid"></section>

    <section id="map" class="map-section">
        <h2>Карта достопримечательностей</h2>
        <div id="map-canvas" class="placeholder-map"></div>
    </section>
</main>

<footer>
    <p>&copy; 2026 Путеводитель по Саратовской области</p>
    <p class="credit">Фотографии: Wikimedia Commons (свободные лицензии)</p>
</footer>

<!-- Окно с подробной информацией -->
<dialog id="details">
    <button class="dlg-close" id="dlg-close" aria-label="Закрыть">&times;</button>
    <div class="dlg-scroll" id="dlg-content"></div>
</dialog>

<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.js"></script>
<script>
    // ===== ДАННЫЕ =====
    // Чтобы добавить место, допишите объект в этот список — карточка, окно и метка появятся сами.
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
            name: "Место приземления Гагарина",
            img: "images/gagarin-landing.jpg",
            type: "Мемориал · близ Энгельса",
            short: "Мемориальный комплекс близ Энгельса, где в 1961 году приземлился первый космонавт.",
            coords: [51.2835, 46.8175],
            history: [
                "12 апреля 1961 года Юрий Гагарин, совершив первый в истории орбитальный полёт, приземлился в Саратовской области — в поле близ села Смеловка в окрестностях Энгельса. По воспоминаниям очевидцев, первыми, кого он встретил, были местная жительница Анна Тахтарова и её внучка Рита.",
                "С Саратовом судьба Гагарина связана и раньше: здесь он учился в индустриальном техникуме и сделал первые шаги в авиации, занимаясь в аэроклубе. Поэтому для региона эта история особенно значима. На месте приземления создан мемориальный комплекс, а в самом Саратове есть Набережная Космонавтов, названная в честь этого события."
            ],
            highlights: [
                "Мемориальный комплекс на месте приземления",
                "Открытое пространство и вид на степные окрестности",
                "Связанные места: Набережная Космонавтов в Саратове",
                "Рассказ о первом полёте человека в космос"
            ],
            info: [
                ["Где находится", "Окрестности села Смеловка, неподалёку от Энгельса"],
                ["Как добраться", "Удобнее всего на автомобиле или с экскурсией из Саратова"],
                ["Совет", "Перед поездкой уточните маршрут и состояние дороги, а также время работы мемориала"]
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
        }
    ];

    // ===== КАРТОЧКИ =====
    const grid = document.getElementById('attractions');
    places.forEach((p, i) => {
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
                    '<a class="btn outline" href="#map" data-place="' + i + '">На карте</a>' +
                '</div>' +
            '</div>';
        grid.appendChild(card);
    });

    // ===== АВТОПОДБОР ФОТО ИЗ ВИКИПЕДИИ =====
    // Работает, если локального файла из images/ нет. Порядок как в places.
    const photoQueries = [
        "Парк Победы Саратов Соколовая гора",
        "Саратовский художественный музей имени Радищева",
        "Саратовская консерватория имени Собинова",
        "Приземление Гагарина Смеловка памятник",
        "Хвалынский национальный парк",
        "Вольск меловые горы"
    ];

    async function wikiPhoto(query) {
        const url = 'https://ru.wikipedia.org/w/api.php?action=query&format=json&origin=*' +
            '&generator=search&gsrlimit=3&prop=pageimages&piprop=thumbnail&pithumbsize=900' +
            '&gsrsearch=' + encodeURIComponent(query);
        const res = await fetch(url);
        const data = await res.json();
        const pages = Object.values((data.query || {}).pages || {})
            .sort((a, b) => a.index - b.index);
        const hit = pages.find(p => p.thumbnail);
        return hit ? hit.thumbnail.source : null;
    }

    places.forEach((p, i) => {
        const probe = new Image();
        probe.onerror = async () => {
            try {
                const photo = await wikiPhoto(photoQueries[i]);
                if (!photo) return;
                places[i].img = photo; // подхватится и в окне «Подробнее»
                document.querySelectorAll('.card')[i].querySelector('img').src = photo;
            } catch (e) { /* без интернета останется серая заглушка */ }
        };
        probe.src = p.img;
    });

    // ===== КАРТА =====
    const map = L.map('map-canvas');

    // Убираем «Leaflet» с флажком; подпись OpenStreetMap оставляем (требование лицензии)
    map.attributionControl.setPrefix(false);

    L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
        maxZoom: 18,
        attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>'
    }).addTo(map);

    const markers = places.map((p, i) =>
        L.marker(p.coords)
            .addTo(map)
            .bindPopup(
                '<h4>' + p.name + '</h4>' +
                '<p>' + p.short + '</p>' +
                '<button class="popup-btn" data-details="' + i + '">Подробнее</button>'
            )
    );

    map.fitBounds(L.latLngBounds(places.map(p => p.coords)).pad(0.15));

    function showOnMap(i) {
        document.getElementById('map').scrollIntoView({ behavior: 'smooth' });
        map.flyTo(places[i].coords, 13);
        markers[i].openPopup();
    }

    // ===== ОКНО С ПОДРОБНОСТЯМИ =====
    const dlg = document.getElementById('details');
    const dlgContent = document.getElementById('dlg-content');

    function openDetails(i) {
        const p = places[i];
        dlgContent.innerHTML =
            '<img class="dlg-img" src="' + p.img + '" alt="' + p.name + '">' +
            '<div class="dlg-body">' +
                '<span class="tag">' + p.type + '</span>' +
                '<h2>' + p.name + '</h2>' +
                p.history.map(t => '<p>' + t + '</p>').join('') +
                '<h4>Что посмотреть</h4>' +
                '<ul>' + p.highlights.map(h => '<li>' + h + '</li>').join('') + '</ul>' +
                '<h4>Практическая информация</h4>' +
                '<table class="info-table">' +
                    p.info.map(r => '<tr><th>' + r[0] + '</th><td>' + r[1] + '</td></tr>').join('') +
                '</table>' +
                '<p class="note">Режим работы, цены и условия посещения могут меняться — проверяйте актуальные данные перед поездкой.</p>' +
                '<div class="dlg-actions">' +
                    '<button class="btn" data-map="' + i + '">Показать на карте</button>' +
                    '<button class="btn outline" data-close>Закрыть</button>' +
                '</div>' +
            '</div>';
        dlgContent.scrollTop = 0;
        if (!dlg.open) dlg.showModal();
    }

    document.getElementById('dlg-close').addEventListener('click', () => dlg.close());

    // Закрытие по клику на затемнённый фон
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
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Путеводитель по Саратовской области</title>
    <!-- Подключение шрифта -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter&display=swap" rel="stylesheet">
    <style>
        /* Базовые настройки */
        :root {
            --text-color: #333;
            --primary-color: #004d9e; /* Основной синий */
            --secondary-color: #1a75cc; /* Акцентный голубой */
        }

        *,
        *::before,
        *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            line-height: 1.6;
            color: var(--text-color);
            font-family: 'Inter', Arial, sans-serif;
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

        .attractions-grid {
            display: grid;
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto 3rem;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        }

        .card {
            background: white;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            display: flex;
            flex-direction: column;
            position: relative;
        }

        .card img {
            width: 100%;
            aspect-ratio: 3 / 2;
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
            align-self: flex-start;
            font-size: 0.75rem;
            font-weight: bold;
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

        .card-buttons a {
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
            transition: all 0.3s;
        }

        .card-buttons a.outline {
            background: transparent;
            color: var(--primary-color);
        }

        .card-buttons a:hover {
            background: var(--secondary-color);
            border-color: var(--secondary-color);
        }

        dialog.modal {
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

        @media (max-width: 600px) {
            .dlg-body { padding: 1.2rem; }
            .dlg-img { height: 190px; }
            header h1 { font-size: 2rem; }
        }
    </style>
</head>
<body>

<header>
    <h1>Путеводитель по Саратовской области</h1>
    <p>Откройте для себя красоту Поволжья!</p>
</header>

<!-- Блок с достопримечательностями -->
<section class="attractions-grid">
    <!-- Село Лох -->
    <article class="card" data-dialog="#dlg-lokh">
        <img src="https://via.placeholder.com/600x400/EEF0F2/AAAAAA/?text=%D0%A1%D0%B5%D0%BB%D0%BE+%D0%9B%D0%BE%D1%85" alt="Село Лох">
        <div class="card-content">
            <span class="tag">История</span>
            <h3>Село Лох</h3>
            <p>Старинное село на берегу Волги — колыбель истории региона.</p>
            <div class="card-buttons">
                <a href="#" class="btn" onclick="openDlg('dlg-lokh')">Подробнее</a>
                <a href="#" class="btn outline" target="_blank">Маршрут</a>
            </div>
        </div>
    </article>

    <!-- Дунина гора -->
    <article class="card" data-dialog="#dlg-duinina-gora">
        <img src="https://via.placeholder.com/600x400/EEF0F2/AAAAAA/?text=%D0%94%D1%83%D0%BD%D0%B8%D0%BD%D0%B0+%D0%B3%D0%BE%D1%80%D0%B0" alt="Дунина гора">
        <div class="card-content">
            <span class="tag">Природа</span>
            <h3>Дунина гора</h3>
            <p>Уникальный геологический памятник с видом на пойму реки Медведицы.</p>
            <div class="card-buttons">
                <a href="#" class="btn" onclick="openDlg('dlg-duinina-gora')">Подробнее</a>
                <a href="#" class="btn outline" target="_blank">Маршрут</a>
            </div>
        </div>
    </article>

    <!-- Серебряный родник -->
    <article class="card" data-dialog="#dlg-srebrnyy-rodnik">
        <img src="https://via.placeholder.com/600x400/EEF0F2/AAAAAA/?text=%D0%A1%D0%B5%D1%80%D0%B5%D0%B1%D1%80%D1%8F%D0%BD%D1%8B%D0%B9+%D1%80%D0%BE%D0%B4%D0%BD%D0%B8%D0%BA" alt="Серебряный родник">
        <div class="card-content">
            <span class="tag">Экология</span>
            <h3>Серебряный родник</h3>
            <p>Святой источник с кристально чистой водой, окутанный легендами.</p>
            <div class="card-buttons">
                <a href="#" class="btn" onclick="openDlg('dlg-srebrnyy-rodnik')">Подробнее</a>
                <a href="#" class="btn outline" target="_blank">Маршрут</a>
            </div>
        </div>
    </article>
</section>

<!-- Модальные окна -->

<!-- Село Лох -->
<dialog id="dlg-lokh" class="modal">
    <button class="dlg-close" aria-label="Закрыть диалог" title="Закрыть диалог">×</button>
    <div class="dlg-scroll">
        <img class="dlg-img" src="https://via.placeholder.com/1200x260/EEF0F2/AAAAAA/?text=%D0%A1%D0%B5%D0%BB%D0%BE+%D0%9B%D0%BE%D1%85" alt="Село Лох">
        <div class="dlg-body">
            <h2>Село Лох</h2>
            <p><strong>Локализация:</strong> Саратовская область, Балашовский район.</p>
            <p>Основанное в XVII веке, это одно из старейших поселений региона. Название происходит от финно-угорского слова «лох», что означает «рыба». Село знаменито своими рыбными промыслами и живописным расположением на высоком правом берегу Волги.</p>
            <p>Главные точки притяжения: старинная деревянная церковь, краеведческий музей и набережная с видом на реку.</p>
            <div class="dlg-actions">
                <a href="#" class="btn" target="_blank">Официальный сайт</a>
                <a href="#" class="btn outline" target="_blank">Фотогалерея</a>
            </div>
        </div>
    </div>
</dialog>

<!-- Дунина гора -->
<dialog id="dlg-duinina-gora" class="modal">
    <button class="dlg-close" aria-label="Закрыть диалог" title="Закрыть диалог">×</button>
    <div class="dlg-scroll">
        <img class="dlg-img" src="https://via.placeholder.com/1200x260/EEF0F2/AAAAAA/?text=%D0%94%D1%83%D0%BD%D0%B8%D0%BD%D0%B0+%D0%B3%D0%BE%D1%80%D0%B0" alt="Дунина гора">
        <div class="dlg-body">
            <h2>Дунина гора</h2>
            <p><strong>Локализация:</strong> Саратовская область, окрестности г. Вольск.</p>
            <p>Это уникальный останец, возвышающийся над долиной р. Медведицы. Гора сложена древними известняками и песчаниками, которые формируют причудливые скалы и гроты.</p>
            <p>Здесь находится ботанический заказник с редкими видами растений. С вершины открывается панорамный вид на бескрайние степи и извилистую речную долину.</p>
            <div class="info-table">
                <table>
                    <tr>
                        <th>Высота:</th>
                        <td>≈80 м над уровнем реки</td>
                    </tr>
                    <tr>
                        <th>Статус:</th>
                        <td>Геологический памятник природы</td>
                    </tr>
                </table>
            </div>
            <div class="dlg-actions">
                <a href="#" class="btn" target="_blank">Как добраться</a>
                <a href="#" class="btn outline" target="_blank">Правила посещения</a>
            </div>
        </div>
    </div>
</dialog>

<!-- Серебряный родник -->
<dialog id="dlg-srebrnyy-rodnik" class="modal">
    <button class="dlg-close" aria-label="Закрыть диалог" title="Закрыть диалог">×</button>
    <div class="dlg-scroll">
        <img class="dlg-img" src="https://via.placeholder.com/1200x260/EEF0F2/AAAAAA/?text=%D0%A1%D0%B5%D1%80%D0%B5%D0%B1%D1%80%D1%8F%D0%BD%D1%8B%D0%B9+%D1%80%D0%BE%D0%B4%D0%BD%D0%B8%D0%BA" alt="Серебряный родник">
        <div class="dlg-body">
            <h2>Серебряный родник</h2>
            <p><strong>Локализация:</strong> Саратовская область, Хвалынский район.</p>
            <p>Один из самых известных святых источников области. Вода здесь считается целебной благодаря высокому содержанию серебра и других микроэлементов.</p>
            <ul>
                <li>Температура воды круглый год ≈+7 °C;</li>
                <li>Вода пригодна для питья после кипячения;</li>
                <li>Рядом есть парковка и зона отдыха.</li>
            </ul>
            <div class="dlg-actions">
                <a href="#" class="btn" target="_blank">Посмотреть карту</a>
                <a href="#" class="btn outline" target="_blank">Отзывы туристов</a>
            </div>
        </div>
    </div>
</dialog>

<!-- Скрипт для открытия модальных окон -->
<script>
function openDlg(id) {
    const dlg = document.getElementById(id);
    if (!dlg.showModal) {
        // Полифилл для старых браузеров
        import('https://unpkg.com/@webcomponents/dialog@latest/dist/dialog.min.js')
          .then(module => module.defineCustomElements(window))
          .catch(() => console.warn('Полифилл не загрузился.'));
    }
    dlg.showModal();
}
document.querySelectorAll('.dlg-close').forEach(btn => btn.addEventListener('click', () => btn.closest('dialog').close()));
</script>

<footer style="padding: 2rem; text-align: center; background: var(--primary-color); color: white;">
    © 2026 Путеводитель по Саратовской области<br>
    Фотографии: Wikimedia Commons (свободные лицензии)
</footer>

</body>
</html>
