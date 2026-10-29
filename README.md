<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Достопримечательности Саратовской области</title>
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
        background-color: #fff;
    }

    header {
        background: linear-gradient(135deg, var(--primary-color), #003366);
        color: white;
        padding: 2rem 0;
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
        background: var(--bg-light);
        padding: 1rem 0;
        position: sticky;
        top: 0;
        z-index: 100;
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
        margin-bottom: 3rem;
        font-size: 1.1rem;
        line-height: 1.8;
        max-width: 800px;
        margin-left: auto;
        margin-right: auto;
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

    .card a {
        display: inline-block;
        margin-top: 1rem;
        padding: 0.5rem 1rem;
        background: var(--primary-color);
        color: white;
        text-decoration: none;
        border-radius: 5px;
        text-align: center;
        font-weight: bold;
    }

    .card a:hover {
        background: var(--secondary-color);
    }

    .map-section {
        background: var(--bg-light);
        padding: 3rem 2rem;
        margin-top: 3rem;
        border-radius: 10px;
        text-align: center;
    }

    .map-section h2 {
        margin-bottom: 1.5rem;
        color: var(--primary-color);
    }

    .placeholder-map {
        width: 100%;
        height: 400px;
        border: 0;
        border-radius: 10px;
    }

    footer {
        text-align: center;
        padding: 2rem;
        background: var(--primary-color);
        color: white;
        margin-top: 3rem;
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

    <section id="attractions" class="attractions-grid">

        <div class="card">
            <img src="images/park-pobedy.jpg" alt="Парк Победы на Соколовой горе" loading="lazy">
            <div class="card-content">
                <h3>Парк Победы на Соколовой горе</h3>
                <p>Мемориал с монументом «Журавли» и панорамой на Волгу и город Саратов.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

        <div class="card">
            <img src="images/radishchev-museum.jpg" alt="Музей имени Радищева" loading="lazy">
            <div class="card-content">
                <h3>Музей имени Радищева</h3>
                <p>Один из старейших художественных музеев России с богатой коллекцией живописи.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

        <div class="card">
            <img src="images/conservatory.jpg" alt="Саратовская консерватория" loading="lazy">
            <div class="card-content">
                <h3>Саратовская консерватория</h3>
                <p>Историческое здание с концертным залом, одна из музыкальных жемчужин города.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

        <div class="card">
            <img src="images/gagarin-landing.jpg" alt="Место приземления Гагарина" loading="lazy">
            <div class="card-content">
                <h3>Место приземления Гагарина</h3>
                <p>Мемориальный комплекс близ Энгельса, где в 1961 году приземлился первый космонавт.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

        <div class="card">
            <img src="images/khvalynsk-park.jpg" alt="Национальный парк «Хвалынский»" loading="lazy">
            <div class="card-content">
                <h3>Национальный парк «Хвалынский»</h3>
                <p>Лесистые склоны Приволжской возвышенности, живописные виды и тропы для прогулок.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

        <div class="card">
            <img src="images/volsk-chalk-mountains.jpg" alt="Меловые горы в Вольске" loading="lazy">
            <div class="card-content">
                <h3>Меловые горы в Вольске</h3>
                <p>Белые склоны над Волгой и старые карьеры, связанные с историей цементной промышленности.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

    </section>

    <section id="map" class="map-section">
        <h2>Карта</h2>
        <iframe class="placeholder-map"
            src="https://www.openstreetmap.org/export/embed.html?bbox=45.85,51.40,46.25,51.65&layer=mapnik"
            loading="lazy"></iframe>
    </section>
</main>

<footer>
    <p>&copy; 2026 Путеводитель по Саратовской области</p>
</footer>

</body>
</html><!DOCTYPE html>
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
        background-color: #fff;
    }

    header {
        background: linear-gradient(135deg, var(--primary-color), #003366);
        color: white;
        padding: 2rem 0;
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
        background: var(--bg-light);
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
        margin-bottom: 3rem;
        font-size: 1.1rem;
        line-height: 1.8;
        max-width: 800px;
        margin-left: auto;
        margin-right: auto;
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

    .card a {
        display: inline-block;
        margin-top: 1rem;
        padding: 0.5rem 1rem;
        background: var(--primary-color);
        color: white;
        text-decoration: none;
        border-radius: 5px;
        text-align: center;
        font-weight: bold;
    }

    .card a:hover {
        background: var(--secondary-color);
    }

    .map-section {
        background: var(--bg-light);
        padding: 3rem 2rem;
        margin-top: 3rem;
        border-radius: 10px;
        text-align: center;
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

    .leaflet-popup-content h4 {
        color: var(--primary-color);
        margin-bottom: 0.3rem;
    }

    .leaflet-popup-content p {
        margin: 0;
        font-size: 0.9rem;
        text-align: left;
    }

    footer {
        text-align: center;
        padding: 2rem;
        background: var(--primary-color);
        color: white;
        margin-top: 3rem;
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

    <section id="attractions" class="attractions-grid">

        <div class="card">
            <img src="images/park-pobedy.jpg" alt="Парк Победы на Соколовой горе" loading="lazy">
            <div class="card-content">
                <h3>Парк Победы на Соколовой горе</h3>
                <p>Мемориал с монументом «Журавли» и панорамой на Волгу и город Саратов.</p>
                <a href="#map" data-place="0">Показать на карте</a>
            </div>
        </div>

        <div class="card">
            <img src="images/radishchev-museum.jpg" alt="Музей имени Радищева" loading="lazy">
            <div class="card-content">
                <h3>Музей имени Радищева</h3>
                <p>Один из старейших художественных музеев России с богатой коллекцией живописи.</p>
                <a href="#map" data-place="1">Показать на карте</a>
            </div>
        </div>

        <div class="card">
            <img src="images/conservatory.jpg" alt="Саратовская консерватория" loading="lazy">
            <div class="card-content">
                <h3>Саратовская консерватория</h3>
                <p>Историческое здание с концертным залом, одна из музыкальных жемчужин города.</p>
                <a href="#map" data-place="2">Показать на карте</a>
            </div>
        </div>

        <div class="card">
            <img src="images/gagarin-landing.jpg" alt="Место приземления Гагарина" loading="lazy">
            <div class="card-content">
                <h3>Место приземления Гагарина</h3>
                <p>Мемориальный комплекс близ Энгельса, где в 1961 году приземлился первый космонавт.</p>
                <a href="#map" data-place="3">Показать на карте</a>
            </div>
        </div>

        <div class="card">
            <img src="images/khvalynsk-park.jpg" alt="Национальный парк «Хвалынский»" loading="lazy">
            <div class="card-content">
                <h3>Национальный парк «Хвалынский»</h3>
                <p>Лесистые склоны Приволжской возвышенности, живописные виды и тропы для прогулок.</p>
                <a href="#map" data-place="4">Показать на карте</a>
            </div>
        </div>

        <div class="card">
            <img src="images/volsk-chalk-mountains.jpg" alt="Меловые горы в Вольске" loading="lazy">
            <div class="card-content">
                <h3>Меловые горы в Вольске</h3>
                <p>Белые склоны над Волгой и старые карьеры, связанные с историей цементной промышленности.</p>
                <a href="#map" data-place="5">Показать на карте</a>
            </div>
        </div>

    </section>

    <section id="map" class="map-section">
        <h2>Карта достопримечательностей</h2>
        <div id="map-canvas" class="placeholder-map"></div>
    </section>
</main>

<footer>
    <p>&copy; 2026 Путеводитель по Саратовской области</p>
</footer>

<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.js"></script>
<script>
    // Список мест: порядок соответствует data-place в карточках.
    // Чтобы добавить место, допишите строку сюда (и карточку в HTML).
    const places = [
        { name: "Парк Победы на Соколовой горе", coords: [51.5655, 45.9680],
          text: "Мемориал с монументом «Журавли» и видом на Волгу." },
        { name: "Музей имени Радищева", coords: [51.5337, 46.0168],
          text: "Один из старейших художественных музеев России." },
        { name: "Саратовская консерватория", coords: [51.5316, 46.0176],
          text: "Историческое здание с концертным залом." },
        { name: "Место приземления Гагарина", coords: [51.2835, 46.8175],
          text: "Мемориальный комплекс близ Энгельса." },
        { name: "Национальный парк «Хвалынский»", coords: [52.4933, 48.1003],
          text: "Лесистые склоны Приволжской возвышенности." },
        { name: "Меловые горы в Вольске", coords: [52.0390, 47.3830],
          text: "Белые склоны над Волгой и старые карьеры." }
    ];

    const map = L.map('map-canvas');

    L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
        maxZoom: 18,
        attribution: '&copy; Авторы <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>'
    }).addTo(map);

    const markers = places.map(p =>
        L.marker(p.coords)
            .addTo(map)
            .bindPopup('<h4>' + p.name + '</h4><p>' + p.text + '</p>')
    );

    // Подбираем масштаб так, чтобы были видны все метки
    map.fitBounds(L.latLngBounds(places.map(p => p.coords)).pad(0.15));

    // Кнопка в карточке: приближает карту к нужной метке и открывает подпись
    document.querySelectorAll('[data-place]').forEach(link => {
        link.addEventListener('click', () => {
            const i = Number(link.dataset.place);
            map.flyTo(places[i].coords, 13);
            markers[i].openPopup();
        });
    });
</script>

</body>
</html>
