<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Syafni Tiara Puspita 🎂</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(#ffdee9, #b5fffc);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
      text-align: center;
    }
    .container {
      max-width: 600px;
      padding: 2rem;
      background: white;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.2);
      position: relative;
    }

    
    h1 {
      font-size: 2rem;
      color: #ff4081;
    }
    .message {
      margin-top: 1rem;
      font-size: 1.2rem;
      display: none;
    }
    .btn, .hug-btn {
      margin-top: 1.5rem;
      padding: 0.8rem 1.5rem;
      font-size: 1rem;
      border: none;
      border-radius: 10px;
      background: #ff4081;
      color: white;
      cursor: pointer;
      transition: background 0.3s;
    }
    .btn:hover, .hug-btn:hover {
      background: #e91e63;
    }
    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: -1;
    }
    #icebear {
      display: none;
      width: 150px;
      margin-top: 1.5rem;
      animation: bounce 1s infinite;
    }
    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }
    .hearts {
      position: fixed;
      top: 0;
      left: 0;
      pointer-events: none;
      width: 100%;
      height: 100%;
      z-index: 1;
    }
    .heart {
      width: 20px;
      height: 20px;
      background: red;
      position: absolute;
      top: -20px;
      transform: rotate(45deg);
      animation: fall 4s linear infinite;
    }
    .heart::before, .heart::after {
      content: "";
      position: absolute;
      width: 20px;
      height: 20px;
      background: red;
      border-radius: 50%;
    }
    .heart::before {
      top: -10px;
      left: 0;
    }
    .heart::after {
      top: 0;
      left: -10px;
    }
    @keyframes fall {
      0% { transform: translateY(0) rotate(45deg); opacity: 1; }
      100% { transform: translateY(100vh) rotate(45deg); opacity: 0; }
    }

    #musicBtn {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      background: #ff4081;
      color: white;
      border: none;
      border-radius: 20px;
      padding: 10px 20px;
      font-size: 1rem;
      cursor: pointer;
      z-index: 3;
    }

  </style>
</head>
<body>
  <canvas id="confetti"></canvas>
  <div class="hearts" id="hearts"></div>
  <div class="container">
    <h1>Selamat Ulang Tahun, Sayangkuuu! my hani bani switi little babyyy 🎉</h1>
    <p class="message" id="msg1"></p>
    <p class="message" id="msg2"></p>
    <p class="message" id="msg3"></p>
    <p class="message" id="msg4"></p>
    <img id="icebear" src="https://media.tenor.com/qWvu6yAZczsAAAAi/icebear-ice-bear.gif" alt="Ice Bear">
    <button class="btn" onclick="showNextMessage()">Open Letter ❤️</button>
    <button class="hug-btn" onclick="sendHug()">Virtual hugggggg 🤗</button>
    <button onclick="toggleMusic()" id="musicBtn" style="
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  background: #ff4081;
  color: white;
  border: none;
  border-radius: 20px;
  padding: 10px 20px;
  font-size: 1rem;
  cursor: pointer;
  z-index: 10;
">Play Song 🎵</button>

  </div>

  <audio id="bgmusic" loop>
    <source src="https://media.vocaroo.com/mp3/1oKjajUc90EF" type="audio/mpeg" />
  </audio>


  <script>
    const messages = [
      "I hope today is ur happiest day cause u were born to this world ❤️",
      "Teknyuu for ur presence cuz u make my world changing 🌈",
      "I love youu veryyyy mucchhh💖💖💖💖💖💖💖💖💖",
      "Maaf ya aku ga disana pas hari penting begini, sooooo i sent u a cute ice bear for u.... jadi dia bisa gantiin aku buat nemenin kamuu cayaangg 🥰"
    ];
    let current = 0;

    function showNextMessage() {
      if (current < messages.length) {
        typeEffect(document.getElementById("msg" + (current + 1)), messages[current]);
        current++;
        if (current === messages.length) {
          document.getElementById("icebear").style.display = "block";
        }
      } else {
        alert("Hwappy birthdayy babyyy, Wopyuu 😘");
      }
    }

    function typeEffect(element, text, i = 0) {
      element.style.display = "block";
      if (i < text.length) {
        element.innerHTML += text.charAt(i);
        setTimeout(() => typeEffect(element, text, i + 1), 50);
      }
    }

    function sendHug() {
      document.body.style.animation = "shake 0.5s";
      setTimeout(() => document.body.style.animation = "", 500);
      generateHearts();
    }

    function generateHearts() {
      const hearts = document.getElementById('hearts');
      for (let i = 0; i < 20; i++) {
        const heart = document.createElement('div');
        heart.className = 'heart';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
        hearts.appendChild(heart);
        setTimeout(() => heart.remove(), 5000);
      }
    }

    // Konfeti efek tetap
    const canvas = document.getElementById('confetti');
    const ctx = canvas.getContext('2d');
    let W = window.innerWidth;
    let H = window.innerHeight;
    canvas.width = W;
    canvas.height = H;

    const particles = [];
    const particleCount = 150;
    for (let i = 0; i < particleCount; i++) {
      particles.push({
        x: Math.random() * W,
        y: Math.random() * H,
        r: Math.random() * 10 + 5,
        d: Math.random() * particleCount,
        color: `hsl(${Math.random() * 360}, 100%, 70%)`,
        tilt: Math.floor(Math.random() * 10) - 10,
        tiltAngleIncremental: (Math.random() * 0.07) + .05,
        tiltAngle: 0
      });
    }

    function draw() {
      ctx.clearRect(0, 0, W, H);
      for (let i = 0; i < particleCount; i++) {
        const p = particles[i];
        ctx.beginPath();
        ctx.lineWidth = p.r / 2;
        ctx.strokeStyle = p.color;
        ctx.moveTo(p.x + p.tilt + p.r / 3, p.y);
        ctx.lineTo(p.x + p.tilt, p.y + p.tilt + p.r / 3);
        ctx.stroke();
      }
      update();
    }

    function update() {
      for (let i = 0; i < particleCount; i++) {
        const p = particles[i];
        p.tiltAngle += p.tiltAngleIncremental;
        p.y += (Math.cos(p.d) + 3 + p.r / 2) / 2;
        p.x += Math.sin(p.d);
        p.tilt = Math.sin(p.tiltAngle - (i / 3)) * 15;
        if (p.y > H) {
          particles[i] = {
            x: Math.random() * W,
            y: -20,
            r: p.r,
            d: p.d,
            color: p.color,
            tilt: p.tilt,
            tiltAngleIncremental: p.tiltAngleIncremental,
            tiltAngle: p.tiltAngle
          };
        }
      }
    }

    setInterval(draw, 30);
    window.addEventListener('resize', () => {
      W = window.innerWidth;
      H = window.innerHeight;
      canvas.width = W;
      canvas.height = H;
    });

    function toggleMusic() {
  const audio = document.getElementById("bgmusic");
  const btn = document.getElementById("musicBtn");
  if (audio.paused) {
    audio.play();
    btn.textContent = "Pause Song ⏸️";
  } else {
    audio.pause();
    btn.textContent = "Play Song 🎵";
  }
}

  </script>
</body>
</html>
