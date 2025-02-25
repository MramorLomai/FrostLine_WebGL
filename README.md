body {
  padding: 0;
  margin: 0;
  background-color: #121212; /* Темный фон для всей страницы */
  color: #ffffff; /* Белый текст по умолчанию */
  font-family: 'Press Start 2P', cursive; /* Пиксельный шрифт */
}

#unity-container {
  position: absolute;
}

#unity-container.unity-desktop {
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

#unity-container.unity-mobile {
  width: 100%;
  height: 100%;
}

#unity-canvas {
  background: #1e1e1e; /* Темный фон для canvas */
}

.unity-mobile #unity-canvas {
  width: 100%;
  height: 100%;
}

#unity-loading-bar {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  display: none;
}

#unity-logo {
  width: 154px;
  height: 130px;
  background: url('unity-logo-dark.png') no-repeat center; /* Логотип для темной темы */
}

#unity-progress-bar-empty {
  width: 141px;
  height: 18px;
  margin: 10px 0 0 6.5px;
  background: url('progress-bar-empty-dark.png') no-repeat center; /* Пустой прогресс-бар для темной темы */
}

#unity-progress-bar-full {
  width: 0%;
  height: 18px;
  margin-top: 10px;
  background: url('progress-bar-full-dark.png') no-repeat center; /* Полный прогресс-бар для темной темы */
}

#unity-footer {
  position: relative;
}

.unity-mobile #unity-footer {
  display: none;
}

#unity-webgl-logo {
  float: left;
  width: 204px;
  height: 38px;
  background: url('webgl-logo.png') no-repeat center;
}

#unity-build-title {
  float: right;
  margin-right: 10px;
  line-height: 38px;
  font-family: 'Press Start 2P', cursive; /* Пиксельный шрифт для заголовка */
  font-size: 14px; /* Уменьшенный размер для пиксельного шрифта */
  color: #ffffff; /* Белый текст */
}

#unity-fullscreen-button {
  float: right;
  width: 38px;
  height: 38px;
  background: url('fullscreen-button.png') no-repeat center;
}

#unity-warning {
  position: absolute;
  left: 50%;
  top: 5%;
  transform: translateX(-50%);
  background: #333333; /* Темный фон для предупреждения */
  padding: 10px;
  display: none;
  color: #ffffff; /* Белый текст */
  font-family: 'Press Start 2P', cursive; /* Пиксельный шрифт для предупреждения */
  font-size: 12px; /* Уменьшенный размер для пиксельного шрифта */
  border: 2px solid #555555; /* Граница для выделения */
}