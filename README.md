<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RC Slots Database - Full</title>
    <style>
        :root {
            --bg-page: #f4f7f9;
            --table-bg: #ffffff;
            --text-main: #1a1a1a;
            --text-secondary: #555555;
            --accent-blue: #3498db;
            --story-header: #eef2f7;
            --gold-dark: #b8860b;
        }

        body { 
            font-family: 'Segoe UI', Helvetica, Arial, sans-serif; 
            background-color: var(--bg-page);
            color: var(--text-main);
            margin: 0; padding: 10px;
            display: flex; flex-direction: column; align-items: center;
        }

        .header-box { text-align: center; margin: 10px 0 20px; }
        .header-box h2 { color: var(--text-main); margin: 0; text-transform: uppercase; letter-spacing: 1px; }

        .search-wrapper { width: 100%; max-width: 900px; margin-bottom: 15px; }
        #searchInput { 
            width: 100%; padding: 14px; border: 2px solid #ddd; border-radius: 10px; 
            font-size: 16px; outline: none; transition: border-color 0.3s;
        }
        #searchInput:focus { border-color: var(--accent-blue); }

        .table-container { 
            width: 100%; max-width: 900px; 
            background: var(--table-bg);
            border-radius: 12px; overflow: hidden; 
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
            border: 1px solid #e0e0e0;
        }

        table { width: 100%; border-collapse: collapse; table-layout: fixed; }
        
        th { background: #f8f9fa; padding: 12px; font-size: 0.8em; text-transform: uppercase; color: #666; border-bottom: 2px solid #eee; }
        td { padding: 12px 8px; text-align: center; border-bottom: 1px solid #f0f0f0; font-size: 0.9em; color: var(--text-main); }

        th:nth-child(1), td:nth-child(1) { width: 22%; font-weight: 600; }
        th:nth-child(2), td:nth-child(2) { width: 53%; }
        th:nth-child(3), td:nth-child(3) { width: 25%; }

        tr:hover:not(.story-row) { background-color: #fcfcfc; }

        .story-row { background: var(--story-header); font-weight: bold; color: var(--gold-dark); }
        .story-row td { text-align: left; padding-left: 15px; border-bottom: 1px solid #d1d8e0; }

        .code-text { font-family: 'Consolas', 'Monaco', monospace; color: #2c3e50; word-break: break-all; font-weight: bold; display: block; margin-bottom: 6px; font-size: 0.95em; }
        
        .copy-btn {
            background: #fdfdfd; color: #27ae60; border: 1px solid #27ae60; padding: 4px 10px; 
            border-radius: 4px; cursor: pointer; font-size: 0.75em; transition: all 0.2s; font-weight: 600;
        }
        .copy-btn:hover { background: #27ae60; color: white; }
        .copy-btn.copied { background: #3498db; border-color: #3498db; color: white; }

        .info-txt { font-size: 0.8em; color: var(--text-secondary); line-height: 1.3; }

        @media (max-width: 600px) {
            td, th { font-size: 0.8em; padding: 10px 4px; }
            .copy-btn { padding: 4px 6px; font-size: 0.7em; }
        }
    </style>
</head>
<body>

<div class="header-box">
    <h2>База слотов фаворитов</h2>
</div>

<div class="search-wrapper">
    <input type="text" id="searchInput" onkeyup="filterData()" placeholder="Введите имя, историю или параметр...">
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
            <tr><td>Оникс</td><td><span class="code-text">024d696ab878ff9cd37faa17ec1694b9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">солнце, статус, присутствие, без фин.</td></tr>
            <tr><td>Шен</td><td><span class="code-text">eb50c06aca17d42410b89351df99c25b</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">луна, статус, присутствие, финал</td></tr>
            <tr><td>Льюсен</td><td><span class="code-text">91a15cc20674e465f65b0d2b8171c129</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">луна, статус, присутствие, финал</td></tr>
            <tr><td>Ренато</td><td><span class="code-text">e66581e63fde0a21d95f75ecc213a107</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">солнце, статус, присутствие, без фин.</td></tr>
            <tr><td>Веспер</td><td><span class="code-text">eff25e263104797a0fb1796ff4771f4e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">луна, статус, присутствие, без фин.</td></tr>

            <tr class="story-row"><td colspan="3">Te Amo (1 и 2 тома)</td></tr>
            <tr><td>Майкл (1т)</td><td><span class="code-text">d82650d204cd6817204797033fca7e00</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">восприятие, финал</td></tr>
            <tr><td>Томас (1т)</td><td><span class="code-text">13a2ca74e39b641db42db6369d6e8725</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение, финал</td></tr>
            <tr><td>Ли (1т)</td><td><span class="code-text">f7db94fbabcd3b41b2af6d8ba20628f1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">чувства, финал</td></tr>
            <tr><td>Жанна (1т)</td><td><span class="code-text">8cacc44c76e75bf310a487b7f654a6ea</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">чувства, финал</td></tr>
            <tr><td>Мэт (2т)</td><td><span class="code-text">cf48199c00acd80a0a96ad72fe8544dc</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение</td></tr>

            <tr class="story-row"><td colspan="3">7б / Авверис</td></tr>
            <tr><td>Грант</td><td><span class="code-text">2437db5000468bea11082a9c22c91297</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">капитализм, милашка</td></tr>
            <tr><td>Саймон</td><td><span class="code-text">31b9101b1eda80857c3e10d178cdce09</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">капитализм, милашка</td></tr>
            <tr><td>Джаспер</td><td><span class="code-text">a51a6814eecd12487a2b65bb67563914</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">капитализм, милашка</td></tr>
            <tr><td>Аш</td><td><span class="code-text">365a71d10df45dbc2368135630db129c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">аномалия, система</td></tr>

            <tr class="story-row"><td colspan="3">Арканум</td></tr>
            <tr><td>Лиам</td><td><span class="code-text">c050f3a89e9130f3b7eeb90a8f63c8aa</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">2с 7с, жрица, искупление</td></tr>
            <tr><td>Деймон</td><td><span class="code-text">b7f66b3ace303b21f5111101662041c6</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жрица, искупление, финал</td></tr>
            <tr><td>Роб</td><td><span class="code-text">f411139513014a04593d49a2fbeb6f04</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жрица, искупление, финал</td></tr>

            <tr class="story-row"><td colspan="3">Бездушная</td></tr>
            <tr><td>Винсент</td><td><span class="code-text">64c35738c74fa1c47a6bb77c8d037694</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>
            <tr><td>Уолтер</td><td><span class="code-text">ab6f6189c4de352bc47d927c29aa56b9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>
            <tr><td>Мент</td><td><span class="code-text">d1f1d2190a7a331a0bdaa0554c94b</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">2с 5с, баланс</td></tr>
            <tr><td>Трексио</td><td><span class="code-text">d451d86fcd41910efba62d216d323f07</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>

            <tr class="story-row"><td colspan="3">Дракула: История любви</td></tr>
            <tr><td>Ноэ</td><td><span class="code-text">5544e1ef9352878265d67cb8b4f1035d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">конец 3с, баланс</td></tr>
            <tr><td>Влад</td><td><span class="code-text">5ef89c04eb5fe0084c7bc0c98ffe5b23</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">начало 3с, баланс</td></tr>
            <tr><td>Лео</td><td><span class="code-text">3b443ca263066aaa1caef0f9ef433b93</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс, финал человек</td></tr>

            <tr class="story-row"><td colspan="3">И поглотит нас морок</td></tr>
            <tr><td>Драган</td><td><span class="code-text">2cd483f99137fd6da27f616d2b0b832a</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">явь, сострадание, выс. связь</td></tr>
            <tr><td>Волот</td><td><span class="code-text">482f96035041ffa5ba2a86ba4c6c6d7d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">явь, сострадание, выс. связь</td></tr>
            <tr><td>Озар</td><td><span class="code-text">5b2ae942e42b7f7e3dfa307a92da6412</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">явь, сострадание, выс. связь</td></tr>
            <tr><td>Сирин</td><td><span class="code-text">9e5ae173528a15c6a70633431d5b73e0</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">явь, сострадание, выс. связь</td></tr>
            <tr><td>Новак</td><td><span class="code-text">17c10046c34b928a54e042c492114ad2</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">морок, сострадание, связь</td></tr>

            <tr class="story-row"><td colspan="3">Идеал</td></tr>
            <tr><td>Мона</td><td><span class="code-text">5533f4140c8373e74845b76002e57eab</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">разум, без финала</td></tr>
            <tr><td>Тьяго</td><td><span class="code-text">3314682cb550834df00991a51abb4e1c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">разум</td></tr>

            <tr class="story-row"><td colspan="3">Кали: Пламя Сансары</td></tr>
            <tr><td>Доран</td><td><span class="code-text">0c4281618c21644c1f471caa6b6151ab</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие, гордость</td></tr>
            <tr><td>Кристиан</td><td><span class="code-text">fc0df0d7263064c4e7fdf459954876bf</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">конец 2с, гордость</td></tr>
            <tr><td>Рам</td><td><span class="code-text">ab3f19bcfa164fc1b641231b631540f8</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие, гордость</td></tr>
            <tr><td>Сара</td><td><span class="code-text">eb7401a112bb8bffd554c25121a24ab6</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">2с 7с, наследие</td></tr>
            <tr><td>Камал</td><td><span class="code-text">f162bdce98c6e34bf9b28d9b3502dfe8</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие, гордость</td></tr>

            <tr class="story-row"><td colspan="3">Кали: Зов Тьмы</td></tr>
            <tr><td>Рейтан</td><td><span class="code-text">6d3b4356a3b5816ccbc5f5c95715a6d9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">3с 5с, гнев</td></tr>
            <tr><td>Килиан</td><td><span class="code-text">2bfa38fa2b11a412b15ae5e3f488ac58</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">гнев, концовка</td></tr>
            <tr><td>Амрит</td><td><span class="code-text">1520ec77e59ed379751d2f150f50a736</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">лояльность, милость</td></tr>

            <tr class="story-row"><td colspan="3">Код синий</td></tr>
            <tr><td>Нахом</td><td><span class="code-text">199362602aebc9aee32696a0c47768e6</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жгг, сочувствие</td></tr>
            <tr><td>Тобиас</td><td><span class="code-text">5706512d2f48a49cbec573ce5496ed38</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жгг, сочувствие</td></tr>
            <tr><td>Эстебан</td><td><span class="code-text">3afeef4fe5f6874b1e5fdba2cd1ce59d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жгг, сочувствие</td></tr>

            <tr class="story-row"><td colspan="3">Легенда Ивы</td></tr>
            <tr><td>Кадзу</td><td><span class="code-text">974e6428cd00bcbc1f3737c02b1d1024</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">страсть, янтарная лиса</td></tr>

            <tr class="story-row"><td colspan="3">Песнь о Красном Ниле</td></tr>
            <tr><td>Ливий</td><td><span class="code-text">d13d0007af972568f876507cf9af10a2</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность, некро</td></tr>
            <tr><td>Сет</td><td><span class="code-text">a0b719bc394314786f64253a8539cb30</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хитрость, некро</td></tr>
            <tr><td>Амен</td><td><span class="code-text">6cd61d7df682189d9911cadaf85c5482</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность, некро</td></tr>
            <tr><td>Анубис</td><td><span class="code-text">07642c99bee9f281d329174668b6fcf3</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность, онейро</td></tr>

            <tr class="story-row"><td colspan="3">Пси Ψ</td></tr>
            <tr><td>Иво</td><td><span class="code-text">2cdd74cc1251b961aba59029430d775c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">импульс, вектор</td></tr>
            <tr><td>Йонас</td><td><span class="code-text">9451e14bc97ecaca8f773b2113157c10</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">контроль, вектор</td></tr>
            <tr><td>Кей</td><td><span class="code-text">0fb719ac9766de2af3d68623974e4d4c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">контроль, форма</td></tr>

            <tr class="story-row"><td colspan="3">Покоряя Версаль</td></tr>
            <tr><td>Александр</td><td><span class="code-text">5b96ea7a8de4ab46697bc1a7eaa56c1c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">расчёт</td></tr>

            <tr class="story-row"><td colspan="3">Пришествие 3</td></tr>
            <tr><td>Зейн</td><td><span class="code-text">a6799ef899b53f7b0961b48c70ef2878</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">догман, напор</td></tr>
            <tr><td>Макс</td><td><span class="code-text">0dbbd6e90b90faf6c13220cf9b7c7cf5</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">отречение, напор</td></tr>
            <tr><td>Ксандр</td><td><span class="code-text">420d05f34ce854f98ed46ee525e2a526</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">отречение, напор (баги)</td></tr>
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
            <tr><td>Адиль</td><td><span class="code-text">fe7933dfe668439263d6139f367c3601</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">мечта, баланс, без 3с</td></tr>
            <tr><td>Зейн</td><td><span class="code-text">a3c176918bd0734ad23e9e570c96f7fe</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">мечта, баланс</td></tr>

            <tr class="story-row"><td colspan="3">Сага о Грозах</td></tr>
            <tr><td>Ша'арнез</td><td><span class="code-text">0c1e8e898fa04d809817115fb3d09cf9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">Ворон, призыв</td></tr>
            <tr><td>Велора</td><td><span class="code-text">af2c8064bd9b338eca5286db66a567ff</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">конец 1с, изменения</td></tr>
            <tr><td>Тай</td><td><span class="code-text">d41eb664fd102d5cf9df87d00ca88e80</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">середина 2с, изменения</td></tr>
            <tr><td>Гриаран</td><td><span class="code-text">5b90b322cb696c25c5d7250f05b6f380</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">середина 3с, изменения</td></tr>

            <tr class="story-row"><td colspan="3">Секрет Небес</td></tr>
            <tr><td>Одиночка</td><td><span class="code-text">4c9152d8dca82cf40e92d29105979f34</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">ангел</td></tr>
            <tr><td>Люцифер</td><td><span class="code-text">35afb2332ef908a54d3bf3cd7f619d40</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">демон</td></tr>
            <tr><td>Маль</td><td><span class="code-text">4dc308fcf83c68f1c040c7d9b35a0261</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">равновесие</td></tr>

            <tr class="story-row"><td colspan="3">Секрет Небес: Реквием</td></tr>
            <tr><td>Дима</td><td><span class="code-text">27c666a4a26617b105b29ca465522beb</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие, адаптация</td></tr>
            <tr><td>Грег</td><td><span class="code-text">baba1f6920e63dbe595047ea4a64d5eb</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие, адаптация</td></tr>
            <tr><td>Ян</td><td><span class="code-text">fbc509aa35f9955b1939e8f398b7d37e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие, адаптация</td></tr>
            <tr><td>Каин</td><td><span class="code-text">ac6bb94dc93ff03670242dcf0790d53d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие, адаптация</td></tr>
            <tr><td>Каин+Авель</td><td><span class="code-text">8aa3af17bddb8304f8d06365fb038698</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жестокость, дьявол</td></tr>

            <tr class="story-row"><td colspan="3">Секрет Небес 2</td></tr>
            <tr><td>Голод</td><td><span class="code-text">b1af411532cdba680e5a35e18a39a4d7</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровие, Война мертв</td></tr>
            <tr><td>Люцифер</td><td><span class="code-text">5691325191392ca26f8098be0819b783</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">темперамент, Война жив</td></tr>
            <tr><td>Астарот</td><td><span class="code-text">8dd4fbc94766a9ef4314e2f960388e6f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровие, Война мертв</td></tr>
            <tr><td>Мальбонте</td><td><span class="code-text">bf5acee0a34afd508f6f10d96904bcd5</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровие, Война жив</td></tr>
            <tr><td>Война</td><td><span class="code-text">cb907d487948233617f4b61c2d5c985a</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">хладнокровие</td></tr>

            <tr class="story-row"><td colspan="3">Секрет небес 3 (Комбо)</td></tr>
            <tr><td>Война+Грег+Кас</td><td><span class="code-text">7a433600d30678e35c6cfde3d3c752e9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие, тьма Шепфа</td></tr>
            <tr><td>Люц+Грег+Кас</td><td><span class="code-text">d5acbc5eb7ee4173109afdbd7ab5a24c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие, тьма Шепфа</td></tr>
            <tr><td>Маль+Каин+Мика</td><td><span class="code-text">1f82e3e2cb055a7b87bf449e4f2b6d8e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие, тьма Шепфа</td></tr>

            <tr class="story-row"><td colspan="3">Эдемов Сад</td></tr>
            <tr><td>Одиночка</td><td><span class="code-text">1b196faa0f4649e8b3c98f50eace2b90</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">1с 8с (выбор ветки)</td></tr>
            <tr><td>Минхёк</td><td><span class="code-text">4f03e11a86304a1fd884dfb12c7d827d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">амбиции, популярность</td></tr>
            <tr><td>Кас</td><td><span class="code-text">f1ad1c34f9ecdf9f19f731e409c0d5dd</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">амбиции, популярность</td></tr>

            <tr class="story-row"><td colspan="3">Другие истории</td></tr>
            <tr><td>Рейнхольд (СТ)</td><td><span class="code-text">a5e2ba6722aa3fe934a4b14a0a0aafd1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рациональность</td></tr>
            <tr><td>Граф (ТГЛГВ)</td><td><span class="code-text">05362d9356139f6d50ddbc29585f5cdc</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жизнелюбие, баланс</td></tr>
            <tr><td>Вишня (ТС)</td><td><span class="code-text">f50408871d7f1ca307939bcfc177aab0</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">осторожность</td></tr>
            <tr><td>Майкл (ТС)</td><td><span class="code-text">b1c0024ca68aa77be6c6586a28cad08f</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">осторожность</td></tr>
            <tr><td>Ниалл (ЦФОТ)</td><td><span class="code-text">5dacddb30e3015a5475df5d6f6b3774c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">огонь</td></tr>
            <tr><td>Сэм (ЯОНТ)</td><td><span class="code-text">ea9c827a062eb5c3bb6fff106c738d85</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">логика</td></tr>
            <tr><td>Эзра (ЯОНТ2)</td><td><span class="code-text">9e61e9fd7a31c6a938a427b0c934f926</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">логика</td></tr>
            <tr><td>Мёрфи (ЯТ)</td><td><span class="code-text">a6e9c1b40abb0d1f7e7fda9f8d9cb026</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">божественность</td></tr>
        </tbody>
    </table>
</div>

<script>
    function copy(btn) {
        const text = btn.previousElementSibling.innerText;
        navigator.clipboard.writeText(text).then(() => {
            const originalText = btn.innerText;
            btn.innerText = "Готово! ✓";
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
                lastStoryRow = row;
                storyHasMatch = false;
                row.style.display = "none";
                continue;
            }

            const text = row.innerText.toLowerCase();
            if (text.includes(input)) {
                row.style.display = "";
                storyHasMatch = true;
                if (lastStoryRow) lastStoryRow.style.display = "";
            } else {
                row.style.display = "none";
            }
        }
        if (lastStoryRow) lastStoryRow.style.display = storyHasMatch ? "" : "none";
    }
</script>

</body>
</html>
