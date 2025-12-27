# studious-garbanzo
bot Highrise 
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🎭 Анимационный Бот Highrise</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
            color: white;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            min-height: 100vh;
            padding: 15px;
        }
        
        .container {
            max-width: 500px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5);
            border: 1px solid rgba(255, 255, 255, 0.1);
            position: relative;
            overflow: hidden;
        }
        
        .bot-header {
            text-align: center;
            margin-bottom: 30px;
            position: relative;
            padding-bottom: 20px;
            border-bottom: 2px solid rgba(255, 255, 255, 0.1);
        }
        
        .bot-avatar {
            width: 120px;
            height: 120px;
            background: linear-gradient(45deg, #FF416C, #FF4B2B);
            border-radius: 50%;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 50px;
            animation: pulse 2s infinite;
            box-shadow: 0 0 30px rgba(255, 65, 108, 0.5);
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        h1 {
            font-size: 28px;
            margin-bottom: 10px;
            background: linear-gradient(90deg, #FF416C, #FF4B2B);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 2px 10px rgba(255, 65, 108, 0.3);
        }
        
        .instructions {
            background: rgba(255, 255, 255, 0.08);
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 25px;
            border-left: 4px solid #FF416C;
        }
        
        .instructions h3 {
            color: #FFD166;
            margin-bottom: 10px;
            font-size: 18px;
        }
        
        .instructions ol {
            padding-left: 20px;
            line-height: 1.6;
        }
        
        .instructions li {
            margin-bottom: 8px;
        }
        
        .input-section {
            background: rgba(0, 0, 0, 0.3);
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 25px;
            text-align: center;
        }
        
        .number-input {
            width: 100%;
            padding: 18px;
            margin: 15px 0;
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid rgba(255, 255, 255, 0.2);
            border-radius: 12px;
            color: white;
            font-size: 22px;
            text-align: center;
            outline: none;
            transition: all 0.3s;
            font-weight: bold;
        }
        
        .number-input:focus {
            border-color: #FF416C;
            box-shadow: 0 0 20px rgba(255, 65, 108, 0.5);
            transform: translateY(-2px);
        }
        
        .btn {
            width: 100%;
            padding: 18px;
            background: linear-gradient(90deg, #FF416C, #FF4B2B);
            border: none;
            border-radius: 12px;
            color: white;
            font-size: 20px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            margin: 10px 0;
            letter-spacing: 1px;
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(255, 65, 108, 0.4);
        }
        
        .result {
            background: rgba(0, 0, 0, 0.4);
            padding: 25px;
            border-radius: 15px;
            margin-top: 20px;
            display: none;
            animation: slideUp 0.5s ease-out;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        @keyframes slideUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .animation-preview {
            text-align: center;
            margin: 20px 0;
        }
        
        .preview-box {
            width: 200px;
            height: 200px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 60px;
            animation: previewAnim 2s infinite alternate;
            border: 2px solid rgba(255, 255, 255, 0.1);
        }
        
        @keyframes previewAnim {
            0% { transform: scale(1) rotate(0deg); }
            50% { transform: scale(1.05) rotate(5deg); }
            100% { transform: scale(1) rotate(0deg); }
        }
        
        .animation-name {
            font-size: 26px;
            font-weight: bold;
            color: #FFD166;
            margin: 15px 0;
            text-align: center;
        }
        
        .animation-info {
            display: flex;
            justify-content: space-between;
            background: rgba(255, 255, 255, 0.05);
            padding: 15px;
            border-radius: 10px;
            margin: 15px 0;
            flex-wrap: wrap;
        }
        
        .info-item {
            flex: 1;
            min-width: 150px;
            text-align: center;
            padding: 10px;
        }
        
        .info-label {
            font-size: 14px;
            color: #aaa;
            margin-bottom: 5px;
        }
        
        .info-value {
            font-size: 18px;
            font-weight: bold;
            color: #FF416C;
        }
        
        .notification {
            background: rgba(0, 255, 0, 0.1);
            border: 1px solid rgba(0, 255, 0, 0.3);
            padding: 15px;
            border-radius: 10px;
            margin: 15px 0;
            text-align: center;
            display: none;
        }
        
        .error {
            background: rgba(255, 0, 0, 0.1);
            border: 1px solid rgba(255, 0, 0, 0.3);
            padding: 15px;
            border-radius: 10px;
            margin: 15px 0;
            text-align: center;
            display: none;
        }
        
        .quick-numbers {
            display: grid;
            grid-template-columns: repeat(10, 1fr);
            gap: 8px;
            margin-top: 25px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.03);
            border-radius: 15px;
        }
        
        .number-btn {
            width: 40px;
            height: 40px;
            background: rgba(255, 255, 255, 0.08);
            border: none;
            border-radius: 8px;
            color: white;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.2s;
            margin: 0 auto;
        }
        
        .number-btn:hover {
            background: rgba(255, 65, 108, 0.5);
            transform: scale(1.1);
        }
        
        .number-btn.active {
            background: #FF416C;
            box-shadow: 0 0 10px rgba(255, 65, 108, 0.5);
        }
        
        .copy-btn {
            background: linear-gradient(90deg, #11998e, #38ef7d);
            border: none;
            border-radius: 8px;
            color: white;
            padding: 10px 20px;
            cursor: pointer;
            margin: 10px 5px;
            transition: all 0.3s;
        }
        
        .copy-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(17, 153, 142, 0.4);
        }
        
        .action-buttons {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 20px;
        }
        
        @media (max-width: 600px) {
            .container {
                padding: 15px;
            }
            .quick-numbers {
                grid-template-columns: repeat(5, 1fr);
            }
            .info-item {
                min-width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="bot-header">
            <div class="bot-avatar">🤖</div>
            <h1>Анимационный Бот</h1>
            <p>Выберите число от 1 до 100 для анимации</p>
        </div>
        
        <div class="instructions">
            <h3>🎯 Как работает бот:</h3>
            <ol>
                <li>Введите число от 1 до 100 в поле ниже</li>
                <li>Нажмите "Показать анимацию"</li>
                <li>Бот покажет анимацию на себе (превью)</li>
                <li>Создатель комнаты увидит число и включит вам анимацию</li>
            </ol>
        </div>
        
        <div class="input-section">
            <input type="number" 
                   class="number-input" 
                   id="animationNumber" 
                   placeholder="Введите число от 1 до 100" 
                   min="1" 
                   max="100">
            
            <button class="btn" onclick="showAnimation()">
                🎬 Показать анимацию
            </button>
        </div>
        
        <div class="error" id="errorMessage">
            ❌ Пожалуйста, введите число от 1 до 100!
        </div>
        
        <div class="notification" id="copyNotification">
            ✅ Название анимации скопировано в буфер обмена!
        </div>
        
        <div class="result" id="animationResult">
            <div class="animation-preview">
                <div class="preview-box" id="previewEmoji">
                    👻
                </div>
            </div>
            
            <div class="animation-name" id="animationTitle">
                Ghost
            </div>
            
            <div class="animation-info">
                <div class="info-item">
                    <div class="info-label">Номер:</div>
                    <div class="info-value" id="infoNumber">1</div>
                </div>
                <div class="info-item">
                    <div class="info-label">Тип:</div>
                    <div class="info-value" id="infoType">Emote</div>
                </div>
                <div class="info-item">
                    <div class="info-label">Статус:</div>
                    <div class="info-value" id="infoStatus">Готово</div>
                </div>
            </div>
            
            <div style="text-align: center; margin: 20px 0;">
                <p>📍 <strong>Создатель комнаты увидел ваш выбор!</strong></p>
                <p>Ожидайте, когда вам включат эту анимацию в игре.</p>
            </div>
            
            <div class="action-buttons">
                <button class="copy-btn" onclick="copyAnimationName()">
                    📋 Скопировать название
                </button>
                <button class="copy-btn" onclick="shareAnimation()">
                    🔗 Поделиться
                </button>
                <button class="copy-btn" onclick="openInGame()">
                    🎮 Открыть в игре
                </button>
            </div>
        </div>
        
        <div style="margin: 25px 0; text-align: center;">
            <h3>⚡ Быстрый выбор:</h3>
            <div class="quick-numbers" id="numbersGrid">
                <!-- Числа от 1 до 100 будут сгенерированы -->
            </div>
        </div>
    </div>

    <script>
        // Массив анимаций с вашими ссылками
        const animations = {
            1: { name: "Floor Sleeping", emoji: "😴", type: "Idle", url: "https://high.rs/item?id=idle-floorsleeping&type=emote" },
            2: { name: "Ghost", emoji: "👻", type: "Emote", url: "https://high.rs/item?id=emote-ghost-idle&type=emote" },
            3: { name: "Twerk", emoji: "💃", type: "Dance", url: "https://high.rs/item?id=dance-twerk&type=emote" },
            4: { name: "Sit Cute", emoji: "🐱", type: "Sit", url: "https://high.rs/item?id=sit-idle-cute&type=emote" },
            5: { name: "Woah Dance", emoji: "🤯", type: "Dance", url: "https://high.rs/item?id=dance-woah&type=emote" },
            6: { name: "Heart Eyes", emoji: "😍", type: "Emote", url: "https://high.rs/item?id=emote-hearteyes&type=emote" },
            7: { name: "Naughty", emoji: "😏", type: "Emoji", url: "https://high.rs/item?id=emoji-naughty&type=emote" },
            8: { name: "Laying Down 2", emoji: "😪", type: "Idle", url: "https://high.rs/item?id=idle_layingdown2&type=emote" },
            9: { name: "TikTok Dance 4", emoji: "📱", type: "Idle", url: "https://high.rs/item?id=idle-dance-tiktok4&type=emote" },
            10: { name: "Enthusiastic", emoji: "🤩", type: "Idle", url: "https://high.rs/item?id=idle-enthusiastic&type=emote" },
            11: { name: "TikTok Dance 9", emoji: "💫", type: "Dance", url: "https://high.rs/item?id=dance-tiktok9&type=emote" },
            12: { name: "Space", emoji: "🚀", type: "Idle", url: "https://high.rs/item?id=idle-space&type=emote" },
            13: { name: "UwU", emoji: "🌸", type: "Idle", url: "https://high.rs/item?id=idle-uwu&type=emote" },
            14: { name: "Stargazer", emoji: "✨", type: "Emote", url: "https://high.rs/item?id=emote-stargazer&type=emote" },
            15: { name: "Hands Up Dance", emoji: "🙌", type: "Dance", url: "https://high.rs/item?id=dance-handsup&type=emote" },
            16: { name: "Angry", emoji: "😠", type: "Idle", url: "https://high.rs/item?id=idle-angry&type=emote" },
            17: { name: "Floor Sleeping 2", emoji: "💤", type: "Idle", url: "https://high.rs/item?id=idle-floorsleeping2&type=emote" },
            18: { name: "Shy 2", emoji: "😳", type: "Emote", url: "https://high.rs/item?id=emote-shy2&type=emote" },
            19: { name: "Employee Dance", emoji: "💼", type: "Dance", url: "https://high.rs/item?id=dance-employee&type=emote" },
            20: { name: "Posh", emoji: "👑", type: "Idle", url: "https://high.rs/item?id=idle-posh&type=emote" },
            // Добавьте остальные анимации аналогично
            100: { name: "Elbow Bump", emoji: "👊", type: "Emote", url: "https://high.rs/item?id=emote-elbowbump&type=emote" }
        };

        // Заполняем оставшиеся анимации
        for (let i = 21; i < 100; i++) {
            if (!animations[i]) {
                animations[i] = {
                    name: `Анимация ${i}`,
                    emoji: getRandomEmoji(),
                    type: ["Emote", "Dance", "Idle", "Sit", "Emoji"][Math.floor(Math.random() * 5)],
                    url: "#"
                };
            }
        }

        function getRandomEmoji() {
            const emojis = ["🎭", "💃", "🕺", "🌟", "✨", "🎵", "🎶", "🔥", "💫", "🎪", "👯", "🌈"];
            return emojis[Math.floor(Math.random() * emojis.length)];
        }

        let selectedNumber = null;

        // Заполняем сетку чисел
        function generateNumbersGrid() {
            const grid = document.getElementById('numbersGrid');
            for (let i = 1; i <= 100; i++) {
                const btn = document.createElement('button');
                btn.className = 'number-btn';
                btn.textContent = i;
                btn.onclick = () => selectNumber(i, btn);
                grid.appendChild(btn);
            }
        }

        function selectNumber(number, element) {
            selectedNumber = number;
            document.getElementById('animationNumber').value = number;
            
            // Убираем активный класс у всех кнопок
            document.querySelectorAll('.number-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            
            // Добавляем активный класс выбранной кнопке
            element.classList.add('active');
            
            // Показываем анимацию
            showAnimation();
        }

        function showAnimation() {
            const input = document.getElementById('animationNumber');
            const number = parseInt(input.value);
            const error = document.getElementById('errorMessage');
            const result = document.getElementById('animationResult');
            
            // Скрываем сообщения
            error.style.display = 'none';
            
            // Проверяем валидность
            if (isNaN(number) || number < 1 || number > 100) {
                error.style.display = 'block';
                return;
            }
            
            // Получаем данные анимации
            const anim = animations[number];
            
            // Заполняем данные
            document.getElementById('previewEmoji').textContent = anim.emoji;
            document.getElementById('animationTitle').textContent = `${number}. ${anim.name}`;
            document.getElementById('infoNumber').textContent = number;
            document.getElementById('infoType').textContent = anim.type;
            document.getElementById('infoStatus').textContent = "Ожидание";
            
            // Анимируем превью
            const previewBox = document.getElementById('previewEmoji');
            previewBox.style.animation = 'none';
            setTimeout(() => {
                previewBox.style.animation = 'previewAnim 2s infinite alternate';
            }, 10);
            
            // Показываем результат
            result.style.display = 'block';
            
            // Прокрутка к результату
            result.scrollIntoView({ behavior: 'smooth' });
            
            // Имитируем загрузку
            setTimeout(() => {
                document.getElementById('infoStatus').textContent = "Готово";
                document.getElementById('infoStatus').style.color = "#4CAF50";
            }, 1000);
            
            // Отправляем "сигнал" создателю комнаты (в реальности здесь был бы запрос к серверу)
            sendSignalToOwner(number, anim.name);
        }

        function sendSignalToOwner(number, animName) {
            // В реальном приложении здесь был бы AJAX запрос к вашему серверу
            console.log(`Игрок выбрал анимацию: ${number} - ${animName}`);
            
            // Создаем визуальный эффект "отправки"
            const status = document.getElementById('infoStatus');
            status.textContent = "Отправка...";
            
            setTimeout(() => {
                status.textContent = "Отправлено создателю!";
                status.style.color = "#2196F3";
                
                // Показываем уведомление для пользователя
                showNotification(`✅ Запрос на анимацию ${animName} отправлен!`);
            }, 1500);
        }

        function showNotification(message) {
            // Здесь можно добавить уведомление в интерфейс
            console.log(message);
        }

        function copyAnimationName() {
            const title = document.getElementById('animationTitle').textContent;
            const number = document.getElementById('animationNumber').value;
            const anim = animations[number];
            
            const text = `🎭 Анимация: ${anim.name} (№${number})\n✨ Тип: ${anim.type}\n🔗 Ссылка: ${anim.url}`;
            
            // Копирование в буфер обмена
            navigator.clipboard.writeText(text).then(() => {
                const notification = document.getElementById('copyNotification');
                notification.style.display = 'block';
                setTimeout(() => {
                    notification.style.displ
