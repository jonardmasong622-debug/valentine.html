<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Valentine 💘</title>

<style>
  body {
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #ffb6c1, #ffe6eb);
    overflow: hidden;
    height: 100vh;
    margin: 0;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container {
    text-align: center;
    background: white;
    padding: 40px;
    border-radius: 20px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.2);
    z-index: 2;
    position: relative;
  }

  h1 {
    margin-bottom: 20px;
  }

  button {
    font-size: 18px;
    padding: 14px 30px;
    margin: 12px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  #yesBtn {
    background-color: #4CAF50;
    color: white;
  }

  #yesBtn.wiggle {
    animation: wiggle 0.4s infinite;
  }

  #noBtn {
    background-color: #f44336;
    color: white;
  }

  @keyframes wiggle {
    0% { transform: rotate(0deg); }
    25% { transform: rotate(2deg); }
    50% { transform: rotate(-2deg); }
    75% { transform: rotate(2deg); }
    100% { transform: rotate(0deg); }
  }

  /* 💛 Nailong */
  .nailong {
    width: 120px;
    margin: 0 auto 15px;
    animation: bounce 1.5s infinite;
    transition: transform 0.3s ease;
  }

  @keyframes bounce {
    0%,100% { transform: translateY(0); }
    50% { transform: translateY(-12px); }
  }

  .heart {
    position: absolute;
    color: #ff4d6d;
    font-size: 24px;
    animation: floatUp 6s linear infinite;
    opacity: 0.8;
  }

  @keyframes floatUp {
    from {
      transform: translateY(100vh) scale(1);
      opacity: 1;
    }
    to {
      transform: translateY(-10vh) scale(1.5);
      opacity: 0;
    }
  }
</style>
</head>

<body>

<div class="container">
  <!-- 💛 Nailong SVG -->
  <div id="nailong" class="nailong">
    <svg viewBox="0 0 200 200">
      <circle cx="100" cy="110" r="55" fill="#FFD93D"/>
      <circle cx="80" cy="100" r="6" fill="#000"/>
      <circle cx="120" cy="100" r="6" fill="#000"/>
      <path d="M85 120 Q100 135 115 120" stroke="#000" stroke-width="4" fill="none"/>
      <circle cx="60" cy="80" r="15" fill="#FFD93D"/>
      <circle cx="140" cy="80" r="15" fill="#FFD93D"/>
      <text x="100" y="185" text-anchor="middle" font-size="18">Nailong 💛</text>
    </svg>
  </div>

  <h1>💘 Will you be my Valentine, <span id="name">My Love</span>?</h1>
  <button id="yesBtn" onclick="yesClicked()">Yes 💕</button>
  <button id="noBtn" onclick="noClicked()">No 😢</button>
</div>

<audio id="music" loop>
  <source src="https://cdn.pixabay.com/audio/2022/10/25/audio_8fdfc0a16a.mp3" type="audio/mpeg">
</audio>

<script>
  // ✏️ CHANGE HER NAME
  document.getElementById("name").textContent = "Love";

  let noCount = 0;
  let yesScale = 1;

  const noTexts = [
    "Nailong is sad 😳",
    "Nailong says pls 🥺",
    "Nailong crying now 😭",
    "Nailong gave up..."
  ];

  function noClicked() {
    playMusic();
    noCount++;

    const noBtn = document.getElementById("noBtn");
    const yesBtn = document.getElementById("yesBtn");
    const nailong = document.getElementById("nailong");

    if (noCount <= 3) {
      noBtn.textContent = noTexts[noCount - 1];
      noBtn.style.transform = `scale(${1 + noCount * 0.5})`;

      yesScale += 0.3;
      yesBtn.style.transform = `scale(${yesScale})`;
      yesBtn.classList.add("wiggle");

      nailong.style.transform = `scale(${1 + noCount * 0.15}) rotate(-5deg)`;
    }

    if (noCount === 4) {
      noBtn.style.display = "none";
      nailong.style.transform = "scale(1.4)";
    }
  }

  function yesClicked() {
    playMusic();
    document.body.innerHTML = `
      <h1 style="color:white; text-shadow:2px 2px 8px #000;">
        💖 SHE SAID YES 💖<br>
        Nailong approves 🐲💛<br>
        I love you 😍
      </h1>
    `;
  }

  function playMusic() {
    const music = document.getElementById("music");
    if (music.paused) music.play();
  }

  // 💕 Floating hearts
  setInterval(() => {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.innerHTML = "💖";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = Math.random() * 20 + 20 + "px";
    heart.style.animationDuration = Math.random() * 3 + 4 + "s";
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 6000);
  }, 300);
</script>

</body>
</html>
