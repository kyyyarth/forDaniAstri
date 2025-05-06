<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>A Little Surprise</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    body {
      background: linear-gradient(to bottom right, #e0eafc, #cfdef3);
      color: #333;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      transition: background 0.6s;
      overflow: hidden;
    }
    .container {
      text-align: center;
      padding: 2rem;
      border-radius: 1rem;
      background: rgba(255, 255, 255, 0.9);
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
      width: 90%;
      max-width: 400px;
      position: relative;
      z-index: 2;
    }
    h1, h2, p {
      margin-bottom: 1rem;
    }
    button {
      padding: 0.6rem 1.2rem;
      border: none;
      border-radius: 999px;
      background-color: #4f46e5;
      color: #fff;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.3s;
    }
    button:hover {
      background-color: #4338ca;
    }
    .hidden {
      display: none;
    }
    .options button {
      margin: 0.5rem;
    }
    #noBtn {
      position: relative;
    }
    audio {
      display: none;
    }
    .balloon {
      position: absolute;
      width: 40px;
      height: 60px;
      background: pink;
      border-radius: 50% 50% 45% 45%;
      animation: float 6s ease-in infinite;
      opacity: 0.8;
      z-index: 1;
    }
    @keyframes float {
      0% {
        transform: translateY(100vh) rotate(0deg);
        opacity: 0;
      }
      50% {
        opacity: 1;
      }
      100% {
        transform: translateY(-100vh) rotate(360deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <audio autoplay loop>
    <source src="kereta-kencan-hivi.mp3" type="audio/mpeg">

  </audio>

  <div class="container" id="startPage">
    <h1>Ready to know something?</h1>
    <button onclick="showInvite()">Ready</button>
  </div>

  <div class="container hidden" id="invitePage">
    <h2>HAII NIAA</h2>
    <p>So, would you wanna go on our first date with me?</p>
    <div class="options">
      <button onclick="showDetails()">Yes</button>
      <button id="noBtn" onmouseover="moveNoBtn()">No</button>
    </div>
  </div>

  <div class="container hidden" id="detailsPage">
    <h2>Yayy 🎉</h2>
    <p>📅 Friday this week</p>
    <p>🕒 03.00 PM</p>
    <p>📍 Nuanu City</p>
    <p style="margin-top: 1.5rem; font-style: italic;">I'll pick you up. See ya! 🚗</p>
  </div>

  <script>
    const startPage = document.getElementById("startPage");
    const invitePage = document.getElementById("invitePage");
    const detailsPage = document.getElementById("detailsPage");
    const noBtn = document.getElementById("noBtn");

    function showInvite() {
      startPage.classList.add("hidden");
      invitePage.classList.remove("hidden");
    }

    function showDetails() {
      invitePage.classList.add("hidden");
      detailsPage.classList.remove("hidden");
      launchBalloons();
    }

    function moveNoBtn() {
      const container = invitePage;
      const maxX = container.clientWidth - noBtn.offsetWidth;
      const maxY = container.clientHeight - noBtn.offsetHeight;
      const randomX = Math.floor(Math.random() * maxX);
      const randomY = Math.floor(Math.random() * maxY);
      noBtn.style.position = "absolute";
      noBtn.style.left = `${randomX}px`;
      noBtn.style.top = `${randomY}px`;
    }

    function launchBalloons() {
      for (let i = 0; i < 30; i++) {
        const balloon = document.createElement('div');
        balloon.classList.add('balloon');
        balloon.style.left = Math.random() * 100 + 'vw';
        balloon.style.background = `hsl(${Math.random() * 360}, 70%, 80%)`;
        balloon.style.animationDuration = 4 + Math.random() * 4 + 's';
        document.body.appendChild(balloon);

        setTimeout(() => {
          balloon.remove();
        }, 8000);
      }
    }
  </script>
</body>
</html>
