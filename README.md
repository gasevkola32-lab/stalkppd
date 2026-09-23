<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>STALKER_NET | Мой Профиль Сталкера</title>
    <style>
        :root {
            --bg-color: #121612;
            --panel-color: #1a221a;
            --border-color: #384e38;
            --text-color: #adbead;
            --accent-color: #4af626;
            --accent-hover: #3cd01c;
            --danger-color: #ff3333;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            font-family: 'Courier New', Courier, monospace;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
        }

        .container {
            width: 100%;
            max-width: 800px;
            background-color: var(--panel-color);
            border: 2px solid var(--border-color);
            padding: 25px;
            box-shadow: 0 0 15px rgba(74, 246, 38, 0.1);
        }

        h1 {
            color: var(--accent-color);
            text-align: center;
            border-bottom: 2px dashed var(--border-color);
            padding-bottom: 10px;
            margin-top: 0;
            text-shadow: 0 0 5px rgba(74, 246, 38, 0.5);
        }

        h2 {
            color: var(--accent-color);
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 5px;
            margin-top: 25px;
        }

        .profile-info {
            margin-bottom: 20px;
            font-size: 1.1em;
        }

        .profile-info strong {
            color: var(--accent-color);
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        label .required {
            color: var(--danger-color);
        }

        input[type="text"], textarea, select {
            width: 100%;
            padding: 10px;
            background-color: var(--bg-color);
            border: 1px solid var(--border-color);
            color: var(--text-color);
            font-family: inherit;
            box-sizing: border-box;
            border-radius: 4px;
        }

        input[type="text"]:focus, textarea:focus, select:focus {
            outline: none;
            border-color: var(--accent-color);
            box-shadow: 0 0 5px rgba(74, 246, 38, 0.3);
        }

        .radio-group, .select-group {
            display: flex;
            flex-direction: column;
            gap: 8px;
            background-color: rgba(0,0,0,0.2);
            padding: 10px;
            border-radius: 4px;
            border: 1px solid rgba(56, 78, 56, 0.5);
        }

        .radio-label {
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
        }

        .btn {
            background-color: transparent;
            border: 1px solid var(--accent-color);
            color: var(--accent-color);
            padding: 10px 20px;
            font-family: inherit;
            font-size: 1em;
            cursor: pointer;
            transition: all 0.2s ease;
            border-radius: 4px;
        }

        .btn:hover {
            background-color: var(--accent-color);
            color: var(--bg-color);
            box-shadow: 0 0 10px var(--accent-color);
        }

        .btn-block {
            width: 100%;
            margin-top: 10px;
        }

        .actions-row {
            display: flex;
            gap: 15px;
            margin-top: 15px;
        }

        .tabs {
            display: flex;
            gap: 5px;
            margin-bottom: 15px;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 10px;
            flex-wrap: wrap;
        }

        .tab {
            background: none;
            border: 1px solid var(--border-color);
            color: var(--text-color);
            padding: 8px 12px;
            cursor: pointer;
            border-radius: 4px;
        }

        .tab.active {
            background-color: var(--border-color);
            color: var(--accent-color);
            font-weight: bold;
        }

        .object-list {
            min-height: 50px;
            padding: 10px;
            background-color: rgba(0,0,0,0.1);
            border: 1px dashed var(--border-color);
            border-radius: 4px;
        }

        .empty-message {
            text-align: center;
            font-style: italic;
            color: #6a7b6a;
            padding: 20px 0;
        }

        .object-item {
            background-color: rgba(56, 78, 56, 0.2);
            border: 1px solid var(--border-color);
            padding: 12px;
            margin-bottom: 10px;
            border-radius: 4px;
            position: relative;
        }

        .object-item h3 {
            margin: 0 0 5px 0;
            color: var(--accent-color);
        }

        .object-meta {
            font-size: 0.85em;
            color: #8fa08f;
            margin-bottom: 5px;
        }

        .object-notes {
            font-size: 0.95em;
            word-break: break-word;
        }
        
        .delete-btn {
            position: absolute;
            top: 10px;
            right: 10px;
            background: none;
            border: none;
            color: var(--danger-color);
            cursor: pointer;
            font-size: 1.2em;
        }
    </style>
</head>
<body>

<div class="container">
    <h1># STALKER_NET</h1>
    
    <div class="profile-info">
        Личный профиль: <strong>Исследователь</strong>
    </div>

    <h2>Добавить заброшку</h2>
    <form id="stalkerForm">
        <div class="form-group">
            <label for="objectName">Название объекта <span class="required">*</span></label>
            <input type="text" id="objectName" required placeholder="Например, Завод 'Юпитер'">
        </div>

        <div class="form-group">
            <label for="objectCoords">Локация / Координаты <span class="required">*</span></label>
            <input type="text" id="objectCoords" required placeholder="51.4069, 30.0583">
        </div>

        <div class="form-group">
            <label>Добавить в список <span class="required">*</span></label>
            <div class="radio-group">
                <label class="radio-label">
                    <input type="radio" name="listType" value="main" checked> 📍 Основной список
                </label>
                <label class="radio-label">
                    <input type="radio" name="listType" value="want"> ⭐ Хочу посетить
                </label>
                <label class="radio-label">
                    <input type="radio" name="listType" value="visited"> ✅ Уже исследовано
                </label>
            </div>
        </div>

        <div class="form-group">
            <label for="difficulty">Сложность доступа</label>
            <select id="difficulty">
                <option value="easy">Легко (Свободный вход)</option>
                <option value="medium">Средне (Забор / Охрана)</option>
                <option value="hard">Сложно (ЧОП / Камеры)</option>
            </select>
        </div>

        <div class="form-group">
            <label for="notes">Описание и заметки</label>
            <textarea id="notes" rows="4" placeholder="Состояние объекта, хабар, опасности..."></textarea>
        </div>

        <button type="submit" class="btn btn-block">Сохранить в профиль</button>
    </form>

    <div class="actions-row">
        <button id="exportBtn" class="btn">💾 Экспорт данных</button>
        <button id="importBtn" class="btn">📂 Импорт данных</button>
        <input type="file" id="fileInput" style="display: none;" accept=".json">
    </div>

    <h2>Мои сохраненные объекты</h2>
    
    <div class="tabs">
        <button class="tab active" data-filter="all">Все (<span id="count-all">0</span>)</button>
        <button class="tab" data-filter="main">Основной список (<span id="count-main">0</span>)</button>
        <button class="tab" data-filter="want">Хочу посетить (<span id="count-want">0</span>)</button>
        <button class="tab" data-filter="visited">Уже исследовано (<span id="count-visited">0</span>)</button>
    </div>

    <div id="objectList" class="object-list">
        <!-- Сюда будут динамически добавляться объекты -->
    </div>
</div>

<script>
    // Инициализация хранилища данных
    let stalkerData = JSON.parse(localStorage.getItem('stalker_net_data')) || [];
    let currentFilter = 'all';

    // Элементы DOM
    const form = document.getElementById('stalkerForm');
    const objectList = document.getElementById('objectList');
    const fileInput = document.getElementById('fileInput');
    const exportBtn = document.getElementById('exportBtn');
    const importBtn = document.getElementById('importBtn');

    // Функция сохранения в LocalStorage
    function saveData() {
        localStorage.setItem('stalker_net_data', JSON.stringify(stalkerData));
        updateUI();
    }

    // Отрисовка интерфейса и списков
    function updateUI() {
        // Подсчет количества элементов
        const counts = {
            all: stalkerData.length,
            main: stalkerData.filter(item => item.listType === 'main').length,
            want: stalkerData.filter(item => item.listType === 'want').length,
            visited: stalkerData.filter(item => item.listType === 'visited').length
        };

        // Обновление счетчиков в табах
        document.getElementById('count-all').textContent = counts.all;
        document.getElementById('count-main').textContent = counts.main;
        document.getElementById('count-want').textContent = counts.want;
        document.getElementById('count-visited').textContent = counts.visited;

        // Фильтрация объектов для отображения
        const filteredData = currentFilter === 'all' 
            ? stalkerData 
            : stalkerData.filter(item => item.listType === currentFilter);

        // Очистка списка
        objectList.innerHTML = '';

        if (filteredData.length === 0) {
            objectList.innerHTML = '<div class="empty-message">Список пуст. Добавьте свой первый объект выше!</div>';
            return;
        }

        // Вывод объектов
        filteredData.forEach((item, index) => {
            const itemEl = document.createElement('div');
            itemEl.className = 'object-item';
            
            const listIcons = { main: '📍', want: '⭐', visited: '✅' };
            const diffLabels = { easy: 'Легко', medium: 'Средне', hard: 'Сложно' };

            itemEl.innerHTML = `
                <button class="delete-btn" onclick="deleteObject(${index})">&times;</button>
                <h3>${listIcons[item.listType] || ''} ${escapeHTML(item.name)}</h3>
                <div class="object-meta">
                    <strong>Координаты:</strong> ${escapeHTML(item.coords)} | 
                    <strong>Доступ:</strong> ${diffLabels[item.difficulty] || item.difficulty}
                </div>
                ${item.notes ? `<div class="object-notes">${escapeHTML(item.notes).replace(/\n/g, '<br>')}</div>` : ''}
            `;
            objectList.appendChild(itemEl);
        });
    }

    // Хелпер для защиты от XSS
    function escapeHTML(str) {
        return str.replace(/[&<>'"]/g, 
            tag => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', "'": '&#39;', '"': '&quot;' }[tag] || tag)
        );
    }

    // Добавление нового объекта
    form.addEventListener('submit', function(e) {
        e.preventDefault();
        
        const newObject = {
            name: document.getElementById('objectName').value,
            coords: document.getElementById('objectCoords').value,
            listType: document.querySelector('input[name="listType"]:checked').value,
            difficulty: document.getElementById('difficulty').value,
            notes: document.getElementById('notes').value,
            id: Date.now()
        };

        stalkerData.push(newObject);
        saveData();
        form.reset();
    });

    // Удаление объекта
    window.deleteObject = function(index) {
        if(confirm('Удалить эту локацию из профиля?')) {
            // Если включен фильтр, нужно найти правильный id объекта в общем массиве
            if (currentFilter !== 'all') {
                const filtered = stalkerData.filter(item => item.listType === currentFilter);
                const targetId = filtered[index].id;
                stalkerData = stalkerData.filter(item => item.id !== targetId);
            } else {
                stalkerData.splice(index, 1);
            }
            saveData();
        }
    };

    // Переключение вкладок (фильтров)
    document.querySelectorAll('.tab').forEach(tab => {
        tab.addEventListener('click', function() {
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            this.classList.add('active');
            currentFilter = this.getAttribute('data-filter');
            updateUI();
        });
    });

    // Экспорт данных в JSON файл
    exportBtn.addEventListener('click', function() {
        if(stalkerData.length === 0) {
            alert('Нечего экспортировать. Список объектов пуст.');
            return;
        }
        const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(stalkerData, null, 2));
        const downloadAnchor = document.createElement('a');
        downloadAnchor.setAttribute("href", dataStr);
        downloadAnchor.setAttribute("download", "stalker_net_profile.json");
        document.body.appendChild(downloadAnchor);
        downloadAnchor.click();
        downloadAnchor.remove();
    });

    // Импорт данных из JSON файла
    importBtn.addEventListener('click', () => fileInput.click());
    
    fileInput.addEventListener('change', function(e) {
        const file = e.target.files[0];
        if (!file) return;

        const reader = new FileReader();
        reader.onload = function(e) {
            try {
                const imported = JSON.parse(e.target.result);
                if (Array.isArray(imported)) {
                    if(confirm(`Импортировать объектов: ${imported.length}? Текущие данные будут перезаписаны.`)) {
                        stalkerData = imported;
                        saveData();
                    }
                } else {
                    alert('Неверный формат файла. Ожидался массив объектов.');
                }
            } catch (err) {
                alert('Ошибка при чтении файла. Убедитесь, что это корректный JSON.');
            }
        };
        reader.readAsText(file);
        fileInput.value = ''; // сброс инпута
    });

    // Первичная отрисовка при загрузке страницы
    updateUI();
</script>

</body>
</html>
