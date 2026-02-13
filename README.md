<!DOCTYPE html>
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
            <tr><td>Веспер</td><td><span class="code-text">eff25e263104797a0fb1796ff4771f4e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">луна, статус</td></tr>

            <tr class="story-row"><td colspan="3">Te Amo (1 и 2 тома)</td></tr>
            <tr><td>Майкл (1т)</td><td><span class="code-text">d82650d204cd6817204797033fca7e00</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">восприятие</td></tr>
            <tr><td>Мэт (2т)</td><td><span class="code-text">cf48199c00acd80a0a96ad72fe8544dc</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">рассуждение</td></tr>

            <tr class="story-row"><td colspan="3">7 братьев / Авверис</td></tr>
            <tr><td>Грант</td><td><span class="code-text">2437db5000468bea11082a9c22c91297</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">капитализм</td></tr>
            <tr><td>Аш</td><td><span class="code-text">365a71d10df45dbc2368135630db129c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">аномалия</td></tr>

            <tr class="story-row"><td colspan="3">Арканум</td></tr>
            <tr><td>Лиам</td><td><span class="code-text">c050f3a89e9130f3b7eeb90a8f63c8aa</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">жрица, искупление</td></tr>

            <tr class="story-row"><td colspan="3">Бездушная</td></tr>
            <tr><td>Винсент</td><td><span class="code-text">64c35738c74fa1c47a6bb77c8d037694</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс</td></tr>

            <tr class="story-row"><td colspan="3">Дракула: История любви</td></tr>
            <tr><td>Ноэ</td><td><span class="code-text">5544e1ef9352878265d67cb8b4f1035d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">баланс, 3с</td></tr>

            <tr class="story-row"><td colspan="3">Кали (Зов Тьмы / Пламя Сансары)</td></tr>
            <tr><td>Рейтан</td><td><span class="code-text">6d3b4356a3b5816ccbc5f5c95715a6d9</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">гнев, 5с</td></tr>
            <tr><td>Амрит</td><td><span class="code-text">1520ec77e59ed379751d2f150f50a736</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милость</td></tr>
            <tr><td>Рам</td><td><span class="code-text">ab3f19bcfa164fc1b641231b631540f8</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наследие</td></tr>

            <tr class="story-row"><td colspan="3">Песнь о Красном Ниле</td></tr>
            <tr><td>Ливий</td><td><span class="code-text">d13d0007af972568f876507cf9af10a2</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность, некро</td></tr>
            <tr><td>Амен</td><td><span class="code-text">6cd61d7df682189d9911cadaf85c5482</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">честность, эпистат</td></tr>

            <tr class="story-row"><td colspan="3">Секрет Небес (2 / Реквием)</td></tr>
            <tr><td>Люцифер</td><td><span class="code-text">5691325191392ca26f8098be0819b783</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">темперамент</td></tr>
            <tr><td>Каин</td><td><span class="code-text">ac6bb94dc93ff03670242dcf0790d53d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">милосердие</td></tr>

            <tr class="story-row"><td colspan="3">Пси Ψ</td></tr>
            <tr><td>Иво</td><td><span class="code-text">2cdd74cc1251b961aba59029430d775c</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">импульс, вектор</td></tr>
            <tr><td>Кей</td><td><span class="code-text">461e14bc97ecaca8f773b2113157c10</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">контроль</td></tr>

            <tr class="story-row"><td colspan="3">Ярость Титанов / Цветок из Огня Тиамат</td></tr>
            <tr><td>Мёрфи</td><td><span class="code-text">a6e9c1b40abb0d1f7e7fda9f8d9cb026</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">божественность</td></tr>
            <tr><td>Кингу</td><td><span class="code-text">fbc109aa35f9955b1939e8f398b7d37e</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">меч, огонь</td></tr>

            <tr class="story-row"><td colspan="3">Классика (ЯОНТ, РЛ, ВРС, ЛСЗ, ПВ)</td></tr>
            <tr><td>Сэм (ЯОНТ)</td><td><span class="code-text">ea9c827a062eb5c3bb6fff106c738d85</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">логика</td></tr>
            <tr><td>Виктор (РЛ)</td><td><span class="code-text">d41a63c32d7f28afda433d45cff32ea1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">дар луны</td></tr>
            <tr><td>Брэндон (ВРС)</td><td><span class="code-text">8871a06e74362c9da48a0724eb5eb037</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">мастерство</td></tr>
            <tr><td>Рэй (ЛСЗ)</td><td><span class="code-text">1a5d43b5329e3d65a596c04f241bcbd1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">наука</td></tr>
            <tr><td>Улль (ПВ)</td><td><span class="code-text">27c1f8a44d8b928f615e42c492114ad1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">перемены</td></tr>

            <tr class="story-row"><td colspan="3">Прочие (ХЛ, ЭС, ДЖС, ГЛ)</td></tr>
            <tr><td>Чанд (ХЛ)</td><td><span class="code-text">9e61e9fd7a31c6a938a427b0c934f926</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">прагматик</td></tr>
            <tr><td>Минхёк (ЭС)</td><td><span class="code-text">4f03e11a86304a1fd884dfb12c7d827d</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">амбиции</td></tr>
            <tr><td>Бенедикт (ДЖС)</td><td><span class="code-text">13acbd2204cd1817204797033fca7e01</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">тихоня</td></tr>
            <tr><td>Шерлок (ГЛ)</td><td><span class="code-text">c6b2d6fda60b786cbb61b7f6443163c1</span><button class="copy-btn" onclick="copy(this)">Копировать</button></td><td class="info-txt">алые тени</td></tr>
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
