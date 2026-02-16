
<html lang="ru">

    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MODR Slots Database</title>

    
    <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>💎</text></svg>">
    
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    
<style>
:root {
    /* Светлая тема */
    --bg-page: #eef7ff;
    --table-bg: rgba(255, 255, 255, 0.7);
    --text-main: #074799;
    --accent-blue: #0091ea;
    --story-header: rgba(209, 233, 255, 0.85);
    --code-bg: rgba(240, 250, 255, 0.6);
    --highlight: #fff176;
    --btn-gradient: linear-gradient(135deg, #0091ea 0%, #00b0ff 100%);
    --search-icon: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 24 24' stroke='%230091ea' stroke-width='3'%3E%3Cpath stroke-linecap='round' stroke-linejoin='round' d='M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z' /%3E%3C/svg%3E");
    
    /* Переменные для магии (Светлые) */
    --magic-color: #0091ea;
    --magic-text-shadow: 0 0 20px rgba(0, 145, 234, 0.5);
    --toast-bg: rgba(7, 71, 153, 0.9);
}

[data-theme="dark"] {
    /* Темная тема */
    --bg-page: #0f172a;
    --table-bg: rgba(30, 41, 59, 0.6);
    --text-main: #f1f5f9;
    --accent-blue: #38bdf8;
    --story-header: rgba(51, 65, 85, 0.9);
    --code-bg: rgba(15, 23, 42, 0.7);
    --highlight: #fb8c00;
    --btn-gradient: linear-gradient(135deg, #38bdf8 0%, #0ea5e9 100%);
    
    /* Переменные для магии (Неон) */
    --magic-color: #00f2ff;
    --magic-text-shadow: 0 0 20px #00f2ff, 0 0 50px #00f2ff;
    --toast-bg: rgba(0, 0, 0, 0.8);
}

* { box-sizing: border-box; }

body {
    font-family: 'Segoe UI', Roboto, sans-serif;
    margin: 0;
    padding: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
    background: var(--bg-page);
    transition: background 0.5s ease;
    overflow-x: hidden;
}

/* --- ПАСХАЛКИ И ЭФФЕКТЫ --- */

#secret-overlay {
    position: fixed;
    top: 0; left: 0;
    width: 100vw; height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 10001;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.5s ease;
    backdrop-filter: blur(4px);
}

#secret-overlay.show { opacity: 1; }

.secret-text {
    font-size: 5rem;
    color: var(--magic-color);
    text-shadow: var(--magic-text-shadow);
    text-align: center;
    font-weight: 900;
    text-transform: uppercase;
    animation: pulse 0.5s infinite alternate;
}

@keyframes pulse {
    from { transform: scale(1); }
    to { transform: scale(1.1); }
}

.particle {
    position: fixed;
    pointer-events: none;
    width: 6px;
    height: 6px;
    background: var(--magic-color);
    box-shadow: 0 0 10px var(--magic-color);
    border-radius: 50%;
    z-index: 10005;
}

.diamond-rain {
    position: fixed;
    top: -50px;
    font-size: 24px;
    z-index: 9999;
    pointer-events: none;
    animation: fall linear forwards;
    filter: drop-shadow(0 0 5px var(--magic-color));
}

@keyframes fall {
    to { transform: translateY(110vh) rotate(360deg); }
}

/* --- ИНТЕРФЕЙС --- */

#toast {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: var(--toast-bg);
    color: white;
    padding: 12px 25px;
    border-radius: 10px;
    border: 1px solid var(--magic-color);
    box-shadow: 0 0 15px rgba(0, 242, 255, 0.3);
    transform: translateY(150px);
    transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    z-index: 10000;
}

#toast.show { transform: translateY(0); }

#star-container {
    position: fixed;
    top: 0; left: 0;
    width: 100vw; height: 100vh;
    z-index: -2;
    pointer-events: none;
}

[data-theme="light"] #star-container { opacity: 0.3; }

.star {
    position: absolute;
    background: white;
    border-radius: 50%;
    animation: twinkle var(--duration) infinite ease-in-out;
}

[data-theme="light"] .star { background: var(--accent-blue); }

@keyframes twinkle {
    0%, 100% { opacity: 0; transform: scale(0.5); }
    50% { opacity: var(--max-opacity); transform: scale(1.2); }
}

/* --- КОНТЕЙНЕРЫ И 

/* КНОПКА ОТПРАВИТЬ СЛОТЫ */
.tg-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 16px;
    background: var(--btn-gradient);
    color: white !important;
    text-decoration: none;
    font-weight: 800;
    font-size: 14px;
    letter-spacing: 1px;
    border-radius: 16px;
    box-shadow: 0 8px 20px rgba(0, 145, 234, 0.3);
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
    border: 1px solid rgba(255, 255, 255, 0.2) !important;
}

.tg-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 25px rgba(0, 145, 234, 0.5);
    filter: brightness(1.1);
}

/* ПЕРЕКЛЮЧАТЕЛЬ ТЕМ (themeBtn) */
#themeBtn {
    position: fixed;
    top: 15px;
    right: 15px;
    width: 44px;
    height: 44px;
    border-radius: 50%;
    background: var(--table-bg);
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
    font-size: 20px;
    border: 1px solid rgba(255, 255, 255, 0.2) !important;
    backdrop-filter: blur(15px);
    -webkit-backdrop-filter: blur(15px);
    transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

#themeBtn:hover {
    transform: scale(1.1) rotate(15deg);
    box-shadow: 0 0 15px var(--magic-color);
}

/* ПОИСК */
.search-wrapper #searchInput {
    width: 100%;
    padding: 14px 45px;
    border-radius: 16px;
    border: 1px solid rgba(255, 255, 255, 0.1) !important;
    background: var(--table-bg) var(--search-icon) no-repeat 14px center;
    background-size: 20px;
    color: var(--text-main);
    font-size: 14px;
    outline: none;
    transition: 0.3s;
}

.search-wrapper #searchInput:focus {
    box-shadow: 0 0 15px rgba(0, 145, 234, 0.2);
    border-color: var(--accent-blue) !important;
}

#clearSearch {
    position: absolute;
    right: 15px; top: 50%;
    transform: translateY(-50%);
    cursor: pointer;
    color: var(--accent-blue);
    font-size: 24px;
    display: none;
    transition: 0.2s;
}

table {
    width: 100%;
    border-collapse: separate;
    border-spacing: 0 6px;
}

th, td {
    background-color: var(--table-bg) !important;
    color: var(--text-main) !important;
    padding: 10px 5px !important;
    text-align: center;
    font-size: 12px;
    transition: 0.3s ease;
}

tr td:first-child { border-radius: 12px 0 0 12px; }
tr td:last-child { border-radius: 0 12px 12px 0; }

.story-row td {
    background-color: var(--story-header) !important;
    color: var(--accent-blue) !important;
    text-align: left !important;
    padding-left: 15px !important;
    border-radius: 12px !important;
    font-weight: 800;
}

.copy-btn {
    background: var(--btn-gradient);
    color: white;
    border: none;
    padding: 8px;
    border-radius: 8px;
    cursor: pointer;
    width: 90%;
    font-weight: bold;
}

/* КНОПКИ УПРАВЛЕНИЯ */
#theme-toggle {
    position: fixed;
    top: 10px; right: 10px;
    width: 40px; height: 40px;
    border-radius: 50%;
    background: var(--table-bg);
    cursor: pointer;
    display: flex; align-items: center; justify-content: center;
    z-index: 1000;
}

#backToTop {
    position: fixed;
    bottom: 25px; right: 25px;
    width: 50px; height: 50px;
    background: var(--btn-gradient);
    border-radius: 50%;
    display: none; /* Скрыто по умолчанию, управляется JS */
    align-items: center; justify-content: center;
    color: white;
    z-index: 999;
}

@media (max-width: 600px) {
    .secret-text { font-size: 2.5rem; }
}
</style>


<body>

 <body>
    <div id="star-container"></div>
    
    <button id="themeBtn" onclick="toggleTheme()">🌙</button>

   <div class="search-wrapper">
    <input type="text" id="searchInput" oninput="runFilter()" placeholder="Поиск персонажа или истории...">
    <div id="clearSearch" onclick="clearInput()">×</div>
</div>

    </div>
    <div class="tg-wrapper">
        <a href="https://t.me/modr_slots_bot" target="_blank" class="tg-btn">
            ОТПРАВИТЬ СЛОТЫ ⚡
        </a>
    </div>
    </body>

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
<tr><td>Аши</td><td><span class="code-text">365a71d10df45dbc2368135630db129c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">система</td></tr>

<tr class="story-row"><td colspan="3">Арканум</td></tr>
<tr><td>Лиам</td><td><span class="code-text">c050f3a89e9130f3b7eeb90a8f63c8aa</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">2 сезон 7 серия, жрица, искупление</td></tr>
<tr><td>Деймон</td><td><span class="code-text">b7f66b3ace303b21f5111101662041c6</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жрица, искупление, все арканы, финал</td></tr>
<tr><td>Роб</td><td><span class="code-text">f411139513014a04593d49a2fbeb6f04</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жрица, искупление, все арканы, финал</td></tr>

<tr class="story-row"><td colspan="3">Бездушная</td></tr>
<tr><td>Винсент</td><td><span class="code-text">64c35738c74fa1c47a6bb77c8d037694</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">путь баланса</td></tr>
<tr><td>Уолтер</td><td><span class="code-text">ab6f6189c4de352bc47d927c29aa56b9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">путь баланса</td></tr>
<tr><td>Мент (Эллиот)</td><td><span class="code-text">d1f1d2190a7a331a0bdaa0554c94b</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">2 сезон, 5 серия, путь баланса</td></tr>
<tr><td>Трексио</td><td><span class="code-text">d451d86fcd41910efba62d216d323f07</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">путь баланса</td></tr>

<tr class="story-row"><td colspan="3">Высокий прибой</td></tr>
<tr><td>Джейк</td><td><span class="code-text">8af31a9c52257f0c085ea5ffdc1cf3d3</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Отвага</td></tr>

<tr class="story-row"><td colspan="3">Дракула: История любви</td></tr>
<tr><td>Ноэ</td><td><span class="code-text">5544e1ef9352878265d67cb8b4f1035d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">конец 3го сезона, баланс</td></tr>
<tr><td>Влад</td><td><span class="code-text">5ef89c04eb5fe0084c7bc0c98ffe5b23</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">начало 3го сезона, баланс</td></tr>
<tr><td>Влад(2)</td><td><span class="code-text">322cad551b404d2148fa62d0ef1dd1b3</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>
<tr><td>Лео</td><td><span class="code-text">3b443ca263066aaa1caef0f9ef433b93</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс, финал по человеку</td></tr>
<tr>
    <td>Мехмед</td>
    <td>
        <span class="code-text">30b7c5c70f9ccab85e0e9ec8e4fa7d44</span>
        <button class="copy-btn" onclick="copy(this)">Копировать</button>
    </td>
    <td>баланс</td>
</tr>


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

<tr class="story-row"><td colspan="3">Королева за 30 дней</td></tr>
<tr><td>Адам</td><td><span class="code-text">83b84000fdf539754928b33d18e249ed</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Упорство</td></tr>

<tr class="story-row"><td colspan="3">Легенда Ивы</td></tr>
<tr><td>Кадзу</td><td><span class="code-text">974e6428cd00bcbc1f3737c02b1d1024</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Тимон, новый код! страсть, янтарная лиса</td></tr>

<tr class="story-row"><td colspan="3">Песнь о Красном Ниле</td></tr>
<tr><td>Ливий</td><td><span class="code-text">d13d0007af972568f876507cf9af10a2</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность, некромантия</td></tr>
<tr><td>Сет</td><td><span class="code-text">a0b719bc394314786f64253a8539cb30</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хитрость, некромантия</td></tr>
<tr><td>Амен</td><td><span class="code-text">6cd61d7df682189d9911cadaf85c5482</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность, некромантия</td></tr>
<tr><td>Анубис</td><td><span class="code-text">07642c99bee9f281d329174668b6fcf3</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность, онейромантия</td></tr>

<tr class="story-row"><td colspan="3">По тонкому льду</td></tr>
<tr><td>Ходж</td><td><span class="code-text">93475beb0b556f2e6fc3c18551edb6fa</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Баланс</td></tr>

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
<tr><td>Давид</td><td><span class="code-text">74d99b334219b8e8d762475c91f0acb0</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">скептицизм</td></tr>

<tr class="story-row"><td colspan="3">Роза Пустыни</td></tr>
<tr><td>Адиль</td><td><span class="code-text">fe7933dfe668439263d6139f367c3601</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">мечтательность, баланс пустыни и дитя, без 3го сезона</td></tr>
<tr><td>Зейн</td><td><span class="code-text">a3c176918bd0734ad23e9e570c96f7fe</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">мечтательность, баланс пустыни и дитя города</td></tr>

<tr class="story-row"><td colspan="3">Сага о Грозах</td></tr>
<tr><td>Ша'арнез</td><td><span class="code-text">0c1e8e898fa04d809817115fb3d09cf9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Ворон, призыв</td></tr>
<tr><td>Велора</td><td><span class="code-text">af2c8064bd9b338eca5286db66a567ff</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">ворон, изменения, конец 1го сезона</td></tr>
<tr><td>Тай</td><td><span class="code-text">d41eb664fd102d5cf9df87d00ca88e80</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">ворон, изменения, середина 2го сезона</td></tr>
<tr><td>Гриаран</td><td><span class="code-text">5b90b322cb696c25c5d7250f05b6f380</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">ворон, изменения, середина 3го сезона</td></tr>
<tr>
    <td>Эльф</td>
    <td>
        <span class="code-text">c817f98c8c1371cb4a972e4701f24e47</span>
        <button class="copy-btn" onclick="copy(this)">Копировать</button>
    </td>
    <td>ворон призыв</td>
</tr>


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
<tr><td>Каин</td><td><span class="code-text">2c30b39060ee94b301471b9ae6c1bb04</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Шепот дьявола Высокая адаптация/td></tr>
<tr><td>Борис</td><td><span class="code-text">a0d2993286217cf643ce1ad1b6446cf0</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Бог Высокая адаптация/td></tr>

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
<tr>
    <td>Кингу</td>
    <td>
        <span class="code-text">2f85a2203ae6ec2ba83bc6f5a5c2c95e</span>
        <button class="copy-btn" onclick="copy(this)">Копировать</button>
    </td>
    <td>огонь</td>
</tr>

<tr class="story-row"><td colspan="3">Шифр Шекспира</td></tr>
<tr><td>Эдвард</td><td><span class="code-text">7ce633d7d01a54b4caa4557e1600fbcc</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">без греха + хс</td></tr>
<tr><td>Эдмунд</td><td><span class="code-text">df0f71ee75e866439ea95692d8c6729b</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">грех Реджины + хс</td></tr>
<tr><td>Хобелло</td><td><span class="code-text">a8504347c17547f2f47ca047dd3d927e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">без греха + хс</td></tr>
<tr><td>Ральф</td><td><span class="code-text">bb76420474a8f2c702610505ba99de5f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">без греха + хс</td></tr>
<tr>
    <td>Абрахам</td>
    <td>
        <span class="code-text">6b74d66458d59e4ed0492bc0f90325db</span>
        <button class="copy-btn" onclick="copy(this)">Копировать</button>
    </td>
    <td>чародейство / хол. сердце</td>
</tr>


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
<tr>
    <td>Александр</td>
    <td>
        <span class="code-text">be33eb23b5b85f75b53dafb2ff9e7c21</span>
        <button class="copy-btn" onclick="copy(this)">Копировать</button>
    </td>
    <td>логика, авторитет с финалом</td>
</tr>

<tr class="story-row"><td colspan="3">Ярость Титанов</td></tr>
<tr><td>Мёрфи</td><td><span class="code-text">a6e9c1b40abb0d1f7e7fda9f8d9cb026</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">божественность, влияние</td></tr>
<tr class="story-row"><td colspan="3">modr. x timon.</td></tr>


    


    <button id="backToTop" onclick="scrollToTop()">▲</button>

<script>
/**
 * 1. СИСТЕМА ТЕМЫ (Интеграция с твоим CSS)
 */
const storageKey = 'theme-preference';

const reflectPreference = () => {
    const theme = localStorage.getItem(storageKey) || 
        (window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light');
    
    // Устанавливаем атрибут для CSS переменных
    document.documentElement.setAttribute('data-theme', theme);
    
    // Обновляем иконку на кнопке
    const themeBtn = document.querySelector('#theme-toggle');
    if (themeBtn) themeBtn.innerHTML = theme === 'light' ? '🌙' : '☀️';
};

const toggleTheme = (e) => {
    const current = document.documentElement.getAttribute('data-theme');
    const next = current === 'light' ? 'dark' : 'light';
    localStorage.setItem(storageKey, next);
    reflectPreference();
    
    // Искры при смене темы
    if (e) {
        const x = e.clientX || (e.touches && e.touches[0].clientX);
        const y = e.clientY || (e.touches && e.touches[0].clientY);
        spawnParticles(x, y);
    }
};

// Запуск темы немедленно, чтобы не было "мигания" белым
reflectPreference();

/**
 * 2. ПОИСК И ПАСХАЛКИ
 */
// --- ФУНКЦИЯ ПОИСКА ---
function runFilter() {
    const input = document.getElementById('searchInput');
    const clearBtn = document.getElementById('clearSearch');
    const filter = input.value.toLowerCase().trim();
    const rows = Array.from(document.querySelectorAll('tbody tr'));

    // 1. Показываем/скрываем крестик
    if (clearBtn) {
        clearBtn.style.display = filter.length > 0 ? 'flex' : 'none';
    }

    // 2. Пасхалки
    if (filter === 'modr' || filter === 'ирина') { startConfetti(); clearInput(); return; }
    if (filter === 'timer' || filter === 'таймер') { showFullscreenText("SYSTEM OVERRIDE"); clearInput(); return; }

    // 3. Логика фильтрации
    let currentStoryRow = null;
    let storyHasMatch = false;
    let rowsToProcess = [];

    rows.forEach((row) => {
        if (row.classList.contains('story-row')) {
            // Если мы дошли до нового заголовка, обрабатываем предыдущую группу
            if (currentStoryRow) {
                currentStoryRow.style.display = (filter === '' || storyHasMatch) ? '' : 'none';
            }
            currentStoryRow = row;
            storyHasMatch = false;
            // Если само название истории совпадает с поиском, помечаем, что история найдена
            if (row.innerText.toLowerCase().includes(filter)) storyHasMatch = true;
        } else {
            const isMatch = row.innerText.toLowerCase().includes(filter);
            row.style.display = isMatch ? '' : 'none';
            if (isMatch) storyHasMatch = true;
        }
    });

    // Не забываем обработать последнюю историю в списке
    if (currentStoryRow) {
        currentStoryRow.style.display = (filter === '' || storyHasMatch) ? '' : 'none';
    }
}

// --- ФУНКЦИЯ ОЧИСТКИ ---
function clearInput() {
    const input = document.getElementById('searchInput');
    if (input) {
        input.value = '';
        runFilter(); // Сбрасываем таблицу
        input.focus();
    }
}



/**
 * 3. КОПИРОВАНИЕ И TOAST
 */
function copy(btn) {
    const text = btn.getAttribute('data-code') || btn.previousElementSibling?.innerText;
    if (!text) return;

    navigator.clipboard.writeText(text).then(() => {
        showToast(`Код ${text} скопирован!`);
    });
}

function showToast(msg) {
    let toast = document.getElementById('toast');
    if (!toast) {
        toast = document.createElement('div');
        toast.id = 'toast';
        document.body.appendChild(toast);
    }
    toast.innerText = msg;
    toast.classList.add('show');
    setTimeout(() => toast.classList.remove('show'), 2000);
}

/**
 * 4. ЭФФЕКТЫ (ИСКРЫ, КОНФЕТТИ, ТЕКСТ)
 */
function spawnParticles(x, y) {
    if (!x || !y) return;
    for (let i = 0; i < 10; i++) {
        const p = document.createElement('div');
        p.className = 'particle';
        document.body.appendChild(p);
        
        // Позиция
        p.style.left = x + 'px';
        p.style.top = y + 'px';

        requestAnimationFrame(() => {
            const destX = (Math.random() - 0.5) * 120;
            const destY = (Math.random() - 0.5) * 120;
            p.style.transform = `translate(${destX}px, ${destY}px) scale(0)`;
            p.style.opacity = '0';
        });
        setTimeout(() => p.remove(), 600);
    }
}

function startConfetti() {
    for (let i = 0; i < 40; i++) {
        const d = document.createElement('div');
        d.className = 'diamond-rain';
        d.innerHTML = '💎';
        d.style.left = Math.random() * 100 + 'vw';
        d.style.animationDuration = (Math.random() * 2 + 2) + 's';
        document.body.appendChild(d);
        setTimeout(() => d.remove(), 4000);
    }
}

function showFullscreenText(message) {
    let overlay = document.getElementById('secret-overlay');
    if (!overlay) {
        overlay = document.createElement('div');
        overlay.id = 'secret-overlay';
        overlay.innerHTML = `<div class="secret-text">${message}</div>`;
        document.body.appendChild(overlay);
    }
    overlay.classList.add('show');
    setTimeout(() => overlay.classList.remove('show'), 3000);
}

/**
 * 5. ГЕНЕРАЦИЯ ЗВЕЗД
 */
function createStars() {
    const container = document.getElementById('star-container');
    if (!container) return;
    const count = 100;
    for (let i = 0; i < count; i++) {
        const star = document.createElement('div');
        star.className = 'star';
        const size = Math.random() * 3 + 'px';
        star.style.width = size;
        star.style.height = size;
        star.style.left = Math.random() * 100 + '%';
        star.style.top = Math.random() * 100 + '%';
        star.style.setProperty('--duration', (Math.random() * 3 + 2) + 's');
        star.style.setProperty('--max-opacity', Math.random() * 0.7 + 0.3);
        container.appendChild(star);
    }
}

/**
 * 6. ИНИЦИАЛИЗАЦИЯ И СОБЫТИЯ
 */
const handleInteraction = (e) => {
    const x = e.clientX || (e.touches && e.touches[0].clientX);
    const y = e.clientY || (e.touches && e.touches[0].clientY);
    const target = e.target;

    // Искры для кнопок
    if (target.tagName === 'BUTTON' || target.closest('button') || target.classList.contains('copy-btn') || target.id === 'clearSearch' || target.id === 'backToTop') {
        spawnParticles(x, y);
    }
    
    // Клик по теме
    if (target.id === 'theme-toggle' || target.closest('#theme-toggle')) {
        toggleTheme(e);
    }
};

document.addEventListener('click', handleInteraction);
document.addEventListener('touchstart', handleInteraction, { passive: true });

function scrollToTop() {
    window.scrollTo({ top: 0, behavior: 'smooth' });
}

window.addEventListener('scroll', () => {
    const btn = document.getElementById('backToTop');
    if (btn) {
        if (window.scrollY > 300) btn.classList.add('show');
        else btn.classList.remove('show');
    }
});

document.addEventListener('DOMContentLoaded', () => {
    reflectPreference();
    createStars();
    runFilter();
});
</script>


    
    
