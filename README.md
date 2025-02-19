<!DOCTYPE html>
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

        a {
            color: #6A9CFF;
            text-decoration: none;
            transition: color 0.3s ease;
            position: relative;
            padding: 2px 4px;
        }

        a:hover {
            color: #1E90FF;
            text-decoration: underline;
        }

        h1, h2, h3, h4, h5, h6 {
            color: #ffffff;
            margin-top: 1.5em;
            margin-bottom: 0.8em;
        }

        h1 {
            font-size: 2.5em;
            text-align: center;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }

        blockquote {
            border-left: 4px solid #4682B4;
            padding: 15px;
            margin: 20px 0;
            background: rgba(70, 130, 180, 0.1);
            border-radius: 0 5px 5px 0;
        }

        img {
            border: 2px solid #4169E1;
            border-radius: 10px;
            max-width: 100%;
            height: auto;
            display: block;
            margin: 20px auto;
            transition: transform 0.3s ease;
        }

        img:hover {
            transform: scale(1.02);
        }

        .controls {
            background: rgba(255, 255, 255, 0.05);
            padding: 20px;
            border-radius: 10px;
            margin: 20px 0;
        }

        .controls ul {
            list-style-type: none;
            padding: 0;
        }

        .controls li {
            padding: 8px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .controls li:last-child {
            border-bottom: none;
        }

        .easter-egg-button {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 50px;
            height: 50px;
            background-color: transparent;
            cursor: pointer;
            z-index: 1000;
        }

        .easter-egg-modal {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 80%;
            max-width: 600px;
            background-color: rgba(0, 0, 0, 0.9);
            padding: 20px;
            border-radius: 10px;
            z-index: 1001;
            text-align: center;
        }

        .easter-egg-modal img {
            max-width: 100%;
            height: auto;
            border-radius: 10px;
        }

        .close {
            position: absolute;
            top: 10px;
            right: 20px;
            color: white;
            font-size: 30px;
            cursor: pointer;
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
        <img src="https://github.com/user-attachments/assets/3db32614-dff6-4eca-acd0-79268bc0a492" alt="FrostLinePoster" />
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

        <!-- Скрытая кнопка для пасхалки -->
        <div id="easterEggButton" class="easter-egg-button"></div>

        <!-- Модальное окно для отображения изображения -->
        <div id="easterEggModal" class="easter-egg-modal">
            <span class="close">&times;</span>
            <img id="easterEggImage" src="" alt="Пасхалка" />
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // Список изображений для пасхалки
            const easterEggImages = [
                "https://i.imgur.com/8N0ykm8.png",
                "https://i.imgur.com/6g0kaiq.png",
                "https://i.imgur.com/ZkaUeF9.png"
            ];

            // Получаем элементы
            const easterEggButton = document.getElementById('easterEggButton');
            const easterEggModal = document.getElementById('easterEggModal');
            const easterEggImage = document.getElementById('easterEggImage');
            const closeModal = document.querySelector('.close');

            // Функция для открытия случайного изображения
            function openRandomImage() {
                const randomIndex = Math.floor(Math.random() * easterEggImages.length);
                easterEggImage.src = easterEggImages[randomIndex];
                easterEggModal.style.display = 'block';
            }

            // Обработчик для кнопки
            easterEggButton.addEventListener('click', openRandomImage);

            // Закрытие модального окна
            closeModal.addEventListener('click', () => {
                easterEggModal.style.display = 'none';
            });

            // Закрытие модального окна при клике вне его
            window.addEventListener('click', (event) => {
                if (event.target === easterEggModal) {
                    easterEggModal.style.display = 'none';
                }
            });

            // Обработчик ошибок для изображений
            easterEggImage.onerror = function() {
                console.error("Ошибка загрузки изображения:", this.src);
                easterEggModal.style.display = 'none';
            };

            // Создание снежинок
            function createSnowflake() {
                const snowflake = document.createElement('div');
                snowflake.classList.add('snowflake');

                // Настройки для снежинки
                snowflake.style.left = Math.random() * 100 + 'vw';
                snowflake.style.opacity = Math.random() * 0.6 + 0.3;
                const size = Math.random() * 8 + 4;
                snowflake.style.width = size + 'px';
                snowflake.style.height = size + 'px';

                // Анимация с рандомной скоростью
                const duration = Math.random() * 3 + 5;
                snowflake.style.animation = `snowfall ${duration}s linear infinite`;

                // Добавляем снежинку
                document.body.appendChild(snowflake);

                // Удаление через 10 секунд
                setTimeout(() => snowflake.remove(), duration * 1000 + 1000);
            }

            // Интервал создания снежинок
            const isMobile = /Mobi|Android/i.test(navigator.userAgent);
            setInterval(createSnowflake, isMobile ? 150 : 80);
        });
    </script>
</body>
</html>
