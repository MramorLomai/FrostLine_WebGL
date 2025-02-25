
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FrostLine</title>
    <style>
        body {
            background-color: #121212;
            color: #e0e0e0;
            font-family: 'Segoe UI', Arial, sans-serif;
            margin: 0;
            min-height: 100vh;
            position: relative;
            overflow-x: hidden;
            padding: 20px;
            line-height: 1.6;
            max-width: 1200px;
            margin: 0 auto;
        }
        .content-container {
            position: relative;
            z-index: 1;
            background-color: rgba(18, 18, 18, 0.9);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(5px);
        }
        .clickable-image {
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            border: 2px solid #4169E1;
            border-radius: 10px;
            max-width: 100%;
            height: auto;
            display: block;
            margin: 20px auto;
        }
        .clickable-image:hover {
            transform: scale(1.02) translateY(-2px);
            box-shadow: 0 4px 15px rgba(65, 105, 225, 0.4);
        }
        .image-modal {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 90%;
            max-width: 800px;
            background-color: rgba(0, 0, 0, 0.95);
            padding: 20px;
            border-radius: 15px;
            z-index: 1001;
            text-align: center;
            overflow: hidden;
        }
        .image-modal img {
            max-width: 100%;
            max-height: 80vh;
            border-radius: 10px;
            border: 2px solid #4169E1;
            transition: transform 0.3s ease;
        }
        .image-modal.open img {
            transform: scale(1.35); /* Увеличение изображения на 35% */
        }
        .close {
            position: absolute;
            top: 10px;
            right: 20px;
            color: white;
            font-size: 30px;
            cursor: pointer;
            z-index: 1002;
        }
        .close:hover {
            color: #ccc;
        }
        .snowflake {
            position: fixed;
            width: 10px;
            height: 10px;
            background: white;
            border-radius: 50%;
            pointer-events: none;
            z-index: 9999;
            filter: blur(1px);
            top: 0;
            animation: snowfall linear infinite;
        }
        .easter-egg-button {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 40px;
            height: 40px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            cursor: pointer;
            z-index: 1000;
            border: 2px solid #4169E1;
            transition: all 0.3s ease;
        }
        .easter-egg-button:hover {
            background-color: rgba(65, 105, 225, 0.3);
            transform: scale(1.1);
        }
        .easter-egg-button::after {
            content: "❄️";
            position: absolute;
            font-size: 20px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
        @keyframes snowfall {
            0% {
                transform: translateY(0vh) translateX(0) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) translateX(20vw) rotate(360deg);
                opacity: 0.3;
            }
        }
        @media (max-width: 768px) {
            body {
                padding: 10px;
            }
            .content-container {
                padding: 15px;
            }
            h1 {
                font-size: 2em;
            }
        }
    </style>
</head>
<body>
    <div class="content-container">
        <h1>WebGL версия игры <strong>FrostLine</strong> (Сделано в Unity3D)</h1>
        <blockquote>
            <p>Сделано Александром Дробовым (code) и Владимиром Кругляковым (art)</p>
        </blockquote>
        <p>Можно сыграть перейдя по этой ссылке: <a href="https://clck.ru/3GM46t">FrostLine GitHub</a></p>
        <p>Itch.io версия: <a href="https://mramorlomai.itch.io/frostline">FrostLine Itch.io</a></p>
        <p>Ну или если ты хочешь скачать standalone версию на windows/<s>linux</s>: <a href="https://disk.yandex.ru/d/E8916kl56iHSUw">FrostLine PC</a></p>
        <p><strong>FrostLine</strong> — это динамичный арена-шутер на выживание от первого лица, действие которого разворачивается в зимнем средневековом сеттинге. Вам предстоит взять на себя роль рыцаря и защитить крепость от орд врагов. Игра сочетает в себе элементы классических шутеров, таких как <strong>Quake, Ultrakill, Doom и Half-Life</strong>.</p>
        <img src="https://github.com/user-attachments/assets/3db32614-dff6-4eca-acd0-79268bc0a492" 
             alt="FrostLinePoster" 
             class="clickable-image" />
        <h2>Управление:</h2>
        <ul>
            <li>Ходьба - "WASD"/Стрелки</li>
            <li>Приседание/Быстрое приземление - "Ctrl"</li>
            <li>Атака - "Mouse0"</li>
            <li>Перезарядка - "R" / Авто перезарядка</li>
            <li>Рывок - "Mouse1"</li>
            <li>Мясной крюк - "F"</li>
            <li>Slow-mo - "Q"</li>
            <li>Прыжок - "Space"</li>
            <li>Двойной прыжок - 2x "Space"</li>
            <li>Бег - "Shift"</li>
            <li>Смена оружия - "MouseWhl"/ Цифры</li>
            <li>Пауза - "Escape"</li>
            <li>Консоль разработчика - "~"</li>
        </ul>
        <p><strong>P.S.</strong> (Linux больше не поддерживается)</p>
        <!-- Модальное окно для изображений -->
        <div id="imageModal" class="image-modal">
            <span class="close">&times;</span>
            <img id="modalImage" src="" alt="Увеличенное изображение" />
        </div>
        <!-- Кнопка для пасхалки -->
        <div id="easterEggButton" class="easter-egg-button"></div>
        <!-- Модальное окно для пасхалки -->
        <div id="easterEggModal" class="image-modal">
            <span class="close">&times;</span>
            <img id="easterEggImage" src="" alt="Пасхалка" />
        </div>
    </div>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // Инициализация модального окна для изображений
            const imageModal = document.getElementById('imageModal');
            const modalImage = document.getElementById('modalImage');
            const closeButtons = document.querySelectorAll('.close');

            // Обработчики для всех кликабельных изображений
            document.querySelectorAll('.clickable-image').forEach(img => {
                img.addEventListener('click', () => {
                    modalImage.src = img.src;
                    imageModal.style.display = 'block';
                    imageModal.classList.add('open'); // Добавляем класс для увеличения изображения
                });
            });

            // Инициализация пасхалки
            const easterEggImages = [
                "https://github.com/user-attachments/assets/bdd53968-57fc-43e7-b121-f0690855bff6",
                "https://github.com/user-attachments/assets/2de2e4af-76ef-47b9-bfe2-dc344c995a9b",
                "https://github.com/user-attachments/assets/2f02bba7-83b3-4b60-b6bf-c374afd0e829"
            ];
            const easterEggButton = document.getElementById('easterEggButton');
            const easterEggModal = document.getElementById('easterEggModal');
            const easterEggImage = document.getElementById('easterEggImage');

            // Обработчик для кнопки пасхалки
            easterEggButton.addEventListener('click', (e) => {
                e.stopPropagation();
                const randomIndex = Math.floor(Math.random() * easterEggImages.length);
                easterEggImage.src = easterEggImages[randomIndex];
                easterEggModal.style.display = 'block';
                easterEggModal.classList.add('open'); // Добавляем класс для увеличения изображения
            });

            // Общий обработчик закрытия для всех модальных окон
            closeButtons.forEach(btn => {
                btn.addEventListener('click', () => {
                    imageModal.style.display = 'none';
                    easterEggModal.style.display = 'none';
                    imageModal.classList.remove('open'); // Убираем класс для уменьшения изображения
                    easterEggModal.classList.remove('open'); // Убираем класс для уменьшения изображения
                });
            });

            // Закрытие по клику вне окна
            window.addEventListener('click', (event) => {
                if (event.target === imageModal || event.target === easterEggModal) {
                    imageModal.style.display = 'none';
                    easterEggModal.style.display = 'none';
                    imageModal.classList.remove('open'); // Убираем класс для уменьшения изображения
                    easterEggModal.classList.remove('open'); // Убираем класс для уменьшения изображения
                }
            });

            // Обработчик ошибок для изображений
            modalImage.onerror = easterEggImage.onerror = function() {
                console.error("Ошибка загрузки изображения:", this.src);
                this.parentElement.style.display = 'none';
            };

            // Создание снежинок
            function createSnowflake() {
                const snowflake = document.createElement('div');
                snowflake.classList.add('snowflake');
                snowflake.style.left = Math.random() * 100 + 'vw';
                snowflake.style.opacity = Math.random() * 0.6 + 0.3;
                const size = Math.random() * 8 + 4;
                snowflake.style.width = size + 'px';
                snowflake.style.height = size + 'px';
                const duration = Math.random() * 3 + 5;
                snowflake.style.animation = `snowfall ${duration}s linear infinite`;
                document.body.appendChild(snowflake);
                setTimeout(() => snowflake.remove(), duration * 1000 + 1000);
            }

            // Интервал создания снежинок
            const isMobile = /Mobi|Android/i.test(navigator.userAgent);
            setInterval(createSnowflake, isMobile ? 150 : 80);
        });
    </script>
</body>
</html>