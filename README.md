
<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

<style>
    :root {
        /* Светлая тема */
        --bg-page: #eef7ff; 
        --table-bg: #ffffff; 
        --text-main: #074799;
        --accent-blue: #0091ea; 
        --story-header: #d1e9ff; 
        --code-bg: #f0faff;
        --highlight: #fff176;
        --btn-gradient: linear-gradient(135deg, #0091ea 0%, #00b0ff 100%);
        --search-icon: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 24 24' stroke='%230091ea' stroke-width='3'%3E%3Cpath stroke-linecap='round' stroke-linejoin='round' d='M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z' /%3E%3C/svg%3E");
    }

    body.dark-theme {
        /* Темная тема */
        --bg-page: #0f172a; 
        --table-bg: #1e293b; 
        --text-main: #f1f5f9;
        --accent-blue: #38bdf8; 
        --story-header: #334155; 
        --code-bg: #0f172a;
        --highlight: #fb8c00;
        --btn-gradient: linear-gradient(135deg, #38bdf8 0%, #0ea5e9 100%);
    }

    * { box-sizing: border-box; }

   body {
    background: transparent;
        font-family: 'Segoe UI', Roboto, sans-serif; 
        color: var(--text-main); 
        padding: 10px; 
        margin: 0; 
        display: flex; 
        flex-direction: column; 
        align-items: center; 
        transition: background 0.3s, color 0.3s; 
        min-height: 100vh;
    }

    /* МАСШТАБ И КОНТЕЙНЕРЫ */
    .tg-wrapper, .search-wrapper, .table-container { 
        width: 100%; 
        max-width: 600px; 
        margin-bottom: 12px; 
    }

    /* КНОПКА ОТПРАВИТЬ СЛОТЫ */
    .tg-btn { 
        display: flex; 
        align-items: center; 
        justify-content: center; 
        gap: 10px;
        width: 100%; 
        padding: 14px; 
        background: var(--btn-gradient);
        color: white !important; 
        text-decoration: none; 
        font-weight: 800; 
        border-radius: 14px;
        box-shadow: 0 6px 15px rgba(0, 145, 234, 0.2);
        font-size: 15px;
    }

    /* ПОИСКОВАЯ СТРОКА */
    .search-wrapper { position: relative; }
    #searchInput {
        width: 100%; 
        padding: 12px 45px; 
        border-radius: 14px; 
        border: none;
        background: var(--table-bg) var(--search-icon) no-repeat 14px center; 
        background-size: 18px;
        color: var(--text-main); 
        outline: none; 
        box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        font-size: 14px;
    }
    #clearSearch { 
        position: absolute; 
        right: 15px; 
        top: 50%; 
        transform: translateY(-50%); 
        cursor: pointer; 
        color: var(--accent-blue); 
        font-size: 22px; 
        font-weight: bold; 
        display: none; 
        z-index: 5; 
    }

    /* ТАБЛИЦА - ПОЛНАЯ ФИКСАЦИЯ */
    table { 
        width: 100%; 
        border-collapse: separate; 
        border-spacing: 0 6px; 
        table-layout: fixed; 
    }
    
    /* Стили ячеек (th - для верхней строки, td - для данных) */
    th, td { 
        background-color: var(--table-bg) !important; 
        color: var(--text-main) !important; 
        padding: 8px 4px !important; 
        border: none !important; 
        text-align: center; 
        font-size: 12px;
        height: 70px; 
        vertical-align: middle;
        overflow: hidden;
    }

    /* ПРИНУДИТЕЛЬНО ТЕМНАЯ ВЕРХНЯЯ СТРОКА */
    thead th, thead td {
        background-color: var(--table-bg) !important;
        color: var(--accent-blue) !important;
        font-weight: bold;
        text-transform: uppercase;
        font-size: 11px;
        height: 40px; /* Шапка чуть ниже основных строк */
    }
    
    /* Пропорции колонок */
    tr th:nth-child(1), tr td:nth-child(1) { border-radius: 12px 0 0 12px; width: 25%; font-weight: bold; }
    tr th:nth-child(2), tr td:nth-child(2) { width: 45%; }
    tr th:nth-child(3), tr td:nth-child(3) { border-radius: 0 12px 12px 0; width: 30%; font-size: 10px; }

    /* ЗАГОЛОВКИ ИСТОРИЙ */
    .story-row td { 
        background-color: var(--story-header) !important; 
        color: var(--accent-blue) !important; 
        height: 45px !important; 
        text-align: left !important; 
        padding-left: 15px !important; 
        border-radius: 12px !important; 
        font-weight: 800;
        font-size: 13px;
    }

    /* ПОДСВЕТКА ПОИСКА */
    mark { 
        background-color: var(--highlight); 
        color: #000; 
        border-radius: 2px; 
        padding: 0 1px;
    }

    /* КОПИРОВАНИЕ И КОД */
    .code-text { 
        font-family: 'Courier New', monospace; 
        font-size: 9px; 
        display: block; 
        margin-bottom: 5px; 
        color: var(--accent-blue); 
        word-break: break-all; 
        padding: 5px; 
        background: var(--code-bg); 
        border-radius: 6px; 
    }
    
    .copy-btn { 
        background: var(--btn-gradient); 
        color: white; 
        border: none; 
        padding: 7px; 
        border-radius: 8px; 
        cursor: pointer; 
        width: 95%; 
        font-weight: bold; 
        font-size: 10px; 
        text-transform: uppercase; 
    }
    .copy-btn.copied { background: #27ae60 !important; }

    /* КНОПКИ УПРАВЛЕНИЯ */
    #themeBtn { 
        position: fixed; top: 10px; right: 10px; 
        border: none; background: var(--table-bg); 
        width: 38px; height: 38px; border-radius: 50%; 
        z-index: 100; cursor: pointer; 
        box-shadow: 0 2px 8px rgba(0,0,0,0.2); 
        color: var(--text-main); font-size: 18px;
    }
    
    #backToTop { 
        position: fixed; bottom: 20px; right: 20px; 
        width: 48px; height: 48px; 
        background: var(--btn-gradient); 
        border: none; border-radius: 50%; 
        cursor: pointer; z-index: 99; 
        display: flex; align-items: center; justify-content: center; 
        opacity: 0; pointer-events: none; 
        transition: 0.4s; 
        box-shadow: 0 4px 15px rgba(0,0,0,0.3); 
    }
    #backToTop.show { opacity: 1; pointer-events: auto; transform: translateY(0); }

    /* ЖИВОЙ ФОН */
.bg-animation {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1; /* Чтобы фон был за контентом */
    overflow: hidden;
    background: var(--bg-page);
    transition: background 0.3s;
}

.blob {
    position: absolute;
    width: 300px;
    height: 300px;
    background: var(--accent-blue);
    filter: blur(80px); /* Делает пятна мягкими */
    border-radius: 50%;
    opacity: 0.15; /* Очень прозрачно, чтобы не мешать тексту */
    animation: move 20s infinite alternate;
}

/* Настройки для каждого пятна (разные позиции и скорость) */
.blob:nth-child(1) { top: -100px; left: -100px; animation-duration: 25s; }
.blob:nth-child(2) { bottom: -100px; right: -100px; animation-duration: 30s; opacity: 0.1; }
.blob:nth-child(3) { top: 40%; left: 50%; animation-duration: 20s; width: 200px; opacity: 0.08; }

/* Анимация плавного движения */
@keyframes move {
    from { transform: translate(0, 0) scale(1); }
    to { transform: translate(50px, 100px) scale(1.2); }
}

/* В темной теме сделаем пятна чуть заметнее */
body.dark-theme .blob {
    opacity: 0.2;
    background: #1e40af; /* Глубокий синий для темной темы */
}
</style>

<button id="themeBtn" onclick="toggleTheme()">🌙</button>

<div class="tg-wrapper">
    <a href="https://t.me/modr_slots_bot" target="_blank" class="tg-btn">ОТПРАВИТЬ СЛОТЫ ⚡</a>
</div>

<div class="search-wrapper">
    <input type="text" id="searchInput" oninput="runFilter()" placeholder="Поиск персонажа или истории...">
    <div id="clearSearch" onclick="clearInput()">×</div>
</div>
<div class="bg-animation">
    <div class="blob"></div>
    <div class="blob"></div>
    <div class="blob"></div>
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

<button id="backToTop" onclick="scrollToTop()">
    <svg viewBox="0 0 24 24" width="24" height="24" fill="white"><path d="M7.41 15.41L12 10.83l4.59 4.58L18 14l-6-6-6 6z"></path></svg>
</button>

<script>
    const originalNames = new Map();
    let easterEggTriggered = false;

    function runFilter() {
        const input = document.getElementById('searchInput');
        const clearBtn = document.getElementById('clearSearch');
        const filter = input.value.toLowerCase().trim();
        const rows = document.querySelectorAll('#mainTable tbody tr');

        if (clearBtn) clearBtn.style.display = filter.length > 0 ? 'block' : 'none';

        if ((filter === 'modr' || filter === 'ирина') && !easterEggTriggered) {
            fireConfetti();
            easterEggTriggered = true;
        } else if (filter === '') {
            easterEggTriggered = false;
        }

        let storyMatches = false;
        rows.forEach(row => {
            if (row.classList.contains('story-row')) {
                storyMatches = row.innerText.toLowerCase().includes(filter);
                row.style.display = storyMatches ? '' : 'none';
            } else {
                const nameCell = row.cells[0];
                if (!originalNames.has(nameCell)) originalNames.set(nameCell, nameCell.innerText);
                const originalText = originalNames.get(nameCell);
                
                const charMatches = originalText.toLowerCase().includes(filter) || row.cells[2].innerText.toLowerCase().includes(filter);

                if (storyMatches || charMatches) {
                    row.style.display = '';
                    nameCell.innerHTML = (filter && originalText.toLowerCase().includes(filter)) ? 
                        originalText.replace(new RegExp(`(${filter})`, "gi"), '<mark>$1</mark>') : originalText;
                    
                    let prev = row.previousElementSibling;
                    while (prev && !prev.classList.contains('story-row')) prev = prev.previousElementSibling;
                    if (prev) prev.style.display = '';
                } else {
                    row.style.display = 'none';
                }
            }
        });
    }

    function clearInput() {
        document.getElementById('searchInput').value = '';
        runFilter();
        document.getElementById('searchInput').focus();
    }

    function copy(btn) {
        const text = btn.closest('td').querySelector('.code-text').innerText.trim();
        navigator.clipboard.writeText(text).then(() => {
            const old = btn.innerText;
            btn.innerText = 'ГОТОВО ✓';
            btn.classList.add('copied');
            setTimeout(() => { btn.innerText = old; btn.classList.remove('copied'); }, 1500);
        });
    }

    function toggleTheme() {
        document.body.classList.toggle('dark-theme');
        const isDark = document.body.classList.contains('dark-theme');
        localStorage.setItem('theme', isDark ? 'dark' : 'light');
        document.getElementById('themeBtn').innerText = isDark ? '☀️' : '🌙';
    }

    function fireConfetti() {
        const duration = 3000, end = Date.now() + duration;
        (function frame() {
            confetti({ particleCount: 3, angle: 60, spread: 55, origin: { x: 0 }, colors: ['#0091ea', '#ffffff'] });
            confetti({ particleCount: 3, angle: 120, spread: 55, origin: { x: 1 }, colors: ['#0091ea', '#ffffff'] });
            if (Date.now() < end) requestAnimationFrame(frame);
        }());
    }

    window.addEventListener('scroll', () => {
        const btn = document.getElementById('backToTop');
        if (window.pageYOffset > 300) btn.classList.add('show');
        else btn.classList.remove('show');
    });

    function scrollToTop() { window.scrollTo({ top: 0, behavior: 'smooth' }); }

    if (localStorage.getItem('theme') === 'dark') {
        document.body.classList.add('dark-theme');
        document.getElementById('themeBtn').innerText = '☀️';
    }
</script>
<body>

