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
    <!-- Серебряный родник -->
    <article class="card" data-dialog="#dlg-srebrnyy-rodnik">
        <img src="https://via.placeholder.com/600x400/EEF0F2/AAAAAA/?text=%D0%A1%D0%B5%D1%80%D0%B5%D0%B1%D1%80%D1%8F%D0%BD%D1%8B%D0%B9+%D1%80%D0%BE%D0%B4%D0%BD%D0%B8%D0%BA" alt="Серебряный родник">
        <div class="card-content">
            <span class="tag">Природа</span>
            <h3>Серебряный родник</h3>
            <p>Святой источник с кристально чистой водой, богатый серебром.</p>
            <div class="card-buttons">
                <a href="#" class="btn" onclick="openDlg('dlg-srebrnyy-rodnik')">Подробнее</a>
                <a href="#" class="btn outline" target="_blank">Маршрут</a>
            </div>
        </div>
    </article>

    <!-- Село Лох -->
    <article class="card" data-dialog="#dlg-lokh">
        <img src="https://via.placeholder.com/600x400/EEF0F2/AAAAAA/?text=%D0%A1%D0%B5%D0%BB%D0%BE+%D0%9B%D0%BE%D1%85" alt="Село Лох">
        <div class="card-content">
            <span class="tag">История</span>
            <h3>Село Лох</h3>
            <p>Старинное село с деревянной мельницей и легендой о Кудеяре.</p>
            <div class="card-buttons">
                <a href="#" class="btn" onclick="openDlg('dlg-lokh')">Подробнее</a>
                <a href="#" class="btn outline" target="_blank">Фотогалерея</a>
            </div>
        </div>
    </article>

    <!-- Дунина гора -->
    <article class="card" data-dialog="#dlg-duinina-gora">
        <img src="https://via.placeholder.com/600x400/EEF0F2/AAAAAA/?text=%D0%94%D1%83%D0%BD%D0%B8%D0%BD%D0%B0+%D0%B3%D0%BE%D1%80%D0%B0" alt="Дунина гора">
        <div class="card-content">
            <span class="tag">Геология</span>
            <h3>Дунина гора</h3>
            <p>Уникальный геологический останец у реки Медведицы.</p>
            <div class="card-buttons">
                <a href="#" class="btn" onclick="openDlg('dlg-duinina-gora')">Подробнее</a>
                <a href="#" class="btn outline" target="_blank">Как добраться</a>
            </div>
        </div>
    </article>

    <!-- Утёс Степана Разина -->
    <article class="card" data-dialog="#dlg-stepan-razin">
        <img src="https://via.placeholder.com/600x400/EEF0F2/AAAAAA/?text=%D0%A3%D1%82%D1%91%D1%81+%D0%A1%D1%82%D0%B5%D0%BF%D0%B0%D0%BD%D0%B0+%D0%A0%D0%B0%D0%B7%D0%B8%D0%BD%D0%B0" alt="Утёс Степана Разина">
        <div class="card-content">
            <span class="tag">Легенды</span>
            <h3>Утёс Степана Разина</h3>
            <p>Археологический памятник с видом на Волгу и легендарными историями.</p>
            <div class="card-buttons">
                <a href="#" class="btn" onclick="openDlg('dlg-stepan-razin')">Подробнее</a>
                <a href="#" class="btn outline" target="_blank">Панорама</a>
            </div>
        </div>
    </article>
</section>

<!-- Модальные окна -->

<!-- Серебряный родник -->
<dialog id="dlg-srebrnyy-rodnik" class="modal">
    <button class="dlg-close" aria-label="Закрыть диалог" title="Закрыть диалог">×</button>
    <div class="dlg-scroll">
        <img class="dlg-img" src="https://via.placeholder.com/1200x260/EEF0F2/AAAAAA/?text=%D0%A1%D0%B5%D1%80%D0%B5%D0%B1%D1%80%D1%8F%D0%BD%D1%8B%D0%B9+%D1%80%D0%BE%D0%B4%D0%BD%D0%B8%D0%BA" alt="Серебряный родник">
        <div class="dlg-body">
            <h2>Серебряный родник</h2>
            <p><strong>Локализация:</strong> Саратовская область, Хвалынский район.</p>
            <p>Один из самых известных святых источников региона. Вода здесь отличается высоким содержанием серебра и других микроэлементов, благодаря чему считается целебной. Родник облагорожен купелью и часовней. Температура воды круглый год составляет около +7 °C.</p>
            <ul>
                <li>Вода пригодна для питья после кипячения;</li>
                <li>Рядом есть парковка и зона отдыха;</li>
                <li>Родник окружён живописным лесопарком.</li>
            </ul>
        </div>
    </div>
</dialog>

<!-- Село Лох -->
<dialog id="dlg-lokh" class="modal">
    <button class="dlg-close" aria-label="Закрыть диалог" title="Закрыть диалог">×</button>
    <div class="dlg-scroll">
        <img class="dlg-img" src="https://via.placeholder.com/1200x260/EEF0F2/AAAAAA/?text=%D0%A1%D0%B5%D0%BB%D0%BE+%D0%9B%D0%BE%D1%85" alt="Село Лох">
        <div class="dlg-body">
            <h2>Село Лох</h2>
            <p><strong>Локализация:</strong> Новобурасский район, Саратовская область.</p>
            <p>Основано в конце XVII века как сторожевая слобода. Название происходит от слова «лог» (лощина). Здесь сохранилась уникальная атмосфера старой России.</p>
            <p><b>Главные объекты:</b></p>
            <ul>
                <li><b>Водяная мельница (XIX век)</b>: трёхэтажное деревянное здание без единого гвоздя. Сейчас музей под открытым небом.</li>
                <li><b>Симов родник</b>: железистый источник с желтоватой водой, расположенный рядом с рекой Соколкой. По легенде, хранил ключ от сокровищ разбойника Кудеяра.</li>
                <li><b>Кудеярова пещера</b>: антропогенная пещера в горе, связанная с преданиями о знаменитом разбойнике.</li>
                <li><b>Церковь Архангела Михаила</b>: восстановленный храм с историческими фресками.</li>
            </ul>
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
            <p><strong>Локализация:</strong> Балашовский район, Саратовская область.</p>
            <p>Это уникальный меловый останец, возвышающийся над долиной реки Медведицы. Гора сложена известняками и песчаниками, которые формируют причудливые скалы и гроты.</p>
            <p>Здесь расположен ботанический заказник с редкими видами растений. С вершины горы открывается панорамный вид на степи и реку. Высота останца — до 80 м над уровнем реки.</p>
        </div>
    </div>
</dialog>

<!-- Утёс Степана Разина -->
<dialog id="dlg-stepan-razin" class="modal">
    <button class="dlg-close" aria-label="Закрыть диалог" title="Закрыть диалог">×</button>
    <div class="dlg-scroll">
        <img class="dlg-img" src="https://via.placeholder.com/1200x260/EEF0F2/AAAAAA/?text=%D0%A3%D1%82%D1%91%D1%81+%D0%A1%D1%82%D0%B5%D0%BF%D0%B0%D0%BD%D0%B0+%D0%A0%D0%B0%D0%B7%D0%B8%D0%BD%D0%B0" alt="Утёс Степана Разина">
        <div class="dlg-body">
            <h2>Утёс Степана Разина</h2>
            <p><strong>Локализация:</strong> Белогорское, Саратовская область.</p>
            <p>Высокий (около 35–40 м) останец на берегу Волги, официально признанный археологическим памятником природы. Это одно из самых красивых мест в регионе.</p>
            <p>Со скал утёса открываются захватывающие виды на бескрайнюю Волгу шириной более 7 км. Место овеяно множеством легенд: о спрятанном кладе, призраках и даже гробнице Марины Мнишек. Рядом расположена Дурман-гора, известная своими оптическими иллюзиями.</p>
        </div>
    </div>
</dialog>

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

</body>
</html>
