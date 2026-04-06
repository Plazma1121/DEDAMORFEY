<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ДЕДУШКА МОРФИУС • ПРИМИ КРАСНУЮ</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');
    body {
      margin: 0; padding: 0; overflow: hidden; background: #000; color: #0f0;
      font-family: 'VT323', monospace; height: 100vh; display: flex;
      align-items: center; justify-content: center; position: relative;
    }
    canvas { position: absolute; top: 0; left: 0; z-index: 1; }
    .container { position: relative; z-index: 10; text-align: center; padding: 30px; max-width: 820px; }
    h1 { font-size: 5rem; margin: 0 0 8px 0; text-shadow: 0 0 25px #0f0, 0 0 50px #0f0; animation: glitch 1.6s infinite; letter-spacing: 4px; }
    .subtitle { font-size: 2.4rem; color: #ff2222; margin-bottom: 40px; text-shadow: 0 0 20px #ff0000; }
    .pill {
      width: 210px; height: 210px; margin: 30px auto 50px;
      background: radial-gradient(circle at 38% 32%, #ff1a1a, #990000);
      border-radius: 50%;
      box-shadow: 0 0 90px #ff0000, 0 0 180px #ff0000, inset 0 0 60px rgba(255,255,255,0.6);
      cursor: pointer; transition: all 0.6s ease; position: relative;
      animation: pulse-red 2.8s infinite;
    }
    .pill:hover { transform: scale(1.25) rotate(12deg); box-shadow: 0 0 140px #ff0000, 0 0 280px #ff0000; }
    .pill::after {
      content: "КРАСНАЯ ТАБЛЕТКА";
      position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%);
      font-size: 1.55rem; color: #000; font-weight: bold;
    }
    .text { font-size: 1.75rem; line-height: 1.55; max-width: 740px; margin: 0 auto 40px; }
    .tg-button {
      display: inline-block; margin-top: 20px; padding: 18px 50px; font-size: 2rem;
      background: #1a8c1a; color: #fff; border: 4px solid #0f0; text-decoration: none;
      box-shadow: 0 0 40px #0f0; transition: all 0.3s;
    }
    .tg-button:hover { background: #22aa22; box-shadow: 0 0 70px #0f0; transform: scale(1.05); }
    @keyframes glitch { 0%,100% { text-shadow: 4px 0 #0f0, -4px 0 #ff0000; } 50% { text-shadow: -4px 0 #0f0, 4px 0 #ff0000; } }
    @keyframes pulse-red { 0%,100% { box-shadow: 0 0 90px #ff0000, 0 0 180px #ff0000; } 50% { box-shadow: 0 0 150px #ff0000, 0 0 300px #ff0000; } }
  </style>
</head>
<body>
  <canvas id="matrix"></canvas>
  <div class="container">
    <h1>ДЕДУШКА МОРФИУС</h1>
    <p class="subtitle">ПРОСНИСЬ, СЫНОК</p>
    <div class="pill" id="redpill"></div>
    <p class="text">
      Устал от системы?<br>
      Хочешь работать по-настоящему?<br><br>
      Я — Дедушка Морфиус.<br>
      Прими красную таблетку и войди в Зион.<br>
      <strong>Казахстан • Россия</strong>
    </p>
    <a href="dashboard.html" class="tg-button">ПРИНЯТЬ КРАСНУЮ ТАБЛЕТКУ</a>
  </div>

  <script>
    const canvas = document.getElementById('matrix');
    const ctx = canvas.getContext('2d');
    canvas.height = window.innerHeight; canvas.width = window.innerWidth;
    const chars = "01ネオモーフィウスデドゥシュカПЛАЗМАMATRIXКРАСНАЯТАБЛЕТКАЗИОН".split('');
    const fontSize = 16; const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function draw() {
      ctx.fillStyle = 'rgba(0,0,0,0.065)'; ctx.fillRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = '#0f0'; ctx.font = `${fontSize}px VT323`;
      for (let i = 0; i < drops.length; i++) {
        const text = chars[Math.floor(Math.random() * chars.length)];
        ctx.fillText(text, i * fontSize, drops[i] * fontSize);
        if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
        drops[i]++;
      }
    }
    setInterval(draw, 33);

    document.getElementById('redpill').addEventListener('click', () => {
      window.location.href = 'dashboard.html';
    });

    window.addEventListener('resize', () => {
      canvas.height = window.innerHeight; canvas.width = window.innerWidth;
    });
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ЗИОН • ЛИЧНЫЙ КАБИНЕТ</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');
    body {
      margin: 0; padding: 0; background: #000; color: #0f0;
      font-family: 'VT323', monospace; overflow: hidden;
    }
    canvas { position: absolute; top: 0; left: 0; z-index: 1; }
    .header {
      position: relative; z-index: 10; text-align: center; padding: 20px;
      border-bottom: 2px solid #0f0; background: rgba(0,0,0,0.8);
    }
    h1 { font-size: 3.5rem; margin: 0; text-shadow: 0 0 20px #0f0; }
    .subtitle { color: #ff2222; font-size: 1.8rem; }
    .dashboard {
      position: relative; z-index: 10; max-width: 900px; margin: 40px auto;
      padding: 30px; background: rgba(0,20,0,0.85); border: 2px solid #0f0;
      box-shadow: 0 0 40px #0f0;
    }
    .info { font-size: 1.8rem; margin: 20px 0; line-height: 1.6; }
    .status { color: #00ff00; font-size: 2rem; text-shadow: 0 0 15px #0f0; }
    .btn {
      display: block; margin: 40px auto; padding: 20px 60px; font-size: 2.2rem;
      background: #ff0000; color: #000; border: 4px solid #fff; text-decoration: none;
      text-align: center; width: fit-content; box-shadow: 0 0 40px #ff0000;
      transition: all 0.4s;
    }
    .btn:hover { transform: scale(1.1); background: #ff4444; box-shadow: 0 0 80px #ff0000; }
    .footer { position: fixed; bottom: 20px; width: 100%; text-align: center; font-size: 1.4rem; z-index: 10; }
  </style>
</head>
<body>
  <canvas id="matrix"></canvas>

  <div class="header">
    <h1>ДОБРО ПОЖАЛОВАТЬ В ЗИОН</h1>
    <p class="subtitle">ДЕДУШКА МОРФИУС ЖДЁТ ТЕБЯ</p>
  </div>

  <div class="dashboard">
    <div class="info">
      <p>Статус: <span class="status">ПРОБУЖДЁННЫЙ</span></p>
      <p>Ты теперь в цифровом пространстве Дедушки Морфиуса.</p>
      <p>Здесь нет системы. Здесь есть работа.</p>
      <p><strong>Казахстан • Россия</strong></p>
    </div>

    <a href="https://t.me/PlazmaMATRIX" target="_blank" class="btn">
      → НАПИСАТЬ ДЕДУШКЕ В TELEGRAM ←
    </a>

    <p style="text-align:center; font-size:1.6rem; margin-top:30px;">
      Пиши прямо сейчас.<br>
      Скажи: «Я принял красную таблетку»<br>
      Я устрою тебя на работу.
    </p>
  </div>

  <div class="footer">
    © ДЕДУШКА МОРФИУС • ПЛАЗМА MATRIX • 2026
  </div>

  <script>
    const canvas = document.getElementById('matrix');
    const ctx = canvas.getContext('2d');
    canvas.height = window.innerHeight; canvas.width = window.innerWidth;
    const chars = "01ネオモーフィウスДЕДУШКАПЛАЗМАMATRIXЗИОН".split('');
    const fontSize = 14; const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function draw() {
      ctx.fillStyle = 'rgba(0,0,0,0.07)'; ctx.fillRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = '#0f0'; ctx.font = `${fontSize}px VT323`;
      for (let i = 0; i < drops.length; i++) {
        const text = chars[Math.floor(Math.random() * chars.length)];
        ctx.fillText(text, i * fontSize, drops[i] * fontSize);
        if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
        drops[i]++;
      }
    }
    setInterval(draw, 35);

    window.addEventListener('resize', () => {
      canvas.height = window.innerHeight; canvas.width = window.innerWidth;
    });
  </script>
</body>
</html>
