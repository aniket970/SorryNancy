<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>I’m Sorry 🥺</title>

  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">

  <style>
    * { box-sizing: border-box; }

    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ffe4ec, #fff1f5);
      font-family: 'Poppins', sans-serif;
      overflow: hidden;
    }

    .heart {
      position: absolute;
      font-size: 20px;
      opacity: 0.6;
      animation: float 7s linear infinite;
    }

    @keyframes float {
      0% { transform: translateY(100vh); opacity: 0; }
      50% { opacity: 0.7; }
      100% { transform: translateY(-10vh); opacity: 0; }
    }

    .card {
      background: rgba(255,255,255,0.9);
      backdrop-filter: blur(10px);
      padding: 40px;
      border-radius: 30px;
      width: 360px;
      text-align: center;
      box-shadow: 0 30px 60px rgba(0,0,0,0.15);
      animation: pop 1s ease;
      z-index: 2;
    }

    @keyframes pop {
      from { transform: scale(0.85); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }

    h1 {
      color: #ff5c8a;
      margin-bottom: 10px;
    }

    p {
      color: #555;
      font-size: 16px;
      line-height: 1.5;
    }

    .buttons {
      margin-top: 30px;
      position: relative;
      height: 160px;
    }

    button {
      padding: 12px 26px;
      font-size: 15px;
      border-radius: 999px;
      border: none;
      cursor: pointer;
      position: absolute;
      transition: transform 0.25s ease, left 0.25s ease, top 0.25s ease;
      font-family: 'Poppins', sans-serif;
    }

    #forgive {
      background: linear-gradient(135deg, #ff7aa2, #ff9dbb);
      color: white;
      left: 40px;
      top: 60px;
      box-shadow: 0 10px 20px rgba(255,122,162,0.4);
      z-index: 2;
    }

    #still {
      background: #f2f2f2;
      color: #777;
      left: 200px;
      top: 60px;
      z-index: 1;
    }
  </style>
</head>
<body>

  <!-- Floating hearts -->
  <span class="heart" style="left:10%; animation-delay:0s;">💗</span>
  <span class="heart" style="left:30%; animation-delay:1s;">💞</span>
  <span class="heart" style="left:50%; animation-delay:2s;">🌸</span>
  <span class="heart" style="left:70%; animation-delay:3s;">💖</span>
  <span class="heart" style="left:90%; animation-delay:4s;">🌷</span>

  <div class="card">
    <h1>Hey Nancy 🥺</h1>
    <p>
      I know I messed up.<br>
      I didn’t mean to hurt you, and I genuinely feel bad about it.<br><br>
      I value you a lot, and I just wanted to say… I’m really sorry 💗
    </p>

    <div class="buttons">
      <button id="forgive" onclick="forgiven()">It’s okay 💖</button>
      <button id="still">I’m still upset 🥺</button>
    </div>
  </div>

  <script>
    const stillBtn = document.getElementById("still");
    const forgiveBtn = document.getElementById("forgive");
    const box = document.querySelector(".buttons");

    let forgiveScale = 1;

    function runAway() {
      const boxRect = box.getBoundingClientRect();
      const btnRect = stillBtn.getBoundingClientRect();

      const padding = 10;

      const maxX = boxRect.width - btnRect.width - padding;
      const maxY = boxRect.height - btnRect.height - padding;

      const x = Math.random() * maxX;
      const y = Math.random() * maxY;

      stillBtn.style.left = x + "px";
      stillBtn.style.top = y + "px";
      stillBtn.style.transform = "scale(0.7)";

      forgiveScale += 0.1;
      forgiveBtn.style.transform = `scale(${forgiveScale})`;
    }

    // Works better than mouseover
    stillBtn.addEventListener("pointerenter", runAway);
    stillBtn.addEventListener("touchstart", runAway);

    function forgiven() {
      document.body.innerHTML = `
        <div style="
          height:100vh;
          display:flex;
          justify-content:center;
          align-items:center;
          background:linear-gradient(135deg,#ff7aa2,#ff9dbb);
          font-family:Poppins;
          color:white;
          text-align:center;
        ">
          <div>
            <h1>Thank you 🥺💗</h1>
            <p style="font-size:20px;">
              I promise to do better.<br>
              You mean a lot to me 🌸
            </p>
          </div>
        </div>
      `;
    }
  </script>

</body>
</html>

