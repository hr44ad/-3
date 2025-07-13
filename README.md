<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Animated Love Letter</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      background: #ffb6c1;
      height: 100vh;
      margin: 0;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      font-family: 'Segoe UI', 'Arial', sans-serif;
    }
    .container {
      position: relative;
      width: 320px;
      height: 300px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .envelope {
      position: absolute;
      width: 240px;
      height: 150px;
      cursor: pointer;
      z-index: 2;
      transition: transform 0.5s cubic-bezier(.4,2,.3,1), box-shadow 0.4s;
      box-shadow: 0 4px 20px 0 #d97a9b80;
    }
    .envelope.opened {
      transform: translateY(60px) scale(1.08);
      box-shadow: 0 2px 8px 0 #d97a9b80;
    }
    .envelope-top {
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 60px;
      background: #e75480;
      clip-path: polygon(0 100%, 50% 0, 100% 100%);
      transition: transform 0.7s cubic-bezier(.4,2,.3,1);
      z-index: 3;
    }
    .envelope.opened .envelope-top {
      transform: rotateX(80deg) scale(1.1);
      box-shadow: none;
    }
    .envelope-body {
      position: absolute;
      left: 0;
      top: 55px;
      width: 100%;
      height: 80px;
      background: #ff69b4;
      border-bottom-left-radius: 8px;
      border-bottom-right-radius: 8px;
      z-index: 2;
      border: 1px solid #e75480;
    }
    .envelope-bottom {
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 30px;
      background: #e75480;
      clip-path: polygon(0 0, 50% 100%, 100% 0);
      z-index: 2;
    }

    .letter {
      position: absolute;
      left: 50%;
      top: 80px;
      width: 180px;
      height: 110px;
      background: #fff;
      border-radius: 8px;
      box-shadow: 0 2px 8px #e7548050;
      text-align: center;
      padding: 30px 16px 16px 16px;
      font-size: 1.18rem;
      color: #e75480;
      opacity: 0;
      transform: translate(-50%, 50px) scale(0.9);
      z-index: 1;
      transition: opacity 0.7s, transform 0.7s cubic-bezier(.1,1,0,.9);
      pointer-events: none;
    }
    .letter.opened {
      opacity: 1;
      transform: translate(-50%, -100px) scale(1.02);
      pointer-events: auto;
    }
    .letter .close {
      position: absolute;
      top: 8px;
      right: 12px;
      font-size: 1.1rem;
      cursor: pointer;
      background: none;
      border: none;
      color: #e75480;
      font-weight: bold;
      transition: color 0.2s;
    }
    .letter .close:hover {
      color: #ff69b4;
    }

    /* Hearts animation */
    .hearts {
      position: absolute;
      left: 50%;
      bottom: 80px;
      width: 0;
      height: 0;
      pointer-events: none;
      z-index: 5;
    }
    .heart {
      position: absolute;
      left: -10px;
      bottom: 0;
      width: 26px;
      height: 24px;
      opacity: 0.8;
      animation: float 2.5s ease-in-out infinite;
      transform: scale(1);
    }
    .heart:nth-child(1) {
      animation-delay: 0s;
      left: -40px;
      width: 18px;
      opacity: 0.7;
    }
    .heart:nth-child(2) {
      animation-delay: 0.7s;
      left: 10px;
      width: 22px;
      opacity: 0.9;
    }
    .heart:nth-child(3) {
      animation-delay: 1.2s;
      left: 38px;
      width: 20px;
      opacity: 0.8;
    }

    @keyframes float {
      0% {
        transform: translateY(0) scale(1) rotate(-10deg);
        opacity: 0.9;
      }
      60% {
        opacity: 1;
      }
      90% {
        opacity: 0.6;
      }
      100% {
        transform: translateY(-120px) scale(1.3) rotate(10deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="envelope" id="envelope">
      <div class="envelope-top"></div>
      <div class="envelope-body"></div>
      <div class="envelope-bottom"></div>
    </div>
    <div class="letter" id="letter">
      <button class="close" id="closeLetter">&times;</button>
      <div>
        <h2 style="margin:0 0 10px 0;">My Love Letter</h2>
        <p style="margin:0;">
          You are the reason hearts flutter.<br>
          With you, every day feels special.<br>
          💖
        </p>
      </div>
    </div>
    <div class="hearts">
      <svg class="heart" viewBox="0 0 32 29.6"><path fill="#e41c38" d="M23.6,0c-2.7,0-5.1,1.6-6.6,4.1C15.5,1.6,13.1,0,10.4,0C4.7,0,0,4.7,0,10.4c0,7.6,11.5,15.7,15.1,18
      c0.7,0.5,1.7,0.5,2.4,0c3.6-2.3,15.1-10.4,15.1-18C32,4.7,27.3,0,23.6,0z"/></svg>
      <svg class="heart" viewBox="0 0 32 29.6"><path fill="#e41c38" d="M23.6,0c-2.7,0-5.1,1.6-6.6,4.1C15.5,1.6,13.1,0,10.4,0C4.7,0,0,4.7,0,10.4c0,7.6,11.5,15.7,15.1,18
      c0.7,0.5,1.7,0.5,2.4,0c3.6-2.3,15.1-10.4,15.1-18C32,4.7,27.3,0,23.6,0z"/></svg>
      <svg class="heart" viewBox="0 0 32 29.6"><path fill="#e41c38" d="M23.6,0c-2.7,0-5.1,1.6-6.6,4.1C15.5,1.6,13.1,0,10.4,0C4.7,0,0,4.7,0,10.4c0,7.6,11.5,15.7,15.1,18
      c0.7,0.5,1.7,0.5,2.4,0c3.6-2.3,15.1-10.4,15.1-18C32,4.7,27.3,0,23.6,0z"/></svg>
    </div>
  </div>
  <script>
    const envelope = document.getElementById('envelope');
    const letter = document.getElementById('letter');
    const closeBtn = document.getElementById('closeLetter');

    envelope.addEventListener('click', () => {
      envelope.classList.add('opened');
      letter.classList.add('opened');
    });

    closeBtn.addEventListener('click', () => {
      envelope.classList.remove('opened');
      letter.classList.remove('opened');
    });
  </script>
</body>
</html>
