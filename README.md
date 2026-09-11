<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Birthday My Love! ❤️</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Poppins', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #ff758c, #ff7eb3, #764ba2);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      color: #fff;
      overflow-x: hidden;
    }

    /* Floating Hearts Background Animation */
    .heart {
      position: fixed;
      font-size: 1.5rem;
      color: rgba(255, 255, 255, 0.6);
      animation: floatUp 6s linear infinite;
      z-index: 1;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(100vh) scale(0.5);
        opacity: 1;
      }
      100% {
        transform: translateY(-10vh) scale(1.2);
        opacity: 0;
      }
    }

    .card-container {
      position: relative;
      z-index: 10;
      background: rgba(255, 255, 255, 0.15);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border-radius: 25px;
      padding: 30px 20px;
      max-width: 450px;
      width: 100%;
      text-align: center;
      box-shadow: 0 10px 40px rgba(0, 0, 0, 0.25);
      border: 1px solid rgba(255, 255, 255, 0.3);
    }

    h1 {
      font-size: 2.2rem;
      color: #ffffff;
      margin-bottom: 5px;
      text-shadow: 0 0 15px rgba(255, 255, 255, 0.6);
    }

    .subtitle {
      font-size: 1rem;
      color: #ffeaa7;
      margin-bottom: 20px;
      font-style: italic;
    }

    /* Image Wrapper */
    .photo-frame {
      position: relative;
      width: 100%;
      height: 380px;
      border-radius: 18px;
      overflow: hidden;
      margin-bottom: 20px;
      box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
      border: 3px solid rgba(255, 255, 255, 0.5);
    }

    .photo-frame img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.5s ease;
    }

    .photo-frame:hover img {
      transform: scale(1.05);
    }

    /* Message Area */
    .love-message {
      background: rgba(0, 0, 0, 0.25);
      padding: 20px;
      border-radius: 15px;
      font-size: 0.95rem;
      line-height: 1.7;
      margin-bottom: 20px;
      text-align: center;
    }

    /* Buttons */
    .btn-group {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .btn {
      background: #ff4757;
      color: white;
      border: none;
      padding: 12px 20px;
      font-size: 1rem;
      font-weight: bold;
      border-radius: 30px;
      cursor: pointer;
      box-shadow: 0 4px 15px rgba(255, 71, 87, 0.4);
      transition: all 0.3s ease;
    }

    .btn:hover {
      transform: translateY(-2px);
      background: #ff6b81;
    }

    .btn-secondary {
      background: rgba(255, 255, 255, 0.2);
      border: 1px solid rgba(255, 255, 255, 0.5);
    }

    .btn-secondary:hover {
      background: rgba(255, 255, 255, 0.35);
    }

    /* Hidden Surprise Box */
    #surprise-box {
      display: none;
      margin-top: 15px;
      padding: 15px;
      background: rgba(255, 234, 167, 0.25);
      border: 1px dashed #ffeaa7;
      border-radius: 12px;
      font-size: 0.9rem;
      animation: fadeIn 0.6s ease-in-out forwards;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

  <!-- Floating Hearts Container -->
  <div id="hearts-container"></div>

  <div class="card-container">
    <h1>Happy Birthday! 💕</h1>
    <p class="subtitle">Untuk orang paling spesial di hidupku</p>

    <!-- Foto Bermain Gitar -->
    <div class="photo-frame">
      <img id="myPhoto" src="https://lh3.googleusercontent.com/d/1X4aH7qH2fR9L4g9k5R8u8M7A2L1k0aB3=s800" alt="Foto Bermain Gitar">
    </div>

    <!-- Pesan Ulang Tahun -->
    <div class="love-message">
      <p>Selamat ulang tahun sayang! 🎂✨<br>
      Terima kasih sudah selalu ada, bikin hari-hariku jadi lebih berwarna, dan bikin aku bahagia setiap hari. Semoga di usiamu yang baru ini, kamu makin sukses, sehat selalu, dan semua impianmu tercapai. I love you in every universe! ❤️</p>
    </div>

    <div class="btn-group">
      <button class="btn" onclick="toggleSurprise()">Buka Pesan Rahasia 💌</button>
      <button class="btn btn-secondary" onclick="playMusic()">Putar Musik 🎵</button>
    </div>

    <!-- Pesan Rahasia -->
    <div id="surprise-box">
      <p>🎁 <b>Janji Buat Kamu:</b><br>
      "Aku bakal selalu mendukungmu dalam situasi apa pun, mendengarkan semua ceritamu, dan selalu ada buat kamu. Tetap jadi dirimu yang mengagumkan ya!" 🥰</p>
    </div>
  </div>

  <!-- Audio Musik (Paul Partohap - P.S. I Love You) -->
  <audio id="bgMusic" loop>
    <source src="https://files.catbox.moe/97a22m.mp3" type="audio/mpeg">
  </audio>

  <script>
    // 1. Efek Hati Melayang di Background
    function createHeart() {
      const heart = document.createElement('div');
      heart.classList.add('heart');
      heart.innerHTML = '❤️';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = (Math.random() * 3 + 3) + 's';
      document.getElementById('hearts-container').appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 6000);
    }
    setInterval(createHeart, 400);

    // 2. Toggle Pesan Rahasia
    function toggleSurprise() {
      const box = document.getElementById('surprise-box');
      if (box.style.display === 'block') {
        box.style.display = 'none';
      } else {
        box.style.display = 'block';
      }
    }

    // 3. Play / Pause Musik
    function playMusic() {
      const music = document.getElementById('bgMusic');
      if (music.paused) {
        music.play();
        alert('🎵 Memutar lagu: Paul Partohap - P.S. I Love You ❤️');
      } else {
        music.pause();
      }
    }
  </script>
</body>
</html>
