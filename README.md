<Valentine'sDay💓>
<html>
<head>
  <meta charset="UTF-8">
  <title>Valentine 💘</title>

  <style>
    body {
      margin: 0;
      height: 100vh;
      background: linear-gradient(135deg, #ff758c, #ff7eb3);
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      font-family: Arial, sans-serif;
    }

    .box {
      text-align: center;
      position: relative;
    }

    h1 {
      color: white;
      margin-bottom: 20px;
    }

    button {
      padding: 14px 30px;
      font-size: 18px;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      margin: 10px;
      transition: all 0.4s ease;
    }

    #yes {
      background: red;
      color: white;
      z-index: 2;
    }

    #no {
      background: black;
      color: white;
      position: absolute;
      left: 120px;
    }

    #hiddenYes {
      display: none;
      position: absolute;
      bottom: -120px;
      left: 50%;
      transform: translateX(-50%);
      background: gold;
      color: black;
    }

    .emoji {
      position: absolute;
      font-size: 30px;
      animation: float 2s linear forwards;
    }

    @keyframes float {
      from { transform: translateY(0); opacity: 1; }
      to { transform: translateY(-220px); opacity: 0; }
    }
  </style>
</head>

<body>

  <audio id="music" loop>
    <source src="https://files.catbox.moe/9h4h2k.mp3" type="audio/mpeg">
  </audio>

  <div class="box">
    <h1 id="question">Will you be my Valentine on 14th Feb 2026, Daline? 💖</h1>
    <button id="yes">Yes 💘</button>
    <button id="no">No 🙃</button>
    <button id="hiddenYes">Okay fine… YES 😳</button>
  </div>

  <script>
    const questions = [
      "Will you be my Valentine on 14th Feb 2026, Daline? 💖",
      "Are you sure? 😳",
      "Really really sure? 🥺",
      "Do you love me the way I love you? ❤️",
      "Last chance… Daline? 😏"
    ];

    let qIndex = 0;
    let noCount = 0;

    const q = document.getElementById("question");
    const yes = document.getElementById("yes");
    const no = document.getElementById("no");
    const hiddenYes = document.getElementById("hiddenYes");
    const music = document.getElementById("music");

    document.body.addEventListener("click", () => {
      music.play().catch(() => {});
    }, { once: true });

    yes.onclick = () => {
      celebration();
      qIndex++;

      if (qIndex < questions.length) {
        q.innerText = questions[qIndex];
      } else {
        q.innerText = "YAY 💖 THANK YOU FOR BEING MY VALENTINE, DALINE ❤️🫶🧸";
        yes.style.display = "none";
        no.style.display = "none";
        hiddenYes.style.display = "none";
      }
    };

    hiddenYes.onclick = yes.onclick;

    no.onmouseover = no.onclick = () => {
      noCount++;

      // 1st NO: button runs
      if (noCount === 1) {
        move(no);
      }

      // 2nd NO: YES grows big
      else if (noCount === 2) {
        yes.style.transform = "scale(2)";
        move(no);
      }

      // 3rd NO: YES takes over screen
      else if (noCount === 3) {
        yes.style.transform = "scale(6)";
        q.innerText = "Just press YES already 😭❤️";
        move(no);
      }

      // 4th NO: buttons run away, hidden YES appears
      else {
        yes.style.display = "none";
        no.style.display = "none";
        hiddenYes.style.display = "block";
        q.innerText = "Okay… find the right button 👀";
      }
    };

    function move(btn) {
      btn.style.left = Math.random() * (window.innerWidth - 100) + "px";
      btn.style.top = Math.random() * (window.innerHeight - 100) + "px";
    }

    function celebration() {
      const emojis = ["❤️", "💖", "💘", "🧸", "🥰", "✨"];
      for (let i = 0; i < 15; i++) {
        const e = document.createElement("div");
        e.className = "emoji";
        e.innerText = emojis[Math.floor(Math.random() * emojis.length)];
        e.style.left = Math.random() * window.innerWidth + "px";
        e.style.top = window.innerHeight + "px";
        document.body.appendChild(e);
        setTimeout(() => e.remove(), 2000);
      }
    }
  </script>

</body>
</html>
