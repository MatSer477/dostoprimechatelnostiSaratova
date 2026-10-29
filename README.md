<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Достопримечательности Саратова</title>
    <style>
        :root {
            --primary-color: #005a9c; /* Цвет флага Саратовской области */
            --secondary-color: #d4af37; /* Золотой */
            --text-color: #333;
            --bg-light: #f4f4f4;
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
            max-width: 800px;
            height: 400px;
            background: #e0e0e0;
            margin: 0 auto;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #777;
            border-radius: 8px;
            font-size: 1.2rem;
            border: 2px dashed #ccc;
        }

        footer {
            background: #333;
            color: white;
            text-align: center;
            padding: 2rem;
            margin-top: 3rem;
        }

        @media (max-width: 768px) {
            header h1 {
                font-size: 2rem;
            }
            .nav-container {
                flex-direction: column;
                gap: 0.5rem;
            }
            .attractions-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>

<header>
    <h1>Путешествие по Саратову</h1>
    <p>Главные достопримечательности города на Волге</p>
</header>

<nav>
    <div class="nav-container">
        <a href="#nature">Природа</a>
        <a href="#history">История</a>
        <a href="#culture">Культура</a>
        <a href="#architecture">Архитектура</a>
    </div>
</nav>

<main>
    <section class="intro">
        <p>Саратов — один из старейших городов на Волге, основанный в 1590 году. Это город с богатейшей историей, где купеческая архитектура соседствует с монументами космической эры. Здесь учился первый космонавт Юрий Гагарин, а великая русская река задает ритм жизни города. Мы собрали для вас самые интересные места, которые стоит посетить в 2025 году.</p>
    </section>

    <section id="nature">
        <h2 style="text-align: center; margin-bottom: 2rem; color: var(--primary-color);">Природные красоты</h2>
        <div class="attractions-grid">
            <div class="card">
                <img src="https://via.placeholder.com/400x200/4CAF50/FFFFFF?text=Соколовая+гора" alt="Соколовая гора">
                <div class="card-content">
                    <h3>Соколовая гора</h3>
                    <p>Высшая точка города, где расположен мемориальный комплекс «Журавли» и Парк Победы. С вершины открывается панорамный вид на Волгу и автодорожный мост.</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
            <div class="card">
                <img src="https://via.placeholder.com/400x200/2196F3/FFFFFF?text=Набережная" alt="Набережная Космонавтов">
                <div class="card-content">
                    <h3>Набережная Космонавтов</h3>
                    <p>Главная прогулочная зона города протяженностью около 1.5 км. Отсюда открывается лучший вид на знаменитый Саратовский мост.</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
            <div class="card">
                <img src="https://via.placeholder.com/400x200/FF9800/FFFFFF?text=Лимонарий" alt="Саратовский лимонарий">
                <div class="card-content">
                    <h3>Саратовский лимонарий</h3>
                    <p>Уникальная теплица в степной зоне, где круглый год плодоносят цитрусовые и цветут экзотические растения тропиков.</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
        </div>
    </section>

    <section id="history" style="margin-top: 3rem;">
        <h2 style="text-align: center; margin-bottom: 2rem; color: var(--primary-color);">История и память</h2>
        <div class="attractions-grid">
            <div class="card">
                <img src="https://via.placeholder.com/400x200/9C27B0/FFFFFF?text=Парк+Победы" alt="Парк Победы">
                <div class="card-content">
                    <h3>Парк Победы</h3>
                    <p>Мемориальный комплекс на Соколовой горе с экспозицией военной техники под открытым небом и Вечным огнем.</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
            <div class="card">
                <img src="https://via.placeholder.com/400x200/E91E63/FFFFFF?text=Гагаринское+поле" alt="Гагаринское поле">
                <div class="card-content">
                    <h3>Гагаринское поле</h3>
                    <p>Место приземления первого космонавта Юрия Гагарина. Здесь установлен мемориальный комплекс в честь этого события.</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
            <div class="card">
                <img src="https://via.placeholder.com/400x200/607D8B/FFFFFF?text=Музей+Радищева" alt="Музей Радищева">
                <div class="card-content">
                    <h3>Художественный музей им. Радищева</h3>
                    <p>Первый общедоступный художественный музей в России, открытый в 1885 году. Хранит коллекции русского и зарубежного искусства.</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
        </div>
    </section>

    <section id="culture" style="margin-top: 3rem;">
        <h2 style="text-align: center; margin-bottom: 2rem; color: var(--primary-color);">Культура и искусство</h2>
        <div class="attractions-grid">
            <div class="card">
                <img src="https://via.placeholder.com/400x200/3F51B5/FFFFFF?text=Консерватория" alt="Консерватория">
                <div class="card-content">
                    <h3>Саратовская консерватория</h3>
                    <p>Один из старейших музыкальных вузов России. Здание в готическом стиле — один из главных символов города.</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
            <div class="card">
                <img src="https://via.placeholder.com/400x200/009688/FFFFFF?text=Театр+Оперы" alt="Театр оперы">
                <div class="card-content">
                    <h3>Театр оперы и балета</h3>
                    <p>Репертуар театра включает классические оперы, балеты и современные постановки. Расположен на Театральной площади.</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
            <div class="card">
                <img src="https://via.placeholder.com/400x200/795548/FFFFFF?text=Проспект+Кирова" alt="Проспект Кирова">
                <div class="card-content">
                    <h3>Проспект им. Кирова</h3>
                    <p>Главная пешеходная улица города, саратовский «Арбат». Здесь находится знаменитая скульптура «Саратовская гармошка».</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
        </div>
    </section>

    <section id="architecture" style="margin-top: 3rem;">
        <h2 style="text-align: center; margin-bottom: 2rem; color: var(--primary-color);">Архитектура</h2>
        <div class="attractions-grid">
            <div class="card">
                <img src="https://via.placeholder.com/400x200/FF5722/FFFFFF?text=Свято-Троицкий+собор" alt="Свято-Троицкий собор">
                <div class="card-content">
                    <h3>Свято-Троицкий собор</h3>
                    <p>Древнейший храм города (конец XVII века), памятник московского барокко. Главная духовная святыня Саратова.</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
            <div class="card">
                <img src="https://via.placeholder.com/400x200/673AB7/FFFFFF?text=Мост" alt="Саратовский мост">
                <div class="card-content">
                    <h3>Саратовский мост</h3>
                    <p>Арочный мост через Волгу, открытый в 1965 году. На момент постройки был самым длинным в Европе (2825 метров).</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
            <div class="card">
                <img src="https://via.placeholder.com/400x200/00BCD4/FFFFFF?text=Национальная+деревня" alt="Национальная деревня">
                <div class="card-content">
                    <h3>Национальная деревня</h3>
                    <p>Этнографический комплекс под открытым небом на Соколовой горе, представляющий быт народов Поволжья.</p>
                    <a href="#">Подробнее</a>
                </div>
            </div>
        </div>
    </section>

    <section class="map-section">
        <h2>Достопримечательности на карте</h2>
        <div class="placeholder-map">
            [Здесь будет интерактивная карта Саратова с метками]
        </div>
    </section>
</main>

<footer>
    <p>&copy; 2025 Путеводитель по Саратову. Все права защищены.</p>
    <p>Информация собрана на основе открытых данных о городе.</p>
</footer>

</body>
</html>
