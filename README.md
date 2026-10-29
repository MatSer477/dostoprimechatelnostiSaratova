<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Достопримечательности Санкт-Петербурга</title>
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
    <h1>Санкт-Петербург</h1>
    <p>Главные достопримечательности северной столицы</p>
</header>

<nav>
    <div class="nav-container">
        <a href="#attractions">Достопримечательности</a>
        <a href="#map">Карта</a>
    </div>
</nav>

<main>
    <p class="intro">
        Санкт-Петербург — город дворцов, мостов и белых ночей. Ниже собраны места,
        которые стоит увидеть в первую очередь.
    </p>

    <section id="attractions" class="attractions-grid">

        <div class="card">
            <img src="images/hermitage.jpg" alt="Эрмитаж" loading="lazy">
            <div class="card-content">
                <h3>Эрмитаж</h3>
                <p>Один из крупнейших музеев мира с коллекцией в миллионы экспонатов.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

        <div class="card">
            <img src="images/savior-on-blood.jpg" alt="Спас на Крови" loading="lazy">
            <div class="card-content">
                <h3>Спас на Крови</h3>
                <p>Храм в русском стиле, украшенный уникальной мозаикой.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

        <div class="card">
            <img src="images/peterhof.jpg" alt="Петергоф" loading="lazy">
            <div class="card-content">
                <h3>Петергоф</h3>
                <p>Парадная императорская резиденция с каскадами фонтанов.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

        <div class="card">
            <img src="images/isaac-cathedral.jpg" alt="Исаакиевский собор" loading="lazy">
            <div class="card-content">
                <h3>Исаакиевский собор</h3>
                <p>Величественный собор с колоннадой, откуда открывается вид на город.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

        <div class="card">
            <img src="images/bronze-horseman.jpg" alt="Медный всадник" loading="lazy">
            <div class="card-content">
                <h3>Медный всадник</h3>
                <p>Памятник Петру I — один из главных символов города.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

        <div class="card">
            <img src="images/palace-bridge.jpg" alt="Дворцовый мост" loading="lazy">
            <div class="card-content">
                <h3>Дворцовый мост</h3>
                <p>Разводной мост через Неву, главное ночное зрелище города.</p>
                <a href="#">Подробнее</a>
            </div>
        </div>

    </section>

    <section id="map" class="map-section">
        <h2>Карта</h2>
        <iframe class="placeholder-map"
            src="https://www.openstreetmap.org/export/embed.html?bbox=30.20,59.88,30.45,60.00&layer=mapnik"
            loading="lazy"></iframe>
    </section>
</main>

<footer>
    <p>&copy; 2026 Путеводитель по Санкт-Петербургу</p>
</footer>

</body>
</html>
