<style>
body {
    background-color: #121212;
    color: #e0e0e0;
    font-family: Arial, sans-serif;
    margin: 0;
    min-height: 100vh;
    position: relative;
    overflow-x: hidden;
}
a {
    color: #6A9CFF;
}
a:hover {
    color: #1E90FF;
}
h1, h2, h3, h4, h5, h6 {
    color: #ffffff;
}
blockquote {
    border-left: 4px solid #4682B4;
    padding-left: 10px;
    color: #e0e0e0;
}
img {
    border: 2px solid #4169E1;
}

/* Снег */
.snowflake {
    position: fixed;
    width: 10px;
    height: 10px;
    background: white;
    border-radius: 50%;
    pointer-events: none;
    z-index: -1;
}

@keyframes snowfall {
    0% {
        transform: translateY(-10vh) translateX(0);
    }
    100% {
        transform: translateY(100vh) translateX(20px);
    }
}
</style>

<script>
function createSnowflake() {
    const snowflake = document.createElement('div');
    snowflake.classList.add('snowflake');
    snowflake.style.left = Math.random() * 100 + 'vw';
    snowflake.style.animationDuration = Math.random() * 3 + 2 + 's';
    snowflake.style.opacity = Math.random();
    snowflake.style.animation = `snowfall ${Math.random() * 3 + 2}s linear infinite`;

    document.body.appendChild(snowflake);

    setTimeout(() => {
        snowflake.remove();
    }, 5000);
}

setInterval(createSnowflake, 50);
</script>

# WebGL версия игры **FrostLine** (Сделано в Unity3D)
> Сделано Александром Дробовым (code) и Владимиром Кругляковым (art)

Можно сыграть перейдя по этой ссылке:
[FrostLine GitHub](https://clck.ru/3GM46t)

Itch.io версия:
[FrostLine Itch.io](https://mramorlomai.itch.io/frostline)

Ну или если ты хочешь скачать standalone версию на windows/~~linux~~:
[FrostLine PC](https://disk.yandex.ru/d/E8916kl56iHSUw)

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

P.S. (Linux больше не поддерживается)
