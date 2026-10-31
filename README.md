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
