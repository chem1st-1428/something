<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Confession Time!</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: #ffeef2;
      font-family: 'Comic Sans MS', cursive, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
      flex-direction: column;
    }

    h1 {
      text-align: center;
      font-size: 2em;
      color: #d14b8f;
      margin-bottom: 30px;
    }

    .btn {
      padding: 12px 24px;
      margin: 10px;
      border: none;
      border-radius: 12px;
      font-size: 1.2em;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    #yesBtn {
      background-color: #ff7eb9;
      color: white;
      z-index: 2;
    }

    #noBtn {
      background-color: #ccc;
      color: black;
      position: absolute;
      transition: all 0.3s ease;
      z-index: 1;
    }

    .hidden {
      display: none;
    }

    .fullscreen-yes {
      font-size: 3em !important;
      padding: 60px 120px !important;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      z-index: 10;
    }

    .loading {
      border: 6px solid #f3f3f3;
      border-top: 6px solid #ff7eb9;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      animation: spin 1s linear infinite;
      margin-top: 20px;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

  </style>
</head>
<body>

  <h1 id="question">ust wondering... do you feel the same spark I do?? 🥺</h1>
  <button class="btn" id="yesBtn">YES</button>
  <button class="btn" id="noBtn" style="top: 60%; left: 55%;">NO</button>

  <div id="message" class="hidden">
    <h1>😏 I KNEW IT!!!</h1>
    <div class="loading"></div>
  </div>

  <div id="final" class="hidden">
    <h1>How about we go on a study datee? 📚💞</h1>
    <button class="btn" style="background-color:#ff7eb9; color:white;">YESSS!! 😍</button>
  </div>

<div id="reveal" class="hidden">
  <h1>OKAY!!! Contact me if u already know who i am (obvious loh....)</h1>
  <p>- chem1st1428</p>
  <button class="btn" id="closeBtn" style="background-color:#888;">Close</button>
</div>

<div id="panic" class="hidden">
  <h1 style="color:#d14b8f;">Kamu kebiasaan ignoring me, please kali ini aja NOTICE ME 🥺 </h1>
</div>

  <script>
    let noClickCount = 0;
    const noBtn = document.getElementById('noBtn');
    const yesBtn = document.getElementById('yesBtn');
    const message = document.getElementById('message');
    const final = document.getElementById('final');
    const question = document.getElementById('question');

    noBtn.addEventListener('mouseover', () => {
      if (noClickCount === 0) {
        noBtn.style.top = `${Math.random() * 80 + 10}%`;
        noBtn.style.left = `${Math.random() * 80 + 10}%`;
      }
    });

    noBtn.addEventListener('click', () => {
      noClickCount++;
      if (noClickCount === 1) {
        // do nothing, just avoid
      } else if (noClickCount === 2) {
        yesBtn.style.transform = "scale(1.3)";
      } else if (noClickCount === 3) {
        yesBtn.style.transform = "scale(1.6)";
      } else if (noClickCount === 4) {
        yesBtn.classList.add('fullscreen-yes');
        noBtn.classList.add('hidden');
        question.classList.add('hidden');
        setTimeout(() => {
          yesBtn.classList.add('hidden');
          message.classList.remove('hidden');
          setTimeout(() => {
            message.classList.add('hidden');
            final.classList.remove('hidden');
          }, 3000); // loading duration
        }, 1500); // delay before showing message
      }
       // Tambahan di JS bagian bawah
final.querySelector('button').addEventListener('click', () => {
  final.classList.add('hidden');
  document.getElementById('reveal').classList.remove('hidden');
});

// Tombol close diklik
document.getElementById('closeBtn').addEventListener('click', () => {
  document.getElementById('reveal').classList.add('hidden');
  document.getElementById('panic').classList.remove('hidden');
});

    });
  </script>
</body>
</html>
