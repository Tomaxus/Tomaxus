<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tomás | Cybersecurity Portfolio</title>

<style>
/* Fondo negro hacker */
body {
  margin: 0;
  background: black;
  color: #00ff9c;
  font-family: "Courier New", monospace;
  overflow-x: hidden;
}

/* Matrix background */
canvas {
  position: fixed;
  top: 0;
  left: 0;
  z-index: -1;
}

/* Contenedor principal */
.container {
  text-align: center;
  padding: 50px;
}

/* Texto glitch */
.glitch {
  font-size: 3rem;
  font-weight: bold;
  animation: glitch 1.5s infinite;
}

@keyframes glitch {
  0% { text-shadow: 2px 2px #00ff9c; }
  20% { text-shadow: -2px 2px #00ffff; }
  40% { text-shadow: 2px -2px #00ff00; }
  60% { text-shadow: -2px -2px #00ff9c; }
  100% { text-shadow: 2px 2px #00ff9c; }
}

/* Subtitulo typing */
.typing {
  font-size: 1.5rem;
  border-right: 2px solid #00ff9c;
  display: inline-block;
  padding-right: 5px;
  animation: blink 0.7s infinite;
}

@keyframes blink {
  50% { border-color: transparent; }
}

/* Tarjetas */
.card {
  border: 1px solid #00ff9c;
  padding: 20px;
  margin: 20px auto;
  width: 60%;
  background: rgba(0,255,156,0.05);
  box-shadow: 0 0 15px #00ff9c;
  border-radius: 10px;
}

/* Botones */
.btn {
  padding: 12px 20px;
  border: 2px solid #00ff9c;
  color: #00ff9c;
  text-decoration: none;
  margin: 10px;
  display: inline-block;
  transition: 0.3s;
}

.btn:hover {
  background: #00ff9c;
  color: black;
  box-shadow: 0 0 20px #00ff9c;
}
</style>
</head>

<body>

<canvas id="matrix"></canvas>

<div class="container">
  <h1 class="glitch">👋 Hola, soy Tomás</h1>
  <h2 class="typing" id="typing"></h2>

  <div class="card">
    <h2>🛡️ Sobre mí</h2>
    <p>🔐 Apasionado por la Seguridad Informática y el Hacking Ético</p>
    <p>🧠 Estudiando: Linux, Redes, Python, Pentesting</p>
    <p>🎯 Meta: Convertirme en Cybersecurity Expert / Red Team</p>
  </div>

  <div class="card">
    <h2>⚔️ Skills</h2>
    <p>✔ Linux & Kali Linux</p>
    <p>✔ Python & Bash</p>
    <p>✔ Networking & Pentesting</p>
  </div>

  <div class="card">
    <h2>🌐 Encuéntrame</h2>
    <a class="btn" href="https://github.com/Tomaxus" target="_blank">GitHub</a>
    <a class="btn" href="https://www.linkedin.com/in/tomas-uribe-sanchez-614229293/" target="_blank">LinkedIn</a>
  </div>
</div>

<!-- Typing effect -->
<script>
const text = "Cybersecurity Student • Pentester • Ethical Hacker";
let i = 0;
function typing() {
  if (i < text.length) {
    document.getElementById("typing").innerHTML += text.charAt(i);
    i++;
    setTimeout(typing, 80);
  }
}
typing();
</script>

<!-- Matrix effect -->
<script>
const canvas = document.getElementById("matrix");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const letters = "01TOMASCYBERSECURITYHACKING";
const fontSize = 16;
const columns = canvas.width / fontSize;
const drops = Array(Math.floor(columns)).fill(1);

function draw() {
  ctx.fillStyle = "rgba(0,0,0,0.05)";
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  ctx.fillStyle = "#00ff9c";
  ctx.font = fontSize + "px monospace";

  for (let i = 0; i < drops.length; i++) {
    const text = letters[Math.floor(Math.random() * letters.length)];
    ctx.fillText(text, i * fontSize, drops[i] * fontSize);

    if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
      drops[i] = 0;
    }
    drops[i]++;
  }
}

setInterval(draw, 35);
</script>

</body>
</html>
