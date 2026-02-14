<html lang="ru">
<head>

<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

<div id="sideNav" class="side-nav hidden">
    <div id="navToggle" class="nav-toggle" onclick="toggleNav(event)">‹</div>
    </div>


    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>RC Slots Full Database</title>
<link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>💎</text></svg>">

<style>
    /* 1. ПЕРЕМЕННЫЕ И ТЕМЫ */
    :root {
        --bg-page: #e3f2fd;
        --table-bg: #ffffff;
        --text-main: #0d47a1;
        --text-info: #546e7a;
        --accent-blue: #0288d1;
        --story-header: #bbdefb;
        --btn-copy: #03a9f4;
        --border-table: #e1f5fe;
        --code-bg: #f5faff;
        --highlight: #ffeb3b;
        --footer-color: #94a3b8;
        --search-icon: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 24 24' stroke='%230288d1' stroke-width='2.5'%3E%3Cpath stroke-linecap='round' stroke-linejoin='round' d='M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z' /%3E%3C/svg%3E");
    }

    body.dark-mode {
        --bg-page: #0f172a;
        --table-bg: #1e293b;
        --text-main: #f1f5f9;
        --text-info: #94a3b8;
        --accent-blue: #38bdf8;
        --story-header: #334155;
        --btn-copy: #0ea5e9;
        --border-table: #334155;
        --code-bg: #0f172a;
        --highlight: #facc15;
        --footer-color: #64748b;
        --search-icon: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 24 24' stroke='%2338bdf8' stroke-width='2.5'%3E%3Cpath stroke-linecap='round' stroke-linejoin='round' d='M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z' /%3E%3C/svg%3E");
    }

    /* 2. БАЗОВЫЕ НАСТРОЙКИ */
    body { 
        font-family: 'Segoe UI', system-ui, -apple-system, sans-serif; 
        background-color: var(--bg-page);
        color: var(--text-main);
        margin: 0; padding: 15px 10px;
        display: flex; flex-direction: column; align-items: center;
        transition: background-color 0.3s;
        overflow-x: hidden;
    }

    /* 3. ДИЗАЙН ПОИСКА (ФИНАЛ) */
    .search-wrapper { 
        width: 100%; 
        max-width: 500px; 
        margin: 0 auto 20px; 
        position: relative; 
        display: flex;
        align-items: center;
    }
    
    #searchInput { 
        width: 100%; 
        padding: 14px 45px 14px 46px; 
        border: 2px solid transparent; 
        border-radius: 14px; 
        font-size: 16px; 
        background-color: var(--table-bg); 
        color: var(--text-main);
        box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
        outline: none; 
        box-sizing: border-box; 
        transition: all 0.3s;
    }
    
    #searchInput:focus { 
        border-color: var(--accent-blue);
        box-shadow: 0 4px 25px rgba(0, 0, 0, 0.15);
    }

    .search-wrapper::before {
        content: ""; position: absolute; left: 16px; top: 50%;
        transform: translateY(-50%); width: 22px; height: 22px;
        background: var(--search-icon) no-repeat center;
        background-size: contain;
        z-index: 2; pointer-events: none;
    }

    #clearSearch {
        position: absolute; right: 14px; top: 50%;
        transform: translateY(-50%); cursor: pointer;
        font-size: 22px; color: var(--text-info);
        display: none; z-index: 3; padding: 5px;
        line-height: 1; user-select: none; transition: color 0.2s;
    }

    #clearSearch:hover { color: var(--accent-blue); }

    #searchInput:not(:placeholder-shown) + #clearSearch { display: block; }

    /* 4. ТАБЛИЦА (ФИКСИРОВАННАЯ ГЕОМЕТРИЯ) */
    .table-container { 
        width: 100%; max-width: 500px; 
        background-color: var(--table-bg) !important; 
        border-radius: 16px; overflow: hidden; 
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        border: 1px solid var(--border-table);
    }

    table { width: 100%; border-collapse: collapse; table-layout: fixed; background-color: transparent; }

    th { 
        background-color: var(--code-bg); color: var(--accent-blue); 
        padding: 12px 5px; font-size: 0.8em; text-transform: uppercase;
        border-bottom: 2px solid var(--border-table);
    }

    td { 
        padding: 10px 5px !important; 
        border-bottom: 1px solid var(--border-table); 
        color: var(--text-main) !important;
        background-color: var(--table-bg) !important;
        text-align: center; vertical-align: middle;
        /* Фикс высоты, чтобы таблица не прыгала */
        height: 75px !important; 
        line-height: 1.2 !important;
        font-size: 14px !important;
        box-sizing: border-box !important;
    }

    th:nth-child(1), td:nth-child(1) { width: 25%; font-weight: 700; }
    th:nth-child(2), td:nth-child(2) { width: 50%; }
    th:nth-child(3), td:nth-child(3) { width: 25%; font-size: 11px; color: var(--text-info); }

    /* 5. ПОДСВЕТКА (БЕЗ РАСШИРЕНИЯ ТЕКСТА) */
    mark { 
        background-color: var(--highlight); 
        color: #000; 
        border-radius: 2px;
        padding: 0 !important;
        margin: 0 !important;
        font-weight: inherit !important;
        font-size: inherit !important;
    }

    /* 6. ЭЛЕМЕНТЫ СТРОК */
    .story-row, .story-row td { 
        background-color: var(--story-header) !important; 
        color: var(--text-main) !important; font-weight: 800; text-align: left !important;
        padding: 12px 16px !important; border-bottom: none; height: 45px !important;
    }

    .code-text { 
        font-family: 'Courier New', monospace; color: var(--accent-blue); 
        background-color: var(--code-bg); padding: 5px; border-radius: 6px; 
        border: 1px solid var(--border-table); font-size: 11px;
        word-break: break-all; display: block; margin-bottom: 4px;
        line-height: 1.1;
    }
    
    .copy-btn {
        background-color: var(--btn-copy); color: white; border: none; 
        padding: 6px 0; border-radius: 8px; cursor: pointer; 
        font-size: 10px; font-weight: 600; width: 100%; transition: 0.2s;
    }
    .copy-btn.copied { background-color: #10b981; }

    /* 7. КНОПКИ УПРАВЛЕНИЯ */
    .theme-toggle {
        position: fixed; top: 15px; right: 15px;
        background: var(--table-bg); border: 2px solid var(--accent-blue);
        color: var(--accent-blue); border-radius: 50%;
        width: 42px; height: 42px; cursor: pointer; z-index: 1000;
        display: flex; align-items: center; justify-content: center; font-size: 20px;
    }

    .tg-minimal-btn {
        display: inline-block; padding: 12px 28px; background: var(--table-bg);
        color: var(--text-main) !important; text-decoration: none; font-weight: 700;
        border-radius: 12px; border: 2px solid var(--accent-blue); font-size: 14px;
        margin-bottom: 20px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);
    }

    #backToTop {
        display: none; position: fixed; bottom: 25px; right: 25px;
        background: var(--accent-blue); color: white; border: none;
        width: 45px; height: 45px; border-radius: 50%; cursor: pointer; z-index: 99;
        font-size: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);
    }

    .footer-text { margin-top: 40px; margin-bottom: 20px; font-size: 12px; color: var(--footer-color); }
    
/* Основной контейнер панели */
.side-nav {
    position: fixed;
    right: 0; /* Прижата к самому краю */
    top: 50%;
    transform: translateY(-50%);
    display: flex;
    flex-direction: column;
    gap: 4px;
    z-index: 1000;
    background: rgba(2, 136, 209, 0.15);
    backdrop-filter: blur(10px);
    padding: 15px 5px;
    border-radius: 15px 0 0 15px; /* Скругление только слева */
    border: 1px solid rgba(2, 136, 209, 0.2);
    transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1); /* Плавный выезд */
}

/* Состояние "Спрятана" */
.side-nav.hidden {
    transform: translateY(-50%) translateX(100%); /* Уезжает вправо */
}

/* Стрелка-язычок */
.nav-toggle {
    position: absolute;
    left: -30px; /* Выступает за пределы панели */
    top: 50%;
    transform: translateY(-50%);
    width: 30px;
    height: 60px;
    background: rgba(2, 136, 209, 0.8);
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    border-radius: 15px 0 0 15px;
    font-size: 20px;
    font-weight: bold;
    transition: 0.3s;
}

.side-nav.hidden .nav-toggle {
    left: -35px; /* Чуть сильнее выпирает, когда скрыта */
}

/* Меняем направление стрелки */
.nav-toggle::after { content: '›'; }
.side-nav.hidden .nav-toggle::after { content: '‹'; }

/* Буквы внутри */
.side-nav a {
    text-decoration: none;
    color: #0288d1;
    font-weight: 900;
    font-size: 16px;
    width: 35px;
    height: 35px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 8px;
    background: rgba(255, 255, 255, 0.8);
    margin-bottom: 2px;
}


</style>

</head>
<body id="body">

<button class="theme-toggle" onclick="toggleTheme()" id="themeBtn">🌙</button>
<button onclick="topFunction()" id="backToTop">↑</button>

<div class="header-box">
    <h2>ПОЛНАЯ БАЗА СЛОТОВ MODR.💎</h2>
</div>

<div class="search-wrapper">
    <input type="text" id="searchInput" oninput="filterData()" placeholder="Поиск героя или истории...">
    <div id="clearSearch" onclick="clearInput()">×</div>
</div>




<div class="tg-wrapper">
    <a href="https://t.me/modr_slots_bot" target="_blank" class="tg-minimal-btn">Отправить слоты 🩵</a>
</div>

<div class="table-container">
    <table id="mainTable">
        <thead>
            <tr>
                <th>Персонаж</th>
                <th>Код Слота</th>
                <th>Инфо</th>
            </tr>
        </thead>
        <tbody>
                    <tr class="story-row"><td colspan="3">W: Ловчая Времени</td></tr>
<tr>
<td>Оникс</td><td><span class="code-text">024d696ab878ff9cd37faa17ec1694b9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">солнце, выс. статус, сила присутствия, без финала</td></tr>
<tr>
<td>Шен</td><td><span class="code-text">eb50c06aca17d42410b89351df99c25b</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">луна, выс. статус, сила присутствия, с финалом</td></tr>
<tr>
<td>Льюсен</td><td><span class="code-text">91a15cc20674e465f65b0d2b8171c129</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">луна, выс. статус, сила присутствия, с финалом</td></tr>
<tr>
<td>Ренато</td><td><span class="code-text">e66581e63fde0a21d95f75ecc213a107</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">солнце, выс. статус, сила присутствия, без финала</td></tr>
<tr>
<td>Веспер</td><td><span class="code-text">eff25e263104797a0fb1796ff4771f4e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">луна, выс. статус, сила присутствия, без финала</td></tr>

<tr class="story-row"><td colspan="3">Te amo 1 том</td></tr>
<tr><td>Майкл</td><td><span class="code-text">d82650d204cd6817204797033fca7e00</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">восприятие, с финалом</td></tr>
<tr><td>Томас</td><td><span class="code-text">13a2ca74e39b641db42db6369d6e8725</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение, с финалом</td></tr>
<tr><td>Ли</td><td><span class="code-text">f7db94fbabcd3b41b2af6d8ba20628f1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">чувства, с финалом</td></tr>
<tr><td>Жанна</td><td><span class="code-text">8cacc44c76e75bf310a487b7f654a6ea</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">чувства, с финалом</td></tr>
<tr class="story-row"><td colspan="3">Te amo 2 том</td></tr>
<tr><td>Мэт</td><td><span class="code-text">cf48199c00acd80a0a96ad72fe8544dc</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение</td></tr>

<tr class="story-row"><td colspan="3">7Б</td></tr>
<tr><td>Грант</td><td><span class="code-text">2437db5000468bea11082a9c22c91297</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">капитализм, милашка</td></tr>
<tr><td>Саймон</td><td><span class="code-text">31b9101b1eda80857c3e10d178cdce09</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">капитализм, милашка</td></tr>
<tr><td>Джаспер</td><td><span class="code-text">a51a6814eecd12487a2b65bb67563914</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">капитализм, милашка</td></tr>
<tr><td>Тристан</td><td><span class="code-text">2c52220dd1a790c67fe7a3e1cb0a6035</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">антикапитализм</td></tr>
<tr class="story-row"><td colspan="3">Авверис</td></tr>
<tr><td>Аши</td><td><span class="code-text">365a71d10df45dbc2368135630db129c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">аномалия, система</td></tr>

<tr class="story-row"><td colspan="3">Арканум</td></tr>
<tr><td>Лиам</td><td><span class="code-text">c050f3a89e9130f3b7eeb90a8f63c8aa</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">2 сезон 7 серия, жрица, искупление</td></tr>
<tr><td>Деймон</td><td><span class="code-text">b7f66b3ace303b21f5111101662041c6</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жрица, искупление, все арканы, финал</td></tr>
<tr><td>Роб</td><td><span class="code-text">f411139513014a04593d49a2fbeb6f04</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жрица, искупление, все арканы, финал</td></tr>

<tr class="story-row"><td colspan="3">Бездушная</td></tr>
<tr><td>Винсент</td><td><span class="code-text">64c35738c74fa1c47a6bb77c8d037694</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">путь баланса</td></tr>
<tr><td>Уолтер</td><td><span class="code-text">ab6f6189c4de352bc47d927c29aa56b9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">путь баланса</td></tr>
<tr><td>Мент (Эллиот)</td><td><span class="code-text">d1f1d2190a7a331a0bdaa0554c94b</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">2 сезон, 5 серия, путь баланса</td></tr>
<tr><td>Трексио</td><td><span class="code-text">d451d86fcd41910efba62d216d323f07</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">путь баланса</td></tr>

<tr class="story-row"><td colspan="3">Дракула: История любви</td></tr>
<tr><td>Ноэ</td><td><span class="code-text">5544e1ef9352878265d67cb8b4f1035d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">конец 3го сезона, баланс</td></tr>
<tr><td>Влад</td><td><span class="code-text">5ef89c04eb5fe0084c7bc0c98ffe5b23</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">начало 3го сезона, баланс</td></tr>
<tr><td>Влад(2)</td><td><span class="code-text">322cad551b404d2148fa62d0ef1dd1b3</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>
<tr><td>Лео</td><td><span class="code-text">3b443ca263066aaa1caef0f9ef433b93</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс, финал по человеку</td></tr>

<tr class="story-row"><td colspan="3">И поглотит нас морок</td></tr>
<tr><td>Драган</td><td><span class="code-text">2cd483f99137fd6da27f616d2b0b832a</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">высокая связь, явь, сострадание</td></tr>
<tr><td>Волот</td><td><span class="code-text">482f96035041ffa5ba2a86ba4c6c6d7d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">высокая связь, явь, сострадание</td></tr>
<tr><td>Озар</td><td><span class="code-text">5b2ae942e42b7f7e3dfa307a92da6412</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">высокая связь, явь, сострадание</td></tr>
<tr><td>Сирин</td><td><span class="code-text">9e5ae173528a15c6a70633431d5b73e0</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">высокая связь, явь, сострадание</td></tr>
<tr><td>Новак</td><td><span class="code-text">17c10046c34b928a54e042c492114ad2</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">высокая связь, морок, сострадание</td></tr>

<tr class="story-row"><td colspan="3">Идеал</td></tr>
<tr><td>Мона</td><td><span class="code-text">5533f4140c8373e74845b76002e57eab</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">разум, без финала</td></tr>
<tr><td>Тьяго</td><td><span class="code-text">3314682cb550834df00991a51abb4e1c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">разум</td></tr>

<tr class="story-row"><td colspan="3">Кали: Пламя Сансары</td></tr>
<tr><td>Доран (1)</td><td><span class="code-text">0c4281618c21644c1f471caa6b6151ab</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие, гордость</td></tr>
<tr><td>Доран (2)</td><td><span class="code-text">139c6dcd24978160016ef6d842081063</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">свобода, гордость</td></tr>
<tr><td>Кристиан</td><td><span class="code-text">fc0df0d7263064c4e7fdf459954876bf</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие, гордость, конец 2го сезона</td></tr>
<tr><td>Рам</td><td><span class="code-text">ab3f19bcfa164fc1b641231b631540f8</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие, гордость</td></tr>
<tr><td>Сара</td><td><span class="code-text">eb7401a112bb8bffd554c25121a24ab6</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие, гордость, 2 сезон 7серия</td></tr>
<tr><td>Камал</td><td><span class="code-text">f162bdce98c6e34bf9b28d9b3502dfe8</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие, гордость</td></tr>

<tr class="story-row"><td colspan="3">Кали: Зов Тьмы</td></tr>
<tr><td>Рейтан</td><td><span class="code-text">6d3b4356a3b5816ccbc5f5c95715a6d9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">3 сезон, 5 серия, гнев</td></tr>
<tr><td>Килиан</td><td><span class="code-text">2bfa38fa2b11a412b15ae5e3f488ac58</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Гнев, концовка</td></tr>
<tr><td>Амрит</td><td><span class="code-text">1520ec77e59ed379751d2f150f50a736</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">лояльность, милость</td></tr>

<tr class="story-row"><td colspan="3">Код синий</td></tr>
<tr><td>Нахом</td><td><span class="code-text">199362602aebc9aee32696a0c47768e6</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жгг, сочувствие</td></tr>
<tr><td>Тобиас</td><td><span class="code-text">5706512d2f48a49cbec573ce5496ed38</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жгг, сочувствие</td></tr>
<tr><td>Эстебан</td><td><span class="code-text">3afeef4fe5f6874b1e5fdba2cd1ce59d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жгг, сочувствие</td></tr>

<tr class="story-row"><td colspan="3">Легенда Ивы</td></tr>
<tr><td>Кадзу</td><td><span class="code-text">974e6428cd00bcbc1f3737c02b1d1024</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Тимон, новый код! страсть, янтарная лиса</td></tr>

<tr class="story-row"><td colspan="3">Песнь о Красном Ниле</td></tr>
<tr><td>Ливий</td><td><span class="code-text">d13d0007af972568f876507cf9af10a2</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность, некромантия</td></tr>
<tr><td>Сет</td><td><span class="code-text">a0b719bc394314786f64253a8539cb30</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хитрость, некромантия</td></tr>
<tr><td>Амен</td><td><span class="code-text">6cd61d7df682189d9911cadaf85c5482</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность, некромантия</td></tr>
<tr><td>Анубис</td><td><span class="code-text">07642c99bee9f281d329174668b6fcf3</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность, онейромантия</td></tr>

<tr class="story-row"><td colspan="3">Пси Ψ</td></tr>
<tr><td>Иво</td><td><span class="code-text">2cdd74cc1251b961aba59029430d775c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">импульс, вектор</td></tr>
<tr><td>Йонас</td><td><span class="code-text">9451e14bc97ecaca8f773b2113157c10</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">контроль, вектор</td></tr>
<tr><td>Кей</td><td><span class="code-text">0fb719ac9766de2af3d68623974e4d4c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">контроль, форма</td></tr>

<tr class="story-row"><td colspan="3">Покоряя Версаль</td></tr>
<tr><td>Александр</td><td><span class="code-text">5b96ea7a8de4ab46697bc1a7eaa56c1c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">расчёт</td></tr>

<tr class="story-row"><td colspan="3">Пришествие 3</td></tr>
<tr><td>Зейн</td><td><span class="code-text">a6799ef899b53f7b0961b48c70ef2878</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">догман, напор</td></tr>
<tr><td>Макс</td><td><span class="code-text">0dbbd6e90b90faf6c13220cf9b7c7cf5</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">отречение, напор</td></tr>
<tr><td>Ксандр</td><td><span class="code-text">420d05f34ce854f98ed46ee525e2a526</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">отречение, напор (возможны баги)</td></tr>
<tr><td>Октавиан</td><td><span class="code-text">a6be010fa0116965bbf359def68699f8</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">догман, коварство</td></tr>

<tr class="story-row"><td colspan="3">Пропавшие</td></tr>
<tr><td>Мадс</td><td><span class="code-text">2c783eaf342ad2d4991746bb5041d2ed</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение</td></tr>
<tr><td>Ясин</td><td><span class="code-text">1a5d43b5329e3d65a596c04f241bcbd4</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение</td></tr>
<tr><td>Куно</td><td><span class="code-text">7871a06e74362c9da48a0724eb5eb037</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение</td></tr>
<tr><td>Сафаа</td><td><span class="code-text">81af63c32d7f28afda433d45cff32ea7</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">восприятие</td></tr>

<tr class="story-row"><td colspan="3">Разбитое сердце Астреи</td></tr>
<tr><td>Микаэль</td><td><span class="code-text">c6b2d6fda60b786cbb61b7f6443163c2</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">вера</td></tr>
<tr><td>Рафаил</td><td><span class="code-text">d219c6d4627b72d67381773d4b866e5e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">вера</td></tr>
<tr><td>Кас</td><td><span class="code-text">4ab7ade6839cc30b6168df5b62f75349</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">вера</td></tr>
<tr><td>Давид</td><td><span class="code-text">ff367761332a352cb36e5e5a0bb1bcea</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">вера</td></tr>
<tr><td>Малек</td><td><span class="code-text">ea0602a00c8bedc52bb5aaaa54c4435f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">скептицизм</td></tr>

<tr class="story-row"><td colspan="3">Роза Пустыни</td></tr>
<tr><td>Адиль</td><td><span class="code-text">fe7933dfe668439263d6139f367c3601</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">мечтательность, баланс пустыни и дитя, без 3го сезона</td></tr>
<tr><td>Зейн</td><td><span class="code-text">a3c176918bd0734ad23e9e570c96f7fe</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">мечтательность, баланс пустыни и дитя города</td></tr>

<tr class="story-row"><td colspan="3">Сага о Грозах</td></tr>
<tr><td>Ша'арнез</td><td><span class="code-text">0c1e8e898fa04d809817115fb3d09cf9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Ворон, призыв</td></tr>
<tr><td>Велора</td><td><span class="code-text">af2c8064bd9b338eca5286db66a567ff</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">ворон, изменения, конец 1го сезона</td></tr>
<tr><td>Тай</td><td><span class="code-text">d41eb664fd102d5cf9df87d00ca88e80</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">ворон, изменения, середина 2го сезона</td></tr>
<tr><td>Гриаран</td><td><span class="code-text">5b90b322cb696c25c5d7250f05b6f380</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">ворон, изменения, середина 3го сезона</td></tr>

<tr class="story-row"><td colspan="3">Секрет Небес</td></tr>
<tr><td>одиночка</td><td><span class="code-text">4c9152d8dca82cf40e92d29105979f34</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">ангел</td></tr>
<tr><td>Люцифер</td><td><span class="code-text">35afb2332ef908a54d3bf3cd7f619d40</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">демон</td></tr>
<tr><td>Маль</td><td><span class="code-text">4dc308fcf83c68f1c040c7d9b35a0261</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">несущая равновесие</td></tr>

<tr class="story-row"><td colspan="3">Секрет Небес: Реквием</td></tr>
<tr><td>Дима</td><td><span class="code-text">27c666a4a26617b105b29ca465522beb</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Бог, милосердие, выс адаптация</td></tr>
<tr><td>Грег</td><td><span class="code-text">baba1f6920e63dbe595047ea4a64d5eb</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Бог, милосердие, выс адаптация</td></tr>
<tr><td>Ян</td><td><span class="code-text">fbc509aa35f9955b1939e8f398b7d37e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Бог, милосердие, выс адаптация</td></tr>
<tr><td>Каин</td><td><span class="code-text">ac6bb94dc93ff03670242dcf0790d53d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">бог, милосердие, выс адаптация</td></tr>
<tr><td>Каин+Авель</td><td><span class="code-text">8aa3af17bddb8304f8d06365fb038698</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">дьявол, жесткость, выс адаптация</td></tr>

<tr class="story-row"><td colspan="3">Секрет Небес 2</td></tr>
<tr><td>Голод</td><td><span class="code-text">b1af411532cdba680e5a35e18a39a4d7</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровность, Война мёртв</td></tr>
<tr><td>Люцифер</td><td><span class="code-text">5691325191392ca26f8098be0819b783</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Темпераментность, концовка, Война жив</td></tr>
<tr><td>Астарот (1)</td><td><span class="code-text">8dd4fbc94766a9ef4314e2f960388e6f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровность, Война мёртв</td></tr>
<tr><td>Астарот (2)</td><td><span class="code-text">1575dded56f6bcbf58cd5ab2b23e08d7</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровность, Война жив</td></tr>
<tr><td>Мальбонте</td><td><span class="code-text">bf5acee0a34afd508f6f10d96904bcd5</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">не несущая равновесие, хладнокров, Война жив</td></tr>
<tr><td>Война</td><td><span class="code-text">cb907d487948233617f4b61c2d5c985a</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровность</td></tr>

<tr class="story-row"><td colspan="3">Секрет небес 3</td></tr>
<tr><td>Война+Грег+Кас</td><td><span class="code-text">7a433600d30678e35c6cfde3d3c752e9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие, прокаченная тьма Шепфамалума</td></tr>
<tr><td>Люц+Грег+Кас</td><td><span class="code-text">d5acbc5eb7ee4173109afdbd7ab5a24c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие, прокачен. тьма Шепфамалума</td></tr>
<tr><td>Маль+Каин+Мика</td><td><span class="code-text">1f82e3e2cb055a7b87bf449e4f2b6d8e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие, прокачен. тьма Шепфамалума</td></tr>

<tr class="story-row"><td colspan="3">Сердце Треспии</td></tr>
<tr><td>Рейнхольд</td><td><span class="code-text">a5e2ba6722aa3fe934a4b14a0a0aafd1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рациональность</td></tr>

<tr class="story-row"><td colspan="3">Там, где любовь горит вечно</td></tr>
<tr><td>Граф/Мессир/Шеда</td><td><span class="code-text">05362d9356139f6d50ddbc29585f5cdc</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жизнелюбие, баланс</td></tr>

<tr class="story-row"><td colspan="3">Тени Сентфора</td></tr>
<tr><td>Вишня</td><td><span class="code-text">f50408871d7f1ca307939bcfc177aab0</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">осторожность</td></tr>
<tr><td>Майкл</td><td><span class="code-text">b1c0024ca68aa77be6c6586a28cad08f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">осторожность</td></tr>

<tr class="story-row"><td colspan="3">Теодора</td></tr>
<tr><td>Лоуренс+Дариус+Антонио</td><td><span class="code-text">ffe028bef20345275bf7db646331a4f7</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">романтик, выс, энергия</td></tr>
<tr><td>Фридрих+Джон</td><td><span class="code-text">3955bc8eecf8442602bc09d908c2ed9c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">начало 3го сезона, романтик</td></tr>
<tr><td>Лоу+Марсель+Антонио</td><td><span class="code-text">8d6778c11a2fd7ae9f21706d3e65eec8</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">романтик, выс энергия</td></tr>

<tr class="story-row"><td colspan="3">Цветок из огня Тиамат</td></tr>
<tr><td>Ниалл</td><td><span class="code-text">5dacddb30e3015a5475df5d6f6b3774c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">огонь</td></tr>

<tr class="story-row"><td colspan="3">Шифр Шекспира</td></tr>
<tr><td>Эдвард</td><td><span class="code-text">7ce633d7d01a54b4caa4557e1600fbcc</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">без греха + хс</td></tr>
<tr><td>Эдмунд</td><td><span class="code-text">df0f71ee75e866439ea95692d8c6729b</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">грех Реджины + хс</td></tr>
<tr><td>Хобелло</td><td><span class="code-text">a8504347c17547f2f47ca047dd3d927e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">без греха + хс</td></tr>
<tr><td>Ральф</td><td><span class="code-text">bb76420474a8f2c702610505ba99de5f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">без греха + хс</td></tr>

<tr class="story-row"><td colspan="3">Эдемов Сад</td></tr>
<tr><td>Одиночка</td><td><span class="code-text">1b196faa0f4649e8b3c98f50eace2b90</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">1 сезон, 8 серия на выборе ветки</td></tr>
<tr><td>Минхёк</td><td><span class="code-text">4f03e11a86304a1fd884dfb12c7d827d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Амбиции, выс популярность</td></tr>
<tr><td>Кас</td><td><span class="code-text">f1ad1c34f9ecdf9f19f731e409c0d5dd</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">амбиции, выс. популярность</td></tr>
<tr><td>Туен</td><td><span class="code-text">a530e07721873d7311e43577509d5056</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt"></td></tr>

<tr class="story-row"><td colspan="3">Я охочусь на тебя</td></tr>
<tr><td>Сэм</td><td><span class="code-text">ea9c827a062eb5c3bb6fff106c738d85</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">логика</td></tr>
<tr><td>Александр</td><td><span class="code-text">b0ecb26e5011f2eb4717d15b23d187fa</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">логика</td></tr>
<tr class="story-row"><td colspan="3">Я Охочусь на Тебя 2</td></tr>
<tr><td>Эзра</td><td><span class="code-text">9e61e9fd7a31c6a938a427b0c934f926</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">логика</td></tr>

<tr class="story-row"><td colspan="3">Ярость Титанов</td></tr>
<tr><td>Мёрфи</td><td><span class="code-text">a6e9c1b40abb0d1f7e7fda9f8d9cb026</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">божественность, влияние</td></tr>



        </tbody>
    </table>



</div>
<script>
// 1. ГЕНЕРАЦИЯ АЛФАВИТА (Создает кнопки справа)
function generateAlphabet() {
    const sideNav = document.getElementById('sideNav');
    if (!sideNav) return;
    
    const stories = document.querySelectorAll('.story-row');
    const letters = new Set();
    sideNav.innerHTML = ''; 

    stories.forEach(story => {
        const firstLetter = story.innerText.trim()[0].toUpperCase();
        if (firstLetter && !letters.has(firstLetter)) {
            letters.add(firstLetter);
            const link = document.createElement('a');
            link.href = "javascript:void(0)";
            link.innerText = firstLetter;
            link.onclick = () => {
                const offset = 20; // Отступ сверху
                const elementPosition = story.getBoundingClientRect().top + window.pageYOffset;
                window.scrollTo({ top: elementPosition - offset, behavior: 'smooth' });
                
                // Эффект вспышки при переходе
                story.style.transition = "background 0.5s";
                story.style.background = "rgba(255, 64, 129, 0.3)";
                setTimeout(() => story.style.background = "", 1000);
            };
            sideNav.appendChild(link);
        }
    });
}

// 2. ОСНОВНОЙ ПОИСК + ПАСХАЛКА
function filterData() {
    const inputField = document.getElementById("searchInput");
    const filter = inputField.value.toLowerCase().trim();
    const tr = document.getElementById("mainTable").getElementsByTagName("tr");
    const sideNav = document.getElementById('sideNav');

    // Прячем алфавит, когда человек начинает писать в поиске
    if (sideNav) {
        sideNav.style.opacity = filter ? "0" : "1";
        sideNav.style.pointerEvents = filter ? "none" : "auto";
    }

    // ЛОГИКА ПАСХАЛКИ
    const triggerWords = ["modr", "ирина"];
    if (triggerWords.includes(filter)) {
        // Запуск конфетти (если библиотека подключена в head)
        if (typeof confetti === 'function') {
            confetti({ particleCount: 150, spread: 70, origin: { y: 0.6 } });
        }
        
        inputField.classList.add('shake');
        
        for (let i = 1; i < tr.length; i++) {
            tr[i].style.display = ""; 
            if (!tr[i].classList.contains('story-row')) {
                const nameCell = tr[i].cells[0];
                if (!nameCell.hasAttribute("data-original")) {
                    nameCell.setAttribute("data-original", nameCell.innerText);
                }
                nameCell.innerHTML = "Люблю вас! ❤️";
                nameCell.style.color = "#ff4081";
            }
        }
        
        // Через 4 секунды возвращаем всё как было
        setTimeout(() => {
            inputField.classList.remove('shake');
            clearInput(); 
        }, 4000);
        return;
    }

    // ОБЫЧНАЯ ФИЛЬТРАЦИЯ ТАБЛИЦЫ
    let storyVisible = false;
    for (let i = 1; i < tr.length; i++) {
        const row = tr[i];
        if (row.classList.contains('story-row')) {
            storyVisible = row.innerText.toLowerCase().includes(filter);
            row.style.display = storyVisible ? "" : "none";
        } else {
            const nameCell = row.cells[0];
            const original = nameCell.getAttribute("data-original") || nameCell.innerText;
            if (!nameCell.hasAttribute("data-original")) nameCell.setAttribute("data-original", original);

            const match = original.toLowerCase().includes(filter);
            if (match || storyVisible) {
                row.style.display = "";
                // Подсветка совпадений
                nameCell.innerHTML = (match && filter !== "") 
                    ? original.replace(new RegExp(`(${filter})`, "gi"), "<mark>$1</mark>") 
                    : original;
                
                // Показываем заголовок истории для этого героя
                let p = row.previousElementSibling;
                while(p && !p.classList.contains('story-row')) p = p.previousElementSibling;
                if(p) p.style.display = "";
            } else {
                row.style.display = "none";
            }
        }
    }
}

// 3. ОЧИСТКА ПОИСКА
function clearInput() {
    const input = document.getElementById("searchInput");
    if (input) {
        input.value = "";
        
        // Восстанавливаем оригинальные имена в таблице
        const cells = document.querySelectorAll('td');
        cells.forEach(cell => {
            if (cell.hasAttribute("data-original")) {
                cell.innerHTML = cell.getAttribute("data-original");
                cell.style.color = "";
            }
        });
        
        filterData(); // Сбрасываем фильтры
        input.focus();
    }
}

// 4. КОПИРОВАНИЕ
function copy(btn) {
    const text = btn.parentElement.querySelector('.code-text').innerText;
    navigator.clipboard.writeText(text).then(() => {
        if (window.navigator.vibrate) window.navigator.vibrate(25);
        const oldText = btn.innerText;
        btn.innerText = "ГОТОВО ✓";
        btn.style.background = "#4caf50";
        setTimeout(() => {
            btn.innerText = oldText;
            btn.style.background = "";
        }, 1000);
    });
}

// 5. ТЕМНАЯ ТЕМА
function toggleTheme() {
    document.body.classList.toggle("dark-mode");
    const isDark = document.body.classList.contains("dark-mode");
    localStorage.setItem("theme", isDark ? "dark" : "light");
    const btn = document.getElementById("themeBtn");
    if (btn) btn.innerText = isDark ? "☀️" : "🌙";
}

// 6. ЗАПУСК ВСЕГО ПРИ ЗАГРУЗКЕ СТРАНИЦЫ
window.addEventListener('DOMContentLoaded', () => {
    // Генерируем буквы
    generateAlphabet();
    
    // Проверяем сохраненную тему
    if (localStorage.getItem("theme") === "dark") {
        document.body.classList.add("dark-mode");
        const btn = document.getElementById("themeBtn");
        if (btn) btn.innerText = "☀️";
    }
    
    // Динамический заголовок вкладки
    window.onblur = () => document.title = "Жду тебя! 💎";
    window.onfocus = () => document.title = "RC Slots - База";

// Функция открытия/закрытия панели
function toggleNav(event) {
    if (event) event.stopPropagation(); // Чтобы клик по стрелке не считался кликом по экрану
    const nav = document.getElementById('sideNav');
    nav.classList.toggle('hidden');
}

// Закрытие при клике в любое место экрана
document.addEventListener('click', (event) => {
    const nav = document.getElementById('sideNav');
    const isClickInside = nav.contains(event.target);

    // Если панель открыта и клик был НЕ по ней — закрываем
    if (!isClickInside && !nav.classList.contains('hidden')) {
        nav.classList.add('hidden');
    }
});

// Обнови функцию генерации алфавита (добавь stopPropagation)
function generateAlphabet() {
    const sideNav = document.getElementById('sideNav');
    if (!sideNav) return;
    
    const stories = document.querySelectorAll('.story-row');
    const letters = new Set();
    
    // Очищаем всё, кроме кнопки-стрелки
    const toggleBtn = document.getElementById('navToggle');
    sideNav.innerHTML = '';
    if (toggleBtn) sideNav.appendChild(toggleBtn);

    stories.forEach(story => {
        const firstLetter = story.innerText.trim()[0].toUpperCase();
        if (firstLetter && !letters.has(firstLetter)) {
            letters.add(firstLetter);
            const link = document.createElement('a');
            link.href = "javascript:void(0)";
            link.innerText = firstLetter;
            link.onclick = (e) => {
                e.stopPropagation(); // Предотвращаем закрытие при выборе буквы
                story.scrollIntoView({ behavior: 'smooth', block: 'start' });
            };
            sideNav.appendChild(link);
        }
    });
}

});


</script>
<div class="footer-text">modr. x timon.</div>

</body>
</html>
