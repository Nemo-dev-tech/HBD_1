<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>💌 Happy Birthday เพื่อนสาว 💌</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Prompt:wght@400;600&display=swap');

    body {
      font-family: 'Prompt', sans-serif;
      background: linear-gradient(135deg, #ffe6f0, #fff0f6);
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
    }

    /* ลูกโป่ง/ฟองสบู่ */
    .balloon, .confetti {
      position: absolute;
      border-radius: 50%;
      opacity: 0.7;
      animation: floatUp linear infinite;
    }

    .balloon { width: 40px; height: 60px; background: radial-gradient(circle at 50% 30%, #ff66b3, #ffb3d9);}
    .confetti { width: 10px; height: 10px; background: #ffcc00;}

    @keyframes floatUp {
      0% { transform: translateY(100vh) rotate(0deg); opacity: 0.8; }
      100% { transform: translateY(-100px) rotate(360deg); opacity: 0; }
    }

    .envelope {
      position: relative;
      width: 300px;
      height: 200px;
      background: #ffb3d9;
      border-radius: 10px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      transition: transform 0.6s ease;
      transform-style: preserve-3d;
      z-index: 10;
    }

    .flap {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 50%;
      background: #ff66b3;
      clip-path: polygon(0 0, 100% 0, 50% 100%);
      transition: transform 0.6s ease;
      transform-origin: top;
      z-index: 2;
    }

    .message {
      display: none;
      background: #fff0f5;
      padding: 20px;
      border-radius: 15px;
      text-align: center;
      box-shadow: 0 8px 20px rgba(255, 102, 179, 0.4);
      max-width: 350px;
      transform: translateY(-50px);
      animation: popUp 0.8s ease forwards;
      z-index: 5;
      position: relative;
    }

    .message h2 {
      color: #e60073;
      margin-bottom: 10px;
    }

    .message p {
      color: #333;
      font-size: 16px;
      line-height: 1.6;
    }

    .youtube-player {
      width: 100%;
      height: 180px;
      border: none;
      border-radius: 10px;
      margin-top: 10px;
      display: none;
    }

    @keyframes popUp {
      0% { opacity: 0; transform: translateY(-50px) scale(0.5); }
      60% { transform: translateY(0) scale(1.1); }
      100% { opacity: 1; transform: translateY(0) scale(1); }
    }
  </style>
</head>
<body>

  <!-- เอฟเฟคฟองสบู่/ลูกโป่ง -->
  <div id="effects"></div>

  <!-- ซอง -->
  <div class="envelope" id="envelope">
    <div class="flap" id="flap"></div>
  </div>

  <!-- ข้อความ + YouTube -->
  <div class="message" id="message">
    <h2>🎉 สุขสันต์วันเกิดนะจ้ะ 🎉</h2>
    <p>ขอให้มีความสุขทุกวัน<br>
       สนุกสนานกับชีวิต 💖<br>
         สมหวังทุกอย่าง 🌸🎂🎁</p>
    <iframe id="yt-player" class="youtube-player" 
            src="" 
            allow="autoplay; encrypted-media" 
            allowfullscreen></iframe>
  </div>

  <script>
    const envelope = document.getElementById("envelope");
    const flap = document.getElementById("flap");
    const message = document.getElementById("message");
    const ytPlayer = document.getElementById("yt-player");
    const effectsContainer = document.getElementById("effects");

    const youtubeURL = "https://www.youtube.com/embed/EjtxTX_VjxE?autoplay=1&loop=1&playlist=EjtxTX_VjxE";

    // สร้างลูกโป่งและ confetti
    for(let i=0;i<30;i++){
      const b = document.createElement("div");
      b.classList.add(Math.random()<0.7?"balloon":"confetti");
      b.style.left = Math.random()*100 + "vw";
      b.style.animationDuration = (4 + Math.random()*4) + "s";
      b.style.width = (10 + Math.random()*30) + "px";
      b.style.height = (10 + Math.random()*30) + "px";
      effectsContainer.appendChild(b);
    }

    envelope.addEventListener("click", () => {
      flap.style.transform = "rotateX(-180deg)";
      setTimeout(() => {
        envelope.style.display = "none";
        message.style.display = "block";
        ytPlayer.src = youtubeURL;
        ytPlayer.style.display = "block";
      }, 600);
    });
  </script>
</body>
</html>
