<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Полная база Клуба Романтики</title>
    <style>
        body {
            font-family: 'Segoe UI', sans-serif;
            background-color: #f0f2f5;
            margin: 0;
            padding: 10px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        h2 { color: #2c3e50; text-align: center; margin: 20px 0; }
        .table-container {
            width: 100%;
            max-width: 1000px;
            background: #fff;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            border-radius: 8px;
            overflow: hidden;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            table-layout: fixed;
        }
        th, td {
            padding: 10px 5px;
            text-align: center;
            border-bottom: 1px solid #edf0f2;
            word-wrap: break-word;
            font-size: 0.85em;
        }
        thead { background-color: #34495e; color: #ffffff; }
        .story-header {
            background-color: #e8ecef;
            font-weight: bold;
            color: #2980b9;
            text-transform: uppercase;
            font-size: 0.8em;
        }
        .code-cell {
            font-family: monospace;
            color: #e67e22;
            font-size: 0.75em;
            word-break: break-all;
        }
        .info-cell { font-size: 0.8em; color: #7f8c8d; }
        
        @media screen and (max-width: 480px) {
            th, td { padding: 6px 2px; font-size: 0.75em; }
            .code-cell { font-size: 0.65em; }
        }
    </style>
</head>
<body>

<h2>Все слоты фаворитов</h2>

<div class="table-container">
    <table>
        <thead>
            <tr>
                <th style="width: 25%;">Фаворит</th>
                <th style="width: 45%;">Слот (код)</th>
                <th style="width: 30%;">Инфо</th>
            </tr>
        </thead>
        <tbody>
            <tr class="story-header"><td colspan="3">W: Ловчая Времени</td></tr>
            <tr><td>Оникс</td><td class="code-cell">024d696ab878ff9cd37faa17ec1694b9</td><td></td></tr>
            <tr><td>Шен</td><td class="code-cell">eb50c06aca17d42410b89351df99c25b</td><td></td></tr>
            <tr><td>Льюсен</td><td class="code-cell">91a15cc20674e465f65b0d2b8171c129</td><td></td></tr>
            <tr><td>Ренато</td><td class="code-cell">e66581e63fde0a21d95f75ecc213a107</td><td></td></tr>
            <tr><td>Веспер</td><td class="code-cell">eff25e263104797a0fb1796ff4771f4e</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Te amo 1 том</td></tr>
            <tr><td>Майкл</td><td class="code-cell">d82650d204cd6817204797033fca7e00</td><td class="info-cell">восприятие</td></tr>
            <tr><td>Томас</td><td class="code-cell">13a2ca74e39b641db42db6369d6e8725</td><td class="info-cell">рассуждение</td></tr>
            <tr><td>Ли</td><td class="code-cell">f7db94fbabcd3b41b2af6d8ba20628f1</td><td></td></tr>
            <tr><td>Жанна</td><td class="code-cell">8cacc44c76e75bf310a487b7f654a6ea</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Te amo 2 том</td></tr>
            <tr><td>Мэт</td><td class="code-cell">cf48199c00acd80a0a96ad72fe8544dc</td><td class="info-cell">рассуждение</td></tr>

            <tr class="story-header"><td colspan="3">7б</td></tr>
            <tr><td>Грант</td><td class="code-cell">2437db5000468bea11082a9c22c91297</td><td class="info-cell">капитализм</td></tr>
            <tr><td>Саймон</td><td class="code-cell">31b9101b1eda80857c3e10d178cdce09</td><td></td></tr>
            <tr><td>Джаспер</td><td class="code-cell">a51a6814eecd12487a2b65bb67563914</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Авверис</td></tr>
            <tr><td>Аш</td><td class="code-cell">365a71d10df45dbc2368135630db129c</td><td class="info-cell">-аномалия, система</td></tr>

            <tr class="story-header"><td colspan="3">Арканум</td></tr>
            <tr><td>Лиам</td><td class="code-cell">c050f3a89e9130f3b7eeb90a8f63c8aa</td><td class="info-cell">Возможно с концовкой</td></tr>
            <tr><td>Деймон</td><td class="code-cell">b7f66b3ace303b21f5111101662041c6</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Бездушная</td></tr>
            <tr><td>Винсент</td><td class="code-cell">64c35738c74fa1c47a6bb77c8d037694</td><td></td></tr>
            <tr><td>Уолтер</td><td class="code-cell">ab6f6189c4de352bc47d927c29aa56b9</td><td></td></tr>
            <tr><td>Мент</td><td class="code-cell">d1f1d2190a7a331a0bdaa0554c94b</td><td class="info-cell">2 сезон, 5 серия</td></tr>
            <tr><td>Трексио</td><td class="code-cell">d451d86fcd41910efba62d216d323f07</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Дракула: История любви</td></tr>
            <tr><td>Ноэ</td><td class="code-cell">5544e1ef9352878265d67cb8b4f1035d</td><td class="info-cell">Неизвестно момент</td></tr>
            <tr><td>Влад</td><td class="code-cell">94d6116c84f920fbeab96c47e1518673</td><td></td></tr>
            <tr><td>Лео</td><td class="code-cell">3b443ca263066aaa1caef0f9ef433b93</td><td></td></tr>

            <tr class="story-header"><td colspan="3">И поглотит нас морок</td></tr>
            <tr><td>Драган</td><td class="code-cell">2cd483f99137fd6da27f616d2b0b832a</td><td class="info-cell">выс. связь, явь</td></tr>
            <tr><td>Волот</td><td class="code-cell">482f96035041ffa5ba2a86ba4c6c6d7d</td><td class="info-cell">выс. связь, явь</td></tr>
            <tr><td>Озар</td><td class="code-cell">5b2ae942e42b7f7e3dfa307a92da6412</td><td class="info-cell">выс. связь, явь</td></tr>
            <tr><td>Сирин</td><td class="code-cell">9e5ae173528a15c6a70633431d5b73e0</td><td class="info-cell">выс. связь, явь</td></tr>
            <tr><td>Новак</td><td class="code-cell">17c10046c34b928a54e042c492114ad2</td><td class="info-cell">морок, связь</td></tr>

            <tr class="story-header"><td colspan="3">Идеал</td></tr>
            <tr><td>Мона</td><td class="code-cell">5533f4140c8373e74845b76002e57eab</td><td></td></tr>
            <tr><td>Тьяго</td><td class="code-cell">3314682cb550834df00991a51abb4e1c</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Кали: Пламя Сансары</td></tr>
            <tr><td>Доран</td><td class="code-cell">0c4281618c21644c1f471caa6b6151ab</td><td></td></tr>
            <tr><td>Кристиан</td><td class="code-cell">fc0df0d7263064c4e7fdf459954876bf</td><td></td></tr>
            <tr><td>Рам</td><td class="code-cell">ab3f19bcfa164fc1b641231b631540f8</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Кали: Зов Тьмы</td></tr>
            <tr><td>Рейтан</td><td class="code-cell">6d3b4356a3b5816ccbc5f5c95715a6d9</td><td class="info-cell">3 сезон, 5 серия</td></tr>
            <tr><td>Килиан</td><td class="code-cell">2bfa38fa2b11a412b15ae5e3f488ac58</td><td class="info-cell">Гнев, концовка</td></tr>
            <tr><td>Амрит</td><td class="code-cell">1520ec77e59ed379751d2f150f50a736</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Код синий</td></tr>
            <tr><td>Нахом</td><td class="code-cell">199362602aebc9aee32696a0c47768e6</td><td class="info-cell">жгг, сочувствие</td></tr>
            <tr><td>Тобиас</td><td class="code-cell">5706512d2f48a49cbec573ce5496ed38</td><td class="info-cell">жгг, сочувствие</td></tr>
            <tr><td>Эстебан</td><td class="code-cell">3afeef4fe5f6874b1e5fdba2cd1ce59d</td><td class="info-cell">жгг</td></tr>

            <tr class="story-header"><td colspan="3">Легенда Ивы</td></tr>
            <tr><td>Кадзу</td><td class="code-cell">28e44c2908ee68750cd821defe92a75d</td><td></td></tr>
            <tr><td>Масамунэ</td><td class="code-cell">79f6f2d0d81fbf0da59819523d393e85</td><td class="info-cell">развилка имп.</td></tr>

            <tr class="story-header"><td colspan="3">Песнь о Красном Ниле</td></tr>
            <tr><td>Ливий</td><td class="code-cell">d13d0007af972568f876507cf9af10a2</td><td></td></tr>
            <tr><td>Сет</td><td class="code-cell">a0b719bc394314786f64253a8539cb30</td><td></td></tr>
            <tr><td>Амен</td><td class="code-cell">6cd61d7df682189d9911cadaf85c5482</td><td></td></tr>
            <tr><td>Анубис</td><td class="code-cell">cfa54647ca49869499e6e0473db844a7</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Пси Ψ</td></tr>
            <tr><td>Иво</td><td class="code-cell">2cdd74cc1251b961aba59029430d775c</td><td></td></tr>
            <tr><td>Йонас</td><td class="code-cell">9451e14bc97ecaca8f773b2113157c10</td><td></td></tr>
            <tr><td>Кей</td><td class="code-cell">0fb719ac9766de2af3d68623974e4d4c</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Покоряя Версаль</td></tr>
            <tr><td>Александр</td><td class="code-cell">5b96ea7a8de4ab46697bc1a7eaa56c1c</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Пришествие 3</td></tr>
            <tr><td>Зейн</td><td class="code-cell">a6799ef899b53f7b0961b48c70ef2878</td><td class="info-cell">догман, напор</td></tr>
            <tr><td>Макс</td><td class="code-cell">0dbbd6e90b90faf6c13220cf9b7c7cf5</td><td class="info-cell">отречение, напор</td></tr>
            <tr><td>Ксандр</td><td class="code-cell">420d05f34ce854f98ed46ee525e2a526</td><td></td></tr>
            <tr><td>Октавиан</td><td class="code-cell">a6be010fa0116965bbf359def68699f8</td><td class="info-cell">коварство</td></tr>

            <tr class="story-header"><td colspan="3">Пропавшие</td></tr>
            <tr><td>Мадс</td><td class="code-cell">2c783eaf342ad2d4991746bb5041d2ed</td><td class="info-cell">рассуждение</td></tr>
            <tr><td>Ясин</td><td class="code-cell">1a5d43b5329e3d65a596c04f241bcbd4</td><td class="info-cell">рассуждение</td></tr>
            <tr><td>Куно</td><td class="code-cell">7871a06e74362c9da48a0724eb5eb037</td><td class="info-cell">рассуждение</td></tr>
            <tr><td>Сафаа</td><td class="code-cell">81af63c32d7f28afda433d45cff32ea7</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Разбитое сердце Астреи</td></tr>
            <tr><td>Микаэль</td><td class="code-cell">c6b2d6fda60b786cbb61b7f6443163c2</td><td></td></tr>
            <tr><td>Рафаил</td><td class="code-cell">d219c6d4627b72d67381773d4b866e5e</td><td></td></tr>
            <tr><td>Кас</td><td class="code-cell">4ab7ade6839cc30b6168df5b62f75349</td><td></td></tr>
            <tr><td>Фел</td><td class="code-cell">--</td><td></td></tr>
            <tr><td>Давид</td><td class="code-cell">ff367761332a352cb36e5e5a0bb1bcea</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Роза Пустыни</td></tr>
            <tr><td>Адиль</td><td class="code-cell">fe7933dfe668439263d6139f367c3601</td><td></td></tr>
            <tr><td>Зейн</td><td class="code-cell">a3c176918bd0734ad23e9e570c96f7fe</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Сага о Грозах</td></tr>
            <tr><td>Ша'арнез</td><td class="code-cell">0c1e8e898fa04d809817115fb3d09cf9</td><td></td></tr>
            <tr><td>Велора</td><td class="code-cell">af2c8064bd9b338eca5286db66a567ff</td><td></td></tr>
            <tr><td>Тай</td><td class="code-cell">d41eb664fd102d5cf9df87d00ca88e80</td><td></td></tr>
            <tr><td>Гриаран</td><td class="code-cell">5b90b322cb696c25c5d7250f05b6f380</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Секрет Небес</td></tr>
            <tr><td>одиночка</td><td class="code-cell">4c9152d8dca82cf40e92d29105979f34</td><td></td></tr>
            <tr><td>люся</td><td class="code-cell">35afb2332ef908a54d3bf3cd7f619d40</td><td></td></tr>
            <tr><td>Маль</td><td class="code-cell">4dc308fcf83c68f1c040c7d9b35a0261</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Секрет Небес: Реквием</td></tr>
            <tr><td>Дима</td><td class="code-cell">27c666a4a26617b105b29ca465522beb</td><td class="info-cell">милосердие</td></tr>
            <tr><td>Грег</td><td class="code-cell">baba1f6920e63dbe595047ea4a64d5eb</td><td class="info-cell">милосердие</td></tr>
            <tr><td>Ян</td><td class="code-cell">fbc509aa35f9955b1939e8f398b7d37e</td><td class="info-cell">милосердие</td></tr>
            <tr><td>Каин</td><td class="code-cell">ac6bb94dc93ff03670242dcf0790d53d</td><td class="info-cell">милосердие</td></tr>

            <tr class="story-header"><td colspan="3">Секрет Небес 2</td></tr>
            <tr><td>Голод</td><td class="code-cell">b1af411532cdba680e5a35e18a39a4d7</td><td></td></tr>
            <tr><td>Люцифер</td><td class="code-cell">5691325191392ca26f8098be0819b783</td><td class="info-cell">концовка</td></tr>
            <tr><td>Астарот</td><td class="code-cell">8dd4fbc94766a9ef4314e2f960388e6f</td><td></td></tr>
            <tr><td>Мальбонте</td><td class="code-cell">bf5acee0a34afd508f6f10d96904bcd5</td><td class="info-cell">без равновесия</td></tr>
            <tr><td>Мими</td><td class="code-cell">--</td><td></td></tr>
            <tr><td>Война</td><td class="code-cell">cb907d487948233617f4b61c2d5c985a</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Секрет небес 3</td></tr>
            <tr><td>Война+Грег+Кас</td><td class="code-cell">7a433600d30678e35c6cfde3d3c752e9</td><td class="info-cell">милосердие, тьма</td></tr>
            <tr><td>Люц+Грег+Кас</td><td class="code-cell">d5acbc5eb7ee4173109afdbd7ab5a24c</td><td class="info-cell">милосердие, тьма</td></tr>
            <tr><td>Маль+Каин+Мика</td><td class="code-cell">1f82e3e2cb055a7b87bf449e4f2b6d8e</td><td class="info-cell">милосердие, тьма</td></tr>
            <tr><td>Астарот+Дима+Давид</td><td class="code-cell">--</td><td class="info-cell">не пройден</td></tr>

            <tr class="story-header"><td colspan="3">Сердце Треспии</td></tr>
            <tr><td>Рейнхольд</td><td class="code-cell">a5e2ba6722aa3fe934a4b14a0a0aafd1</td><td class="info-cell">рациональность</td></tr>

            <tr class="story-header"><td colspan="3">Там, где любовь горит вечно</td></tr>
            <tr><td>Граф/Мессир</td><td class="code-cell">05362d9356139f6d50ddbc29585f5cdc</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Тени Сентфора</td></tr>
            <tr><td>Вишня</td><td class="code-cell">f50408871d7f1ca307939bcfc177aab0</td><td></td></tr>
            <tr><td>Майкл</td><td class="code-cell">b1c0024ca68aa77be6c6586a28cad08f</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Теодора</td></tr>
            <tr><td>Лоуренс</td><td class="code-cell">ffe028bef20345275bf7db646331a4f7</td><td class="info-cell">дед + Дариус</td></tr>
            <tr><td>Фридрих+Джон</td><td class="code-cell">3955bc8eecf8442602bc09d908c2ed9c</td><td class="info-cell">начало 3 сезона</td></tr>

            <tr class="story-header"><td colspan="3">Цветок из огня Тиамат</td></tr>
            <tr><td>Ниалл</td><td class="code-cell">5dacddb30e3015a5475df5d6f6b3774c</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Шифр Шекспира</td></tr>
            <tr><td>Эдвард</td><td class="code-cell">7ce633d7d01a54b4caa4557e1600fbcc</td><td class="info-cell">без греха</td></tr>
            <tr><td>Эдмунд</td><td class="code-cell">df0f71ee75e866439ea95692d8c6729b</td><td class="info-cell">грех Реджины</td></tr>
            <tr><td>Хобелло</td><td class="code-cell">a8504347c17547f2f47ca047dd3d927e</td><td class="info-cell">без греха</td></tr>
            <tr><td>Ральф</td><td class="code-cell">bb76420474a8f2c702610505ba99de5f</td><td class="info-cell">без греха</td></tr>

            <tr class="story-header"><td colspan="3">Эдемов Сад</td></tr>
            <tr><td>Одиночка</td><td class="code-cell">1b196faa0f4649e8b3c98f50eace2b90</td><td class="info-cell">1 сезон 8 серия</td></tr>
            <tr><td>Минхёк</td><td class="code-cell">4f03e11a86304a1fd884dfb12c7d827d</td><td></td></tr>
            <tr><td>Кас</td><td class="code-cell">f1ad1c34f9ecdf9f19f731e409c0d5dd</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Я Охочусь на Тебя 2</td></tr>
            <tr><td>Эзра</td><td class="code-cell">9e61e9fd7a31c6a938a427b0c934f926</td><td></td></tr>

            <tr class="story-header"><td colspan="3">Ярость Титанов</td></tr>
            <tr><td>Мёрфи</td><td class="code-cell">a6e9c1b40abb0d1f7e7fda9f8d9cb026</td><td></td></tr>
        </tbody>
    </table>
</div>

</body>
</html>
