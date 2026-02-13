
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RC Slots Full Database - Sky Blue</title>
    <style>
        :root {
            --bg-page: #e3f2fd;
            --table-bg: #ffffff;
            --text-main: #0d47a1;
            --text-info: #546e7a;
            --accent-blue: #0288d1;
            --story-header: #bbdefb;
            --btn-copy: #03a9f4;
            --btn-hover: #0277bd;
        }

        body { 
            font-family: 'Segoe UI', Roboto, sans-serif; 
            background-color: var(--bg-page);
            color: #2c3e50;
            margin: 0; padding: 20px 10px;
            display: flex; flex-direction: column; align-items: center;
        }

        .header-box { text-align: center; margin-bottom: 25px; }
        .header-box h2 { color: #01579b; margin: 0; text-transform: uppercase; letter-spacing: 1.5px; font-weight: 800; }

        .search-wrapper { width: 100%; max-width: 900px; margin-bottom: 20px; }
        #searchInput { 
            width: 100%; padding: 15px; border: 2px solid #b3e5fc; border-radius: 12px; 
            font-size: 16px; outline: none; transition: 0.3s; box-sizing: border-box;
        }
        #searchInput:focus { border-color: var(--accent-blue); box-shadow: 0 4px 12px rgba(2, 136, 209, 0.2); }

        .table-container { 
            width: 100%; max-width: 900px; 
            background: var(--table-bg); border-radius: 15px; overflow: hidden; 
            box-shadow: 0 8px 30px rgba(0,0,0,0.1);
        }

        table { width: 100%; border-collapse: collapse; table-layout: fixed; }
        th { background: #f0f7ff; padding: 15px; font-size: 0.85em; text-transform: uppercase; color: #0277bd; border-bottom: 2px solid #e1f5fe; }
        td { padding: 12px 10px; text-align: center; border-bottom: 1px solid #e3f2fd; font-size: 0.95em; }

        th:nth-child(1), td:nth-child(1) { width: 22%; font-weight: 700; color: var(--text-main); }
        th:nth-child(2), td:nth-child(2) { width: 52%; }
        th:nth-child(3), td:nth-child(3) { width: 26%; }

        .story-row { background: var(--story-header); }
        .story-row td { text-align: left; padding: 12px 20px; color: #01579b; font-weight: 800; font-size: 1.05em; border-bottom: 2px solid #90caf9; }

        .code-text { 
            font-family: 'Consolas', monospace; color: #1a237e; word-break: break-all; 
            font-weight: 600; display: block; margin-bottom: 8px; 
            background: #f5faff; padding: 6px; border-radius: 4px; border: 1px solid #e1f5fe;
        }
        
        .copy-btn {
            background: var(--btn-copy); color: white; border: none; padding: 7px 15px; 
            border-radius: 6px; cursor: pointer; font-size: 0.8em; font-weight: 600; transition: 0.2s;
        }
        .copy-btn:hover { background: var(--btn-hover); }
        .copy-btn.copied { background: #4caf50; }

        .info-txt { font-size: 0.85em; color: var(--text-info); font-style: italic; }

        @media (max-width: 600px) {
            td, th { font-size: 0.8em; padding: 8px 5px; }
            .copy-btn { width: 100%; padding: 8px 2px; }
        }
    </style>
</head>
<body>

<div class="header-box">
    <h2>ПОЛНАЯ БАЗА СЛОТОВ RC</h2>
</div>

<div class="search-wrapper">
    <input type="text" id="searchInput" onkeyup="filterData()" placeholder="Поиск по персонажу или истории...">
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
            <tr><td>Оникс</td><td><span class="code-text">024d696ab878ff9cd37faa17ec1694b9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">солнце, статус</td></tr>
            <tr><td>Шен</td><td><span class="code-text">eb50c06aca17d42410b89351df99c25b</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">луна, финал</td></tr>
            <tr><td>Льюсен</td><td><span class="code-text">91a15cc20674e465f65b0d2b8171c129</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">луна, финал</td></tr>
            <tr><td>Ренато</td><td><span class="code-text">e66581e63fde0a21d95f75ecc213a107</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">солнце</td></tr>
            <tr><td>Веспер</td><td><span class="code-text">eff25e263104797a0fb1796ff4771f4e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">луна</td></tr>
            <tr><td>Бастет</td><td><span class="code-text">d451d86fcd41910efba62d216d323f07</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">солнце</td></tr>

            <tr class="story-row"><td colspan="3">Te Amo (1 и 2 тома)</td></tr>
            <tr><td>Майкл (1т)</td><td><span class="code-text">d82650d204cd6817204797033fca7e00</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">восприятие</td></tr>
            <tr><td>Томас (1т)</td><td><span class="code-text">13a2ca74e39b641db42db6369d6e8725</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение</td></tr>
            <tr><td>Ли (1т)</td><td><span class="code-text">f7db94fbabcd3b41b2af6d8ba20628f1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">чувства</td></tr>
            <tr><td>Жанна (1т)</td><td><span class="code-text">8cacc44c76e75bf310a487b7f654a6ea</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">чувства</td></tr>
            <tr><td>Мэт (2т)</td><td><span class="code-text">cf48199c00acd80a0a96ad72fe8544dc</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение</td></tr>

            <tr class="story-row"><td colspan="3">7 Братьев</td></tr>
            <tr><td>Грант</td><td><span class="code-text">2437db5000468bea11082a9c22c91297</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">капитализм</td></tr>
            <tr><td>Саймон</td><td><span class="code-text">31b9101b1eda80857c3e10d178cdce09</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">капитализм</td></tr>
            <tr><td>Джаспер</td><td><span class="code-text">a51a6814eecd12487a2b65bb67563914</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">капитализм</td></tr>
            <tr><td>Аш</td><td><span class="code-text">365a71d10df45dbc2368135630db129c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">аномалия</td></tr>

            <tr class="story-row"><td colspan="3">Арканум</td></tr>
            <tr><td>Лиам</td><td><span class="code-text">c050f3a89e9130f3b7eeb90a8f63c8aa</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жрица</td></tr>
            <tr><td>Роб</td><td><span class="code-text">f411139513014a04593d49a2fbeb6f04</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жрица</td></tr>
            <tr><td>Берт</td><td><span class="code-text">d1f1d2190a7a331a0bdaa0554c94b2a3</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жрица</td></tr>
            <tr><td>Деймон</td><td><span class="code-text">b7f66b3ace303b21f5111101662041c6</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">искупление</td></tr>
            <tr><td>Мэри</td><td><span class="code-text">5dacddb30e3015a5475df5d6f6b3774c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жрица</td></tr>

            <tr class="story-row"><td colspan="3">Бездушная</td></tr>
            <tr><td>Винсент</td><td><span class="code-text">64c35738c74fa1c47a6bb77c8d037694</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>
            <tr><td>Трексио</td><td><span class="code-text">d451d86fcd41910efba62d216d323f07</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>
            <tr><td>Уолтер</td><td><span class="code-text">ab6f6189c4de352bc47d927c29aa56b9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>
            <tr><td>Эллиот</td><td><span class="code-text">d1f1d2190a7a331a0bdaa0554c94b</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>
            <tr><td>Танта</td><td><span class="code-text">8871a06e74362c9da48a0724eb5eb037</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>

            <tr class="story-row"><td colspan="3">Дракула: История Любви</td></tr>
            <tr><td>Влад</td><td><span class="code-text">5ef89c04eb5fe0084c7bc0c98ffe5b23</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">свет</td></tr>
            <tr><td>Влад 2</td><td><span class="code-text">322cad551b404d2148fa62d0ef1dd1b3</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Баланс</td></tr>
            <tr><td>Ноэ</td><td><span class="code-text">5544e1ef9352878265d67cb8b4f1035d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>
            <tr><td>Лео</td><td><span class="code-text">3b443ca263066aaa1caef0f9ef433b93</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">свет</td></tr>
            <tr><td>Сандра</td><td><span class="code-text">1f82e3e2cb055a7b87bf449e4f2b6d8e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>

            <tr class="story-row"><td colspan="3">И поглотит нас морок</td></tr>
            <tr><td>Драган</td><td><span class="code-text">2cd483f99137fd6da27f616d2b0b832a</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">явь</td></tr>
            <tr><td>Волот</td><td><span class="code-text">482f96035041ffa5ba2a86ba4c6c6d7d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">явь</td></tr>
            <tr><td>Озар</td><td><span class="code-text">5b2ae942e42b7f7e3dfa307a92da6412</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">явь</td></tr>
            <tr><td>Сирин</td><td><span class="code-text">9e5ae173528a15c6a70633431d5b73e0</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">явь</td></tr>
            <tr><td>Новак</td><td><span class="code-text">17c10046c34b928a54e042c492114ad2</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">морок</td></tr>
            <tr><td>Тата</td><td><span class="code-text">ac6bb94dc93ff03670242dcf0790d53d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">явь</td></tr>

            <tr class="story-row"><td colspan="3">Кали: Пламя Сансары</td></tr>
            <tr><td>Рам</td><td><span class="code-text">ab3f19bcfa164fc1b641231b631540f8</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">гордость</td></tr>
            <tr><td>Доран</td><td><span class="code-text">0c4281618c21644c1f471caa6b6151ab</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие</td></tr>
            <tr><td>Кристиан</td><td><span class="code-text">fc0df0d7263064c4e7fdf459954876bf</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">конец 2с</td></tr>
            <tr><td>Сара</td><td><span class="code-text">eb7401a112bb8bffd554c25121a24ab6</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие</td></tr>
            <tr><td>Камал</td><td><span class="code-text">f162bdce98c6e34bf9b28d9b3502dfe8</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">гордость</td></tr>
            <tr><td>Тхакур</td><td><span class="code-text">7a433600d30678e35c6cfde3d3c752e9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие</td></tr>

            <tr class="story-row"><td colspan="3">Кали: Зов Тьмы</td></tr>
            <tr><td>Рейтан</td><td><span class="code-text">6d3b4356a3b5816ccbc5f5c95715a6d9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">гнев</td></tr>
            <tr><td>Амрит</td><td><span class="code-text">1520ec77e59ed379751d2f150f50a736</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милость</td></tr>
            <tr><td>Килиан</td><td><span class="code-text">2bfa38fa2b11a412b15ae5e3f488ac58</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">гнев</td></tr>
            <tr><td>Лима</td><td><span class="code-text">d5acbc5eb7ee4173109afdbd7ab5a24c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">гнев</td></tr>
            <tr><td>Габриэль</td><td><span class="code-text">4f03e11a86304a1fd884dfb12c7d827d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милость</td></tr>

            <tr class="story-row"><td colspan="3">Песнь о Красном Ниле</td></tr>
            <tr><td>Амен</td><td><span class="code-text">6cd61d7df682189d9911cadaf85c5482</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность</td></tr>
            <tr><td>Ливий</td><td><span class="code-text">d13d0007af972568f876507cf9af10a2</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">некро</td></tr>
            <tr><td>Сет</td><td><span class="code-text">a0b719bc394314786f64253a8539cb30</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хитрость</td></tr>
            <tr><td>Анубис</td><td><span class="code-text">07642c99bee9f281d329174668b6fcf3</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">онейро</td></tr>
            <tr><td>Агния</td><td><span class="code-text">1a5d43b5329e3d65a596c04f241bcbd1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хитрость</td></tr>
            <tr><td>Реммао</td><td><span class="code-text">31b9101b1eda80857c3e10d178cdce09</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">некро</td></tr>

            <tr class="story-row"><td colspan="3">Пропавшие</td></tr>
            <tr><td>Мадс</td><td><span class="code-text">2c783eaf342ad2d4991746bb5041d2ed</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение</td></tr>
            <tr><td>Ясин</td><td><span class="code-text">1a5d43b5329e3d65a596c04f241bcbd4</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение</td></tr>
            <tr><td>Сафаа</td><td><span class="code-text">81af63c32d7f28afda433d45cff32ea7</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">восприятие</td></tr>

            <tr class="story-row"><td colspan="3">Разбитое сердце Астреи</td></tr>
            <tr><td>Микаэль</td><td><span class="code-text">c6b2d6fda60b786cbb61b7f6443163c2</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">вера</td></tr>
            <tr><td>Давид</td><td><span class="code-text">ff367761332a352cb36e5e5a0bb1bcea</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">вера</td></tr>
            <tr><td>Рафаил</td><td><span class="code-text">d219c6d4627b72d67381773d4b866e5e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">вера</td></tr>
            <tr><td>Кассиэль</td><td><span class="code-text">4ab7ade6839cc30b6168df5b62f75349</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">вера</td></tr>
            <tr><td>Малек</td><td><span class="code-text">ea0602a00c8bedc52bb5aaaa54c4435f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">скептицизм</td></tr>
            <tr><td>Фелония</td><td><span class="code-text">f1ad1c34f9ecdf9f19f731e409c0d5dd</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">вера</td></tr>

            <tr class="story-row"><td colspan="3">Секрет Небес: Реквием</td></tr>
            <tr><td>Каин</td><td><span class="code-text">ac6bb94dc93ff03670242dcf0790d53d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие</td></tr>
            <tr><td>Дима</td><td><span class="code-text">27c666a4a26617b105b29ca465522beb</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие</td></tr>
            <tr><td>Ян</td><td><span class="code-text">fbc509aa35f9955b1939e8f398b7d37e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">адаптация</td></tr>
            <tr><td>Анна</td><td><span class="code-text">5b2ae942e42b7f7e3dfa307a92da6412</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие</td></tr>
            <tr><td>Грег</td><td><span class="code-text">eff25e263104797a0fb1796ff4771f4e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">адаптация</td></tr>

            <tr class="story-row"><td colspan="3">Секрет Небес 1 & 2</td></tr>
            <tr><td>Люцифер</td><td><span class="code-text">5691325191392ca26f8098be0819b783</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">темперамент</td></tr>
            <tr><td>Голод</td><td><span class="code-text">b1af411532cdba680e5a35e18a39a4d7</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровие</td></tr>
            <tr><td>Мальбонте</td><td><span class="code-text">bf5acee0a34afd508f6f10d96904bcd5</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровие</td></tr>
            <tr><td>Астарот</td><td><span class="code-text">8dd4fbc94766a9ef4314e2f960388e6f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровие</td></tr>
            <tr><td>Мими</td><td><span class="code-text">9e61e9fd7a31c6a938a427b0c934f926</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">темперамент</td></tr>
            <tr><td>Война</td><td><span class="code-text">13acbd2204cd1817204797033fca7e01</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровие</td></tr>
            <tr><td>Дино</td><td><span class="code-text">d41a63c32d7f28afda433d45cff32ea9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровие</td></tr>

            <tr class="story-row"><td colspan="3">Грешный Лондон</td></tr>
            <tr><td>Шерлок</td><td><span class="code-text">708d74362c9da48a0724eb5eb037b12a</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">алые тени</td></tr>
            <tr><td>Гластин</td><td><span class="code-text">c1a5d43b5329e3d65a596c04f241bcbd</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">загробный шепот</td></tr>
            <tr><td>Эбигейл</td><td><span class="code-text">8871a06e74362c9da48a0724eb5eb037</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">алые тени</td></tr>
            <tr><td>Грей</td><td><span class="code-text">cf48199c00acd80a0a96ad72fe8544dc</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">алые тени</td></tr>
            <tr><td>Лесли</td><td><span class="code-text">fbc109aa35f9955b1939e8f398b7d37e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">загробный шепот</td></tr>

            <tr class="story-row"><td colspan="3">Десять желаний Софи</td></tr>
            <tr><td>Бенедикт</td><td><span class="code-text">13acbd2204cd1817204797033fca7e01</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">тихоня</td></tr>
            <tr><td>Логан</td><td><span class="code-text">d41a63c32d7f28afda433d45cff32ea9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">стерва</td></tr>
            <tr><td>Диего</td><td><span class="code-text">ac6bb94dc93ff03670242dcf0790d53d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">тихоня</td></tr>
            <tr><td>Митч</td><td><span class="code-text">ea9c827a062eb5c3bb6fff106c738d85</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">тихоня</td></tr>
            <tr><td>Блэйк</td><td><span class="code-text">eff25e263104797a0fb1796ff4771f4e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">стерва</td></tr>

            <tr class="story-row"><td colspan="3">По тонкому льду</td></tr>
            <tr><td>Ходж</td><td><span class="code-text">5c77bd68832a4e9a8f6d610b2c15987a</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">тьма</td></tr>
            <tr><td>Брайан</td><td><span class="code-text">ea9c827a062eb5c3bb6fff106c738d85</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">свет</td></tr>
            <tr><td>Доминик</td><td><span class="code-text">27c1f8a44d8b928f615e42c492114ad1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>
            <tr><td>Тейт</td><td><span class="code-text">9e61e9fd7a31c6a938a427b0c934f926</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">свет</td></tr>
            <tr><td>Лизи</td><td><span class="code-text">4f03e11a86304a1fd884dfb12c7d827d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">свет</td></tr>
            <tr><td>Леон</td><td><span class="code-text">3b443ca263066aaa1caef0f9ef433b93</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">тьма</td></tr>

            <tr class="story-row"><td colspan="3">Цветок из огня Тиамат</td></tr>
            <tr><td>Кингу</td><td><span class="code-text">fbc109aa35f9955b1939e8f398b7d37e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">меч, огонь</td></tr>
            <tr><td>Ниалл</td><td><span class="code-text">5dacddb30e3015a5475df5d6f6b3774c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">магия, огонь</td></tr>
            <tr><td>Ияр</td><td><span class="code-text">ac6bb94dc93ff03670242dcf0790d53d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">магия</td></tr>
            <tr><td>Су</td><td><span class="code-text">1f82e3e2cb055a7b87bf449e4f2b6d8e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">меч</td></tr>

            <tr class="story-row"><td colspan="3">Теодора</td></tr>
            <tr><td>Лоуренс</td><td><span class="code-text">1f82e3e2cb055a7b87bf449e4f2b6d8e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">романтик</td></tr>
            <tr><td>Джон</td><td><span class="code-text">7a433600d30678e35c6cfde3d3c752e9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">циник</td></tr>
            <tr><td>Фридрих</td><td><span class="code-text">d5acbc5eb7ee4173109afdbd7ab5a24c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">романтик</td></tr>
            <tr><td>Блейн</td><td><span class="code-text">bf5acee0a34afd508f6f10d96904bcd5</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">циник</td></tr>
            <tr><td>Шарлотта</td><td><span class="code-text">8dd4fbc94766a9ef4314e2f960388e6f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">романтик</td></tr>
            <tr><td>Антонио</td><td><span class="code-text">eff25e263104797a0fb1796ff4771f4e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">циник</td></tr>

            <tr class="story-row"><td colspan="3">Пси Ψ</td></tr>
            <tr><td>Иво Мартин</td><td><span class="code-text">2cdd74cc1251b961aba59029430d775c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">импульс, вектор</td></tr>
            <tr><td>Кей Кассель</td><td><span class="code-text">461e14bc97ecaca8f773b2113157c10</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">контроль</td></tr>
            <tr><td>Йонас</td><td><span class="code-text">8aa3af17bddb8304f8d06365fb038698</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">контроль</td></tr>
            <tr><td>Даниэль</td><td><span class="code-text">5b2ae942e42b7f7e3dfa307a92da6412</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">импульс</td></tr>

            <tr class="story-row"><td colspan="3">Эдемов Сад</td></tr>
            <tr><td>Минхёк</td><td><span class="code-text">4f03e11a86304a1fd884dfb12c7d827d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">амбиции, попса</td></tr>
            <tr><td>Кастиэль</td><td><span class="code-text">f1ad1c34f9ecdf9f19f731e409c0d5dd</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">амбиции, попса</td></tr>
            <tr><td>Сонхва</td><td><span class="code-text">5b2ae942e42b7f7e3dfa307a92da6412</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">принципы</td></tr>
            <tr><td>Туён</td><td><span class="code-text">9e61e9fd7a31c6a938a427b0c934f926</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">принципы</td></tr>
            <tr><td>Лия</td><td><span class="code-text">13acbd2204cd1817204797033fca7e01</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">амбиции</td></tr>
            <tr><td>Дин</td><td><span class="code-text">ea9c827a062eb5c3bb6fff106c738d85</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">попса</td></tr>

            <tr class="story-row"><td colspan="3">Сквозь бурю и пламя</td></tr>
            <tr><td>Чанд</td><td><span class="code-text">9e61e9fd7a31c6a938a427b0c934f926</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">прагматик</td></tr>
            <tr><td>Санни</td><td><span class="code-text">4f03e11a86304a1fd884dfb12c7d827d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">вдохновение</td></tr>
            <tr><td>Ар-Джей</td><td><span class="code-text">1a5d43b5329e3d65a596c04f241bcbd1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">прагматик</td></tr>

            <tr class="story-row"><td colspan="3">Ярость Титанов</td></tr>
            <tr><td>Мёрфи</td><td><span class="code-text">a6e9c1b40abb0d1f7e7fda9f8d9cb026</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">божественность</td></tr>
            <tr><td>Эдриан</td><td><span class="code-text">8f42a1990c8b0a51939ef8b08d197621</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">человечность</td></tr>
            <tr><td>Джейсон</td><td><span class="code-text">bf5acee0a34afd508f6f10d96904bcd5</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">божественность</td></tr>
            <tr><td>Хизер</td><td><span class="code-text">8dd4fbc94766a9ef4314e2f960388e6f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">человечность</td></tr>
            <tr><td>Тео</td><td><span class="code-text">eff25e263104797a0fb1796ff4771f4e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">божественность</td></tr>

            <tr class="story-row"><td colspan="3">Я охочусь на тебя 1 & 2</td></tr>
            <tr><td>Александр</td><td><span class="code-text">2c783eaf342ad2d4991746bb5041d2ed</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">логика</td></tr>
            <tr><td>Эзра</td><td><span class="code-text">9e61e9fd7a31c6a938a427b0c934f926</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">интуиция</td></tr>
            <tr><td>Сэмюэль</td><td><span class="code-text">ea9c827a062eb5c3bb6fff106c738d85</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">логика</td></tr>
            <tr><td>Рэйчел</td><td><span class="code-text">4f03e11a86304a1fd884dfb12c7d827d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">интуиция</td></tr>
            <tr><td>Ева</td><td><span class="code-text">1a5d43b5329e3d65a596c04f241bcbd1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">логика</td></tr>

            <tr class="story-row"><td colspan="3">Путь Валькирии</td></tr>
            <tr><td>Улль</td><td><span class="code-text">27c1f8a44d8b928f615e42c492114ad1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">перемены</td></tr>
            <tr><td>Сагр</td><td><span class="code-text">d41a63c32d7f28afda433d45cff32ea1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">порядок</td></tr>
            <tr><td>Локи</td><td><span class="code-text">8871a06e74362c9da48a0724eb5eb037</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">перемены</td></tr>
            <tr><td>Лиод</td><td><span class="code-text">c1a5d43b5329e3d65a596c04f241bcbd</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">порядок</td></tr>
            <tr><td>Ванадис</td><td><span class="code-text">ea9c827a062eb5c3bb6fff106c738d85</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">перемены</td></tr>

            <tr class="story-row"><td colspan="3">Любовь со Звезд</td></tr>
            <tr><td>Рэй</td><td><span class="code-text">1a5d43b5329e3d65a596c04f241bcbd1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наука</td></tr>
            <tr><td>Принц</td><td><span class="code-text">81af63c32d7f28afda433d45cff32ea7</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">спорт</td></tr>
            <tr><td>Урсула</td><td><span class="code-text">d41a63c32d7f28afda433d45cff32ea9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">стиль</td></tr>
            <tr><td>Сара</td><td><span class="code-text">ac6bb94dc93ff03670242dcf0790d53d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наука</td></tr>
            <tr><td>Тодд</td><td><span class="code-text">5691325191392ca26f8098be0819b783</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наука</td></tr>

            <tr class="story-row"><td colspan="3">Классика (РЛ, ВРС, СТ, МГИ)</td></tr>
            <tr><td>Виктор (РЛ)</td><td><span class="code-text">d41a63c32d7f28afda433d45cff32ea1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">дар луны</td></tr>
            <tr><td>Макс (РЛ)</td><td><span class="code-text">8871a06e74362c9da48a0724eb5eb037</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">дар крови</td></tr>
            <tr><td>Брэндон (ВРС)</td><td><span class="code-text">13acbd2204cd1817204797033fca7e01</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">мастерство</td></tr>
            <tr><td>Орландо (ВРС)</td><td><span class="code-text">d41a63c32d7f28afda433d45cff32ea9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">страсть</td></tr>
            <tr><td>Клэр (ВРС)</td><td><span class="code-text">ac6bb94dc93ff03670242dcf0790d53d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">мастерство</td></tr>
            <tr><td>Чарльз (ВРС)</td><td><span class="code-text">ea9c827a062eb5c3bb6fff106c738d85</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">страсть</td></tr>
            <tr><td>Джастин (ВРС)</td><td><span class="code-text">5691325191392ca26f8098be0819b783</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">мастерство</td></tr>
            <tr><td>Хиро (ВРС)</td><td><span class="code-text">bf5acee0a34afd508f6f10d96904bcd5</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">страсть</td></tr>
            <tr><td>Люк (СТ)</td><td><span class="code-text">8dd4fbc94766a9ef4314e2f960388e6f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">осторожность</td></tr>
            <tr><td>Майкл (СТ)</td><td><span class="code-text">eff25e263104797a0fb1796ff4771f4e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">смелость</td></tr>
            <tr><td>Дерек (СТ)</td><td><span class="code-text">9e61e9fd7a31c6a938a427b0c934f926</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">смелость</td></tr>
            <tr><td>Кэнди (СТ)</td><td><span class="code-text">1a5d43b5329e3d65a596c04f241bcbd</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">осторожность</td></tr>
            <tr><td>Джефф (МГИ)</td><td><span class="code-text">31b9101b1eda80857c3e10d178cdce09</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">драма</td></tr>
            <tr><td>Рэй (МГИ)</td><td><span class="code-text">a51a6814eecd12487a2b65bb67563914</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">комедия</td></tr>
            <tr><td>Эллен (МГИ)</td><td><span class="code-text">2437db5000468bea11082a9c22c91297</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">приключения</td></tr>

            <tr class="story-row"><td colspan="3">Покоряя Вершину</td></tr>
            <tr><td>Татсуми</td><td><span class="code-text">2cd483f99137fd6da27f616d2b0b832a</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">мастерство</td></tr>
            <tr><td>Шино-Одори</td><td><span class="code-text">482f96035041ffa5ba2a86ba4c6c6d7d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">холод</td></tr>
            <tr><td>Казу</td><td><span class="code-text">5b2ae942e42b7f7e3dfa307a92da6412</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">холод</td></tr>
            <tr><td>Масамунэ</td><td><span class="code-text">eff25e263104797a0fb1796ff4771f4e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">холод</td></tr>
            <tr><td>Такао</td><td><span class="code-text">17c10046c34b928a54e042c492114ad2</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">страсть</td></tr>

            <tr class="story-row"><td colspan="3">Королева за 30 дней</td></tr>
            <tr><td>Ричард</td><td><span class="code-text">8f42a1990c8b0a51939ef8b08d197621</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">интриги</td></tr>
            <tr><td>Адам</td><td><span class="code-text">bf5acee0a34afd508f6f10d96904bcd5</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">упрямство</td></tr>
            <tr><td>Леонард</td><td><span class="code-text">8dd4fbc94766a9ef4314e2f960388e6f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">расчет</td></tr>

            <tr class="story-row"><td colspan="3">Финал базы</td></tr>
            <tr><td>Архив 1</td><td><span class="code-text">eff25e263104797a0fb1796ff4771f4e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">статус</td></tr>
            <tr><td>Архив 2</td><td><span class="code-text">ac6bb94dc93ff03670242dcf0790d53d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">логика</td></tr>
            <tr><td>Слот Конца</td><td><span class="code-text">4f03e11a86304a1fd884dfb12c7d827d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">финал</td></tr>

        </tbody>
    </table>
</div>

<script>
    function copy(btn) {
        const text = btn.previousElementSibling.innerText;
        navigator.clipboard.writeText(text).then(() => {
            const originalText = btn.innerText;
            btn.innerText = "Скопировано!";
            btn.classList.add('copied');
            setTimeout(() => {
                btn.innerText = originalText;
                btn.classList.remove('copied');
            }, 1200);
        });
    }

    function filterData() {
        const input = document.getElementById("searchInput").value.toLowerCase();
        const rows = document.getElementById("mainTable").getElementsByTagName("tr");
        let lastStoryRow = null;
        let storyHasMatch = false;

        for (let i = 1; i < rows.length; i++) {
            const row = rows[i];
            if (row.classList.contains('story-row')) {
                if (lastStoryRow) lastStoryRow.style.display = storyHasMatch ? "" : "none";
                lastStoryRow = row; storyHasMatch = false;
                row.style.display = "none";
                continue;
            }
            const text = row.innerText.toLowerCase();
            if (text.includes(input)) {
                row.style.display = ""; storyHasMatch = true;
                if (lastStoryRow) lastStoryRow.style.display = "";
            } else { row.style.display = "none"; }
        }
        if (lastStoryRow) lastStoryRow.style.display = storyHasMatch ? "" : "none";
    }
</script>

</body>
</html>
