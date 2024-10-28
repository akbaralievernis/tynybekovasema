<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Для моей любимой</title>
  <style>
    body {
        font-family: 'Arial', sans-serif;
        background-color: #fce4ec;
        margin: 0;
        padding: 0;
        text-align: center;
        overflow-x: hidden;
        cursor: url('snapedit_1709554354175.png'), auto;
        background: linear-gradient(120deg, #f48fb1, #81d4fa);
        background-size: 200% 200%;
        animation: gradient 10s ease infinite;
      }
  @keyframes gradient {
        0% { background-position: 0% 50%; }
        50% { background-position: 100% 50%; }
        100% { background-position: 0% 50%; }
}
/* Прелоадер */
#preloader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}
/* Видео-фон */
.video-bg video {
  position: fixed;
  top: 0;
  left: 0;
  min-width: 100%;
  min-height: 100%;
  z-index: -1;
}
/* Анимация сердечек */
.heart {
  position: absolute;
  width: 20px;
  height: 20px;
  background: red;
  border-radius: 50%;
  animation: pop 1s;
}
@keyframes pop {
  from { transform: scale(0); }
  to { transform: scale(2); opacity: 0; }
}
/* Навигация */
nav img {
  width: 50px;
  margin: 10px;
  transition: transform 0.3s;
}
nav img:hover {
  transform: scale(1.2);
}
/* Секретное сообщение */
#secret-message {
  font-size: 24px;
  color: #d81b60;
}
/* Плавающие частицы */
#particles-js {
  position: fixed;
  width: 100%;
  height: 100%;
  z-index: -2;
}
  </style>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
  <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>
</head>
<body>
  <!-- Прелоадер -->
  <div id="preloader">
    <h1>Для самой особенной 🌹</h1>
  </div>
  <!-- Контейнер для частиц -->
  <div id="particles-js"></div>
  <!-- Видео-фон -->
  <div class="video-bg">
    <video autoplay muted loop aria-label="Романтический фон">
      <source src="54598185f0756ef83bc5ef13a423e327b6d17c100dc915d621d2e6ae8c093cd1.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  <!-- Контент -->
  <header>
    <h1>Люблю тебя бесконечно ❤️</h1>
  </header>
  <nav>
    <a href="#story" class="smooth-scroll"><img src="images/icon1.png" alt="История"></a>
    <a href="#gallery" class="smooth-scroll"><img src="images/icon2.png" alt="Галерея"></a>
    <a href="#future" class="smooth-scroll"><img src="images/icon3.png" alt="Будущее"></a>
  </nav>
  <section id="story">
    <h2>Наша история</h2>
    <p>Каждый день с тобой — это чудо, и я счастлив, что мы вместе.</p>
    <img src="snapedit_1709554354175.jpg" alt="Фото" width="500">
  </section>
  <section id="gallery">
    <h2>Галерея</h2>
    <img src="snapedit_1709554354175.jpg" alt="Момент 1" width="400">
    <img src="snapedit_1709554354175.jpg" alt="Момент 2" width="400">
  </section>
  <section id="future">
    <h2>Наше будущее</h2>
    <p>Я с нетерпением жду все дни, которые мы проведем вместе!</p>
  </section>
  <button id="secret-btn">Нажми для сюрприза</button>
  <div id="secret-message" style="display: none;">
    <h2>Я люблю тебя больше всего на свете!</h2>
  </div>
  <button onclick="playAudio()">Прослушать послание</button>
  <audio id="audio" src="music/message.mp3"></audio>
  <footer>
    <p>С любовью, всегда твой ❤️</p>
  </footer>
  <script>
    // Прелоадер
    const video = document.querySelector('.video-bg video');
    video.oncanplaythrough = () => {
      document.getElementById("preloader").style.display = "none";
    };
    // Анимация заголовка
    gsap.from("h1", { duration: 2, y: -100, opacity: 0, ease: "bounce.out" });
    // Инициализация частиц
    particlesJS('particles-js', {
      particles: {
        number: { value: 80 },
        color: { value: '#f48fb1' },
        shape: { type: 'circle' },
        opacity: { value: 0.5 },
        size: { value: 3 },
        line_linked: { enable: true, color: '#d81b60' },
        move: { speed: 2 }
      }
    });
    // Аудио-послание
    function playAudio() {
      document.getElementById('audio').play();
    }
    // Секретное сообщение
    document.getElementById('secret-btn').onclick = function () {
      const message = document.getElementById('secret-message');
      message.style.display = 'block';
      gsap.fromTo(message, { opacity: 0, y: 50 }, { opacity: 1, y: 0, duration: 1 });
    };
    // Плавная прокрутка
    document.querySelectorAll('.smooth-scroll').forEach(anchor => {
      anchor.addEventListener('click', function (e) {
        e.preventDefault();
        document.querySelector(this.getAttribute('href')).scrollIntoView({
          behavior: 'smooth'
        });
      });
    });
    // Сердечки при клике
    document.body.addEventListener('click', (e) => {
      const heart = document.createElement('div');
      heart.className = 'heart';
      heart.style.left = `${e.clientX}px`;
      heart.style.top = `${e.clientY}px`;
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 1000);
    });
  </script>
</body>
</html>
