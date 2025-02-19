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

/* Контейнер для основного контента */
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

/* Стили для списков управления */
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

/* Снег */
.snowflake {
    position: fixed;
    width: 10px;
    height: 10px;
    background: white;
    border-radius: 50%;
    pointer-events: none;
    z-index: 2;
    filter: blur(1px);
}

@keyframes snowfall {
    0% {
        transform: translateY(-10vh) translateX(0) rotate(0deg);
    }
    100% {
        transform: translateY(100vh) translateX(20px) rotate(360deg);
    }
}

/* Адаптивный дизайн */
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

<script>
function createSnowflake() {
    console.log("Creating snowflake"); // Добавьте эту строку для отладки
    const snowflake = document.createElement('div');
    snowflake.classList.add('snowflake');
    snowflake.style.left = Math.random() * 100 + 'vw';
    snowflake.style.opacity = Math.random() * 0.4 + 0.1;
    snowflake.style.width = (Math.random() * 8 + 2) + 'px';
    snowflake.style.height = snowflake.style.width;
    snowflake.style.animation = `snowfall ${Math.random() * 3 + 3}s linear infinite`;

    document.body.appendChild(snowflake);

    setTimeout(() => {
        snowflake.remove();
    }, 6000);
}

// Создаем меньше снежинок на мобильных устройствах
const isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
const snowflakeInterval = isMobile ? 200 : 100;

setInterval(createSnowflake, snowflakeInterval);
</script>

<div class="content-container">
    {{ "## WebGL версия игры **FrostLine** (Сделано в Unity3D)
    > Сделано Александром Дробовым (code) и Владимиром Кругляковым (art)

    Можно сыграть перейдя по этой ссылке: [FrostLine GitHub](https://clck.ru/3GM46t)

    Itch.io версия: [FrostLine Itch.io](https://mramorlomai.itch.io/frostline)

    Ну или если ты хочешь скачать standalone версию на windows/~~linux~~: [FrostLine PC](https://disk.yandex.ru/d/E8916kl56iHSUw)

    **FrostLine** — это динамичный арена-шутер на выживание от первого лица, действие которого разворачивается в зимнем средневековом сеттинге. Вам предстоит взять на себя роль рыцаря и защитить крепость от орд врагов. Игра сочетает в себе элементы классических шутеров, таких как __Quake, Ultrakill, Doom и Half-Life__.

    ![FrostLinePoster](https://github.com/user-attachments/assets/3db32614-dff6-4eca-acd0-79268bc0a492)

    Управление:

    - Ходьба - "WASD"/Стрелки
    * Приседание/Быстрое приземление - "Ctrl"
    + Атака - "Mouse0"
    - Перезарядка - "R" / Авто перезарядка
    * Рывок - "Mouse1"
    + Мясной крюк - "F"
    - Slow-mo - "Q"
    * Прыжок - "Space"
    + Двойной прыжок - 2x "Space"
    - Бег - "Shift"
    * Смена оружия - "MouseWhl"/ Цифры
    + Пауза  - "Escape"
    - Консоль разработчика - "~"

    P.S. (Linux больше не поддерживается)" | markdownify }}
</div>
