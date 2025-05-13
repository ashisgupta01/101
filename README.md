'/><!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Sorry Ankita 💝🥲🥺</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #fff0f5;
      text-align: center;
      padding: 50px;
      transition: background-color 0.8s;
    }
    #message {
      font-size: 26px;
      margin-bottom: 20px;
    }
    .btn {
      padding: 12px 24px;
      font-size: 18px;
      margin: 10px;
      cursor: pointer;
      border: none;
      border-radius: 8px;
      background-color: #ffb6c1;
      color: white;
      transition: background-color 0.3s;
    }
    .btn:hover { background-color: #ff69b4; }

    /* GIF styling */
    #stageGif {
      width: 180px;
      margin-top: 20px;
      opacity: 0;
    }

    /* ==== ANIMATIONS ==== */

    /* 1) INITIAL: scale & fade in */
    @keyframes popIn {
      0%   { transform: scale(0.5); opacity: 0; }
      100% { transform: scale(1);   opacity: 1; }
    }

    /* 2) REFUSAL #1: slide-from-left */
    @keyframes slideIn {
      0%   { transform: translateX(-200px); opacity: 0; }
      100% { transform: translateX(0);     opacity: 1; }
    }

    /* 3) REFUSAL #2: rotate & fade */
    @keyframes rotateIn {
      0%   { transform: rotate(-360deg); opacity: 0; }
      100% { transform: rotate(0);       opacity: 1; }
    }

    /* 4) REFUSAL #3: bounce */
    @keyframes bounceIn {
      0%   { transform: translateY(-200px); opacity: 0; }
      60%  { transform: translateY(30px);   opacity: 1; }
      80%  { transform: translateY(-10px);  }
      100% { transform: translateY(0);      }
    }

    /* 5) FINAL: pulse the button */
    @keyframes pulse {
      0%,100% { transform: scale(1); }
      50%     { transform: scale(1.1); }
    }

    /* moving "Nhi" button after 3rd refusal */
    #nhiBtn.move {
      position: relative;
      animation: dodge 1s infinite alternate ease-in-out;
    }
    @keyframes dodge {
      0%   { top: 0;    left: 0;   }
      25%  { top: -15px; left: 15px;}
      50%  { top: 15px;  left: -15px;}
      75%  { top: -15px; left: -15px;}
      100% { top: 15px;  left: 15px;}
    }

    /* helper to apply */
    .anim-popIn    { animation: popIn 0.6s ease forwards;    }
    .anim-slideIn  { animation: slideIn 0.6s ease forwards;  }
    .anim-rotateIn { animation: rotateIn 0.8s ease forwards; }
    .anim-bounceIn { animation: bounceIn 0.8s ease forwards; }
    .anim-pulse    { animation: pulse 1s infinite ease-in-out; }
    .gif-visible   { opacity: 1; }
  </style>
</head>
<body>

  <div id="message" class="anim-popIn">Soory Ankita 💝🥲🥺</div>
  <div id="buttons">
    <button id="yesBtn" class="btn">Thik hai</button>
    <button id="nhiBtn" class="btn">Nhi</button>
  </div>
  <img id="stageGif" src="" alt="cute cat gif" />

  <script>
    const stages = [
      { /* refusal 1 */
        text: "Please na mnn jao 😶‍🌫️🥲",
        bg: "#ffe4e1", color: "#ff1493",
        gif: "https://media.giphy.com/media/mlvseq9yvZhba/giphy.gif",
        animMsg: "anim-slideIn",
        animGif: "anim-popIn"
      },
      { /* refusal 2 */
        text: "Pylii mumma please maff kr do 😭🥺",
        bg: "#f0e68c", color: "#ff4500",
        gif: "https://media.giphy.com/media/MDJ9IbxxvDUQM/giphy.gif",
        animMsg: "anim-rotateIn",
        animGif: "anim-slideIn"
      },
      { /* refusal 3 */
        text: "Mnn bhi jao mummy 🥺 please naa 🫠",
        bg: "#dda0dd", color: "#8a2be2",
        gif: "https://media.giphy.com/media/13borq7Zo2kulO/giphy.gif",
        animMsg: "anim-bounceIn",
        animGif: "anim-rotateIn"
      }
    ];
    const final = {
      text: "Thank you pylii mumma 😁😋",
      bg: "#e0ffff", color: "#ff69b4",
      gif: "https://media.giphy.com/media/5xaOcLTKCcMp6Y0IE1K/giphy.gif",
      animMsg: "anim-popIn",
      animGif: "anim-bounceIn"
    };

    let stage = 0;
    const msg = document.getElementById('message');
    const nhi = document.getElementById('nhiBtn');
    const yes = document.getElementById('yesBtn');
    const gif = document.getElementById('stageGif');

    // attach handlers
    yes.addEventListener('click', () => handle(true));
    nhi.addEventListener('click', () => handle(false));

    function handle(isYes) {
      if (isYes) {
        // final slide
        applySlide(final);
        nhi.style.display = 'none';
        yes.classList.add('anim-pulse');
      } else if (stage < stages.length) {
        applySlide(stages[stage]);
        stage++;
        if (stage === stages.length) {
          nhi.classList.add('move');
        }
      }
    }

    function applySlide(data) {
      // message
      msg.textContent = data.text;
      msg.className = data.animMsg;
      // colors
      document.body.style.backgroundColor = data.bg;
      msg.style.color = data.color;
      // gif
      gif.src = data.gif;
      gif.className = data.animGif + ' gif-visible';
    }
  </script>

</body>
</html>
