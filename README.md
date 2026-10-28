
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Basmala | My Portfolio</title>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background: #030405;
  color: #fff6df;
  font-family: Georgia, serif;
  overflow-x: hidden;
}

.scene {
  min-height: 100vh;
  position: relative;
  overflow: hidden;
  background:
    radial-gradient(ellipse at 50% 75%,
      #17130b 0%, #08090c 40%, #020304 85%);
  transition: background 2s ease;
}

.scene.lit {
  background:
    radial-gradient(ellipse at 52% 65%,
      #61431b 0%, #241b10 35%, #08090c 78%);
}

.stars {
  position: absolute;
  inset: 0;
  background-image:
    radial-gradient(#ffe6a0 1px, transparent 1px);
  background-size: 65px 65px;
  opacity: .15;
  animation: drift 20s linear infinite;
}

@keyframes drift {
  to { background-position: 65px 65px; }
}

.window {
  position: absolute;
  width: 35%;
  height: 35%;
  top: 8%;
  left: 8%;
  border: 2px solid #30291f;
  background: #05080e;
  box-shadow: 0 0 30px #000;
}

.window::before,
.window::after {
  content: "";
  position: absolute;
  background: #30291f;
}

.window::before {
  width: 3px;
  height: 100%;
  left: 50%;
}

.window::after {
  height: 3px;
  width: 100%;
  top: 50%;
}

.light-beam {
  position: absolute;
  top: 28%;
  right: 10%;
  width: 70%;
  height: 55%;
  background: linear-gradient(
    110deg,
    transparent,
    #ffcb6840,
    transparent
  );
  clip-path: polygon(15% 0, 100% 0, 85% 100%, 0 100%);
  opacity: 0;
  transition: opacity 2s;
  pointer-events: none;
}

.lit .light-beam {
  opacity: 1;
}

.desk {
  position: absolute;
  bottom: 14%;
  left: 5%;
  width: 90%;
  height: 12px;
  background: linear-gradient(#8d6434, #382719);
  box-shadow: 0 10px 25px #000;
}

.desk::after {
  content: "";
  position: absolute;
  top: 10px;
  left: 8%;
  width: 8px;
  height: 100px;
  background: #251b12;
  box-shadow: calc(84vw - 70px) 0 #251b12;
}

.monitor {
  position: absolute;
  bottom: calc(14% + 12px);
  left: 50%;
  transform: translateX(-50%);
  width: 34%;
  height: 22%;
  border: 5px solid #272522;
  border-radius: 5px;
  background: #050606;
  box-shadow: 0 0 25px #000;
  transition: box-shadow 2s;
}

.lit .monitor {
  box-shadow: 0 0 35px #d79b3d50;
}

.monitor::before {
  content: "";
  position: absolute;
  bottom: -24px;
  left: 45%;
  width: 10%;
  height: 22px;
  background: #36302a;
}

.monitor::after {
  content: "";
  position: absolute;
  bottom: -28px;
  left: 30%;
  width: 40%;
  height: 5px;
  background: #494036;
}

.laptop-glow {
  position: absolute;
  inset: 15%;
  background: radial-gradient(#b7803d22, transparent 70%);
}

.lamp {
  position: absolute;
  right: 13%;
  bottom: calc(14% + 12px);
  width: 65px;
  height: 105px;
}

.lamp::before {
  content: "";
  position: absolute;
  width: 5px;
  height: 70px;
  background: #756047;
  left: 30px;
  bottom: 0;
}

.lamp::after {
  content: "";
  position: absolute;
  width: 58px;
  height: 35px;
  background: #473523;
  border-radius: 50% 50% 5px 5px;
  top: 0;
  left: 4px;
  transition: all 1.5s;
}

.lit .lamp::after {
  background: #ffdb83;
  box-shadow: 0 0 25px #ffcb62, 0 0 65px #ffb52d;
}

.switch {
  position: absolute;
  z-index: 5;
  top: 45%;
  right: 7%;
  border: 1px solid #b98b40;
  background: #17120b;
  color: #ffd783;
  border-radius: 50%;
  width: 64px;
  height: 64px;
  font-size: 25px;
  cursor: pointer;
  box-shadow: 0 0 15px #d49a3b20;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  50% { box-shadow: 0 0 28px #d49a3b70; }
}

.switch:active {
  transform: scale(.92);
}

.hint {
  position: absolute;
  top: calc(45% + 76px);
  right: 4%;
  color: #b9a27a;
  font: 10px Arial, sans-serif;
  letter-spacing: 2px;
}

.intro {
  position: absolute;
  z-index: 3;
  top: 12%;
  left: 8%;
  right: 8%;
  text-align: center;
}

.eyebrow {
  color: #c99b51;
  font: 10px Arial, sans-serif;
  letter-spacing: 5px;
  opacity: 0;
  transition: opacity 2s;
}

h1 {
  font-size: clamp(30px, 7vw, 58px);
  font-weight: normal;
  color: #ffe1a0;
  text-shadow: 0 0 30px #dca34760;
  margin: 18px 0;
  overflow-wrap: anywhere;
}

#name {
  opacity: 0;
  transition: opacity 1s;
}

#name.show {
  opacity: 1;
}

.cursor {
  color: #d9a34e;
  animation: blink .8s infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}

.details {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 1.5s, transform 1.5s;
  color: #e4d5bc;
  font: 13px/2 Arial, sans-serif;
}

.details.show {
  opacity: 1;
  transform: translateY(0);
}

.details p {
  margin: 7px;
}

.tag {
  display: inline-block;
  border: 1px solid #98733b;
  padding: 7px 12px;
  margin: 5px;
  color: #e9c47d;
  font-size: 11px;
}

.footer {
  position: absolute;
  bottom: 3%;
  width: 100%;
  text-align: center;
  color: #8d795b;
  font: 10px Arial, sans-serif;
  letter-spacing: 3px;
}

@media (max-height: 650px) {
  .intro { top: 5%; }
  .monitor { height: 17%; }
  .window { height: 28%; }
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: .01ms !important;
    transition-duration: .01ms !important;
  }
}
</style>
</head>

<body>
<main class="scene" id="scene">

  <div class="stars"></div>
  <div class="window"></div>
  <div class="light-beam"></div>

  <section class="intro">
    <div class="eyebrow" id="eyebrow">
      WELCOME TO MY WORLD
    </div>

    <h1>
      <span id="name"></span><span class="cursor" id="cursor">|</span>
    </h1>

    <div class="details" id="details">
      <p>Student • Aspiring Engineer</p>
      <p>Embedded Systems & Artificial Intelligence</p>
      <p>Learning. Building. Creating.</p>

      <div>
        <span class="tag">Embedded Systems</span>
        <span class="tag">Artificial Intelligence</span>
        <span class="tag">Cybersecurity</span>
      </div>

      <p style="margin-top:20px;color:#c9a568">
        Every great journey starts with a spark.
      </p>
    </div>
  </section>

  <div class="monitor">
    <div class="laptop-glow"></div>
  </div>

  <div class="lamp"></div>
  <div class="desk"></div>

  <button class="switch" id="switch" aria-label="Turn on the light">
    ☼
  </button>

  <div class="hint" id="hint">TURN ON THE LIGHT</div>

  <div class="footer">MY PORTFOLIO • 2026</div>

</main>

<script>
const scene = document.getElementById("scene");
const button = document.getElementById("switch");
const name = document.getElementById("name");
const cursor = document.getElementById("cursor");
const details = document.getElementById("details");
const eyebrow = document.getElementById("eyebrow");
const hint = document.getElementById("hint");

const fullName = "Basmala Hamada Mohamed";
let started = false;

button.addEventListener("click", () => {
  if (started) {
    scene.classList.toggle("lit");
    return;
  }

  started = true;
  scene.classList.add("lit");
  button.textContent = "✦";
  hint.textContent = "WELCOME";

  setTimeout(() => {
    eyebrow.style.opacity = "1";
    name.classList.add("show");

    let i = 0;

    function typeName() {
      if (i < fullName.length) {
        name.textContent += fullName.charAt(i);
        i++;
        setTimeout(typeName, 100);
      } else {
        cursor.style.display = "none";

        setTimeout(() => {
          details.classList.add("show");
        }, 700);
      }
    }

    typeName();
  }, 1500);
});
</script>

</body>
</html>

