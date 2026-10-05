<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pesan Khusus Untuk Kak Salsa dari Fernan</title>
  <!-- Google Fonts: Poppins -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <!-- Library untuk Efek Kembang Api/Confetti -->
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <style>
    /* RESET & DASAR */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background: linear-gradient(135deg, #a1c4fd 0%, #c2e9fb 50%, #fbc2eb 100%);
      color: #334155;
      font-family: 'Poppins', 'Segoe UI', sans-serif;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow-x: hidden;
      padding: 20px;
      position: relative;
    }

    /* PARTIKEL LINGKARAN/BINTANG CERAH */
    .bg-particles {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
    }

    .bubble {
      position: absolute;
      background: rgba(255, 255, 255, 0.65);
      border-radius: 50%;
      animation: floatBubble 4s infinite ease-in-out alternate;
      will-change: transform, opacity;
    }

    @keyframes floatBubble {
      0% { transform: translateY(0) scale(0.8); opacity: 0.5; }
      100% { transform: translateY(-25px) scale(1.2); opacity: 0.95; }
    }

    /* HIASAN BADGE ATAS CERAH */
    .ribbon {
      position: absolute;
      top: -15px;
      background: linear-gradient(135deg, #ff758c, #ff7eb3);
      color: #fff;
      font-weight: 800;
      font-size: 0.85rem;
      padding: 6px 22px;
      border-radius: 20px;
      box-shadow: 0 4px 15px rgba(255, 117, 140, 0.4);
      letter-spacing: 1px;
      text-transform: uppercase;
      z-index: 20;
    }

    /* KARTU UTAMA CERAH (GLASSMORPHISM TERANG) */
    .card {
      position: relative;
      z-index: 10;
      background: rgba(255, 255, 255, 0.82);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 2px solid rgba(255, 255, 255, 0.95);
      border-radius: 28px;
      padding: 40px 25px 30px 25px;
      max-width: 550px;
      width: 100%;
      text-align: center;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.08), 0 0 25px rgba(255, 255, 255, 0.9);
      display: flex;
      flex-direction: column;
      align-items: center;
      animation: cardInit 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards;
      will-change: transform, opacity;
    }

    @keyframes cardInit {
      0% { opacity: 0; transform: translateY(20px) scale(0.96); }
      100% { opacity: 1; transform: translateY(0) scale(1); }
    }

    .header-icon {
      font-size: 58px;
      margin-bottom: 8px;
      display: inline-block;
      transition: transform 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
      will-change: transform;
    }

    .header-icon.bounce {
      transform: scale(1.35) rotate(15deg);
    }

    h1 {
      font-size: 2.1rem;
      background: linear-gradient(90deg, #ff4e50, #f9d423, #00c6ff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      margin-bottom: 6px;
      font-weight: 800;
      transition: all 0.4s ease;
    }

    .subtitle {
      color: #64748b;
      font-size: 0.98rem;
      margin-bottom: 25px;
      font-weight: 500;
      transition: all 0.3s ease;
    }

    /* AREA PESAN BERTAHAP */
    .message-container {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin-bottom: 25px;
      width: 100%;
    }

    /* BOX PESAN TEMA TERANG DENGAN ANIMASI HALUS */
    .msg-box {
      background: #ffffff;
      border-radius: 20px;
      padding: 20px;
      border: 2px solid #e0f2fe;
      text-align: left;
      line-height: 1.65;
      color: #334155;
      font-size: 0.96rem;
      display: none;
      opacity: 0;
      box-shadow: 0 6px 18px rgba(0, 0, 0, 0.04);
      will-change: transform, opacity;
    }

    .msg-box.show {
      display: block;
      animation: smoothSlideIn 0.65s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    }

    @keyframes smoothSlideIn {
      0% {
        opacity: 0;
        transform: translateY(25px) scale(0.94);
      }
      100% {
        opacity: 1;
        transform: translateY(0) scale(1);
      }
    }

    .msg-box.highlight {
      background: #fff5f7;
      border-color: #fecdd3;
    }

    .chinese-text {
      background: #f0fdf4;
      border-left: 4px solid #22c55e;
      padding: 12px 14px;
      border-radius: 10px;
      margin-top: 12px;
      font-size: 0.92rem;
      color: #15803d;
      box-shadow: 0 2px 8px rgba(34, 197, 94, 0.08);
    }

    .contact-box {
      margin-top: 15px;
      background: #f0f9ff;
      border: 1px dashed #0284c7;
      padding: 12px;
      border-radius: 12px;
      text-align: center;
      color: #0369a1;
      font-size: 0.9rem;
    }

    .wa-btn {
      display: inline-block;
      margin-top: 8px;
      background: #25d366;
      color: white;
      padding: 8px 18px;
      border-radius: 20px;
      text-decoration: none;
      font-weight: 700;
      font-size: 0.85rem;
      box-shadow: 0 4px 12px rgba(37, 211, 102, 0.3);
      transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), box-shadow 0.3s ease;
      will-change: transform;
    }

    .wa-btn:hover {
      transform: translateY(-2px) scale(1.05);
      box-shadow: 0 6px 16px rgba(37, 211, 102, 0.45);
    }

    /* SALAM HANGAT DARI FERNAN */
    .sender-tag {
      margin-top: 15px;
      padding-top: 12px;
      border-top: 1px dashed #f43f5e;
      text-align: right;
      font-style: italic;
      color: #e11d48;
      font-weight: 700;
      font-size: 0.95rem;
    }

    /* TOMBOL CERAH INTERAKTIF HALUS */
    .btn-main {
      background: linear-gradient(135deg, #38ef7d 0%, #11998e 100%);
      color: #fff;
      border: none;
      padding: 15px 36px;
      font-size: 1.05rem;
      font-weight: 800;
      border-radius: 30px;
      cursor: pointer;
      transition: transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1), 
                  box-shadow 0.4s ease, 
                  background 0.4s ease;
      box-shadow: 0 6px 20px rgba(17, 153, 142, 0.35);
      will-change: transform;
    }

    .btn-main:hover {
      transform: translateY(-3px) scale(1.05);
      box-shadow: 0 10px 25px rgba(17, 153, 142, 0.5);
    }

    .btn-main:active {
      transform: scale(0.96);
    }

    /* EMOJI MELAYANG HALUS */
    .floating-emoji {
      position: absolute;
      pointer-events: none;
      animation: floatUp 3s cubic-bezier(0.25, 1, 0.5, 1) forwards;
      font-size: 30px;
      z-index: 20;
      will-change: transform, opacity;
    }

    @keyframes floatUp {
      0% { opacity: 1; transform: translateY(0) scale(0.8); }
      100% { opacity: 0; transform: translateY(-200px) scale(1.5); }
    }
  </style>
</head>
<body>

  <!-- Background Bubble Cerah -->
  <div class="bg-particles" id="bubbles"></div>

  <div class="card">
    <div class="ribbon">Special Message ✨</div>

    <div class="header-icon" id="header-icon">💌✨</div>
    <h1 id="main-title">To Kak Salsa</h1>
    <p class="subtitle" id="sub-title">Klik tombol hijau di bawah untuk buka surat...</p>

    <!-- Kontainer Pesan Bertahap -->
    <div class="message-container">
      
      <!-- Bagian 1 -->
      <div class="msg-box" id="msg-1">
        ✨ Berasa cepet banget, tau-tau Kak Salsa udah mau kembali ke kampus aja, padahal baru masuk berapa hari. Tapi meski singkat belajar sama Kak Salsa SERU, dan asik diajak bercanda. Makasih ya kak buat ilmunya. Seru bisa kenal dan diajar Kak Salsa dan teman-teman PLP dari UMP.<br><br>
        🌸 <strong>Pesan Titipan:</strong><br>
        Oiya Kak Salsa, bantu ucapin juga makasih dan selamat tinggal buat Kak Anas, Kak Hana, dan Kak Tarysa yaa!
      </div>

      <!-- Bagian 2 -->
      <div class="msg-box" id="msg-2">
        📚 <strong>Pesan Dari Aku:</strong><br>
        Semangat terus Kak Salsa dan teman-teman dari UMP! Sukses terus ya Kak buat kuliahnya di kampus. Semangat terus buat ngadepin tugas-tugas kuliah. Semoga nanti Kak Salsa dan teman-teman dari UMP bisa lulus dengan IPK sempurna! 🔥🎓
      </div>

      <!-- Bagian 3 -->
      <div class="msg-box highlight" id="msg-3">
        <strong>Sukses selalu Kak Salsa dan kawan-kawan dari UMP! ✨💖🌟</strong>

        <!-- Ucapan Mandarin -->
        <div class="chinese-text">
          🇨🇳 <strong>Mandarin Goodbye & Wishes:</strong><br>
          • <strong>再见 (Zàijiàn)</strong> — <em>Sampai Jumpa / Goodbye!</em><br>
          • <strong>祝你一路顺风，学业有成！</strong><br>
          (<em>Zhù nǐ yīlù shùnfēng, xuéyè yǒuchéng!</em>)<br>
          👉 Artinya: Semoga perjalananmu lancar & sukses selalu dalam studinya! 🎓✨
        </div>

        <!-- Nomor Telepon & WhatsApp -->
        <div class="contact-box">
          📱 <strong>Kontak Fernan:</strong><br>
          <span>0882007463795</span><br>
          <a href="https://wa.me/62882007463795" target="_blank" class="wa-btn">💬 Chat via WhatsApp</a>
        </div>
        
        <div class="sender-tag">
          Salam hangat,<br>
          ~ Fernan ✍️✨
        </div>
      </div>

    </div>

    <!-- Tombol Utama -->
    <button class="btn-main" id="action-btn" onclick="nextStep()">Buka Pesan 👆</button>
  </div>

  <script>
    // Bikin Bubble Latar Belakang Cerah
    const bubblesContainer = document.getElementById('bubbles');
    for (let i = 0; i < 35; i++) {
      const bubble = document.createElement('div');
      bubble.classList.add('bubble');
      const size = Math.random() * 20 + 10;
      bubble.style.width = size + 'px';
      bubble.style.height = size + 'px';
      bubble.style.top = Math.random() * 100 + '%';
      bubble.style.left = Math.random() * 100 + '%';
      bubble.style.animationDelay = Math.random() * 3 + 's';
      bubblesContainer.appendChild(bubble);
    }

    let step = 0;

    function nextStep() {
      step++;
      const icon = document.getElementById('header-icon');
      
      icon.classList.add('bounce');
      setTimeout(() => icon.classList.remove('bounce'), 500);

      if (step === 1) {
        document.getElementById('msg-1').classList.add('show');
        document.getElementById('main-title').innerText = "Terima Kasih Kak Salsa! ❤️";
        document.getElementById('sub-title').innerText = "Klik lagi untuk lanjut membaca...";
        icon.innerText = "💖";
        
        triggerConfetti();
        createEmojis(['❤️', '✨', '🎓', '🌸']);

      } else if (step === 2) {
        document.getElementById('msg-2').classList.add('show');
        document.getElementById('sub-title').innerText = "Klik lagi untuk ucapan spesial!";
        icon.innerText = "📚";

        triggerConfetti();
        createEmojis(['🌟', '📚', '💪', '🔥', '🌈']);

      } else if (step === 3) {
        document.getElementById('msg-3').classList.add('show');
        document.getElementById('main-title').innerText = "Sukses Selalu Kak Salsa! 🎓🤲";
        document.getElementById('sub-title').innerText = "Dari Fernan untuk Kak Salsa & Teman-Teman UMP!";
        icon.innerText = "🥳";
        
        const btn = document.getElementById('action-btn');
        btn.innerText = "Pesta Kembang Api! 🎉";
        btn.style.background = "linear-gradient(135deg, #ff758c 0%, #ff7eb3 100%)";
        btn.style.boxShadow = "0 6px 20px rgba(255, 117, 140, 0.4)";

        triggerBigConfetti();
        createEmojis(['🤲', '💖', '🎉', '✨', '✍️', '🌻']);

      } else {
        triggerBigConfetti();
        createEmojis(['🎉', '✨', '💖', '✍️', '🔥', '🌈']);
      }
    }

    function triggerConfetti() {
      confetti({
        particleCount: 50,
        spread: 70,
        origin: { y: 0.7 }
      });
    }

    function triggerBigConfetti() {
      confetti({
        particleCount: 120,
        spread: 100,
        origin: { y: 0.6 }
      });
    }

    function createEmojis(emojiList) {
      emojiList.forEach((symbol, index) => {
        setTimeout(() => {
          const emoji = document.createElement('div');
          emoji.classList.add('floating-emoji');
          emoji.innerText = symbol;
          emoji.style.left = Math.random() * 80 + 10 + '%';
          emoji.style.bottom = '30%';
          document.body.appendChild(emoji);

          setTimeout(() => {
            emoji.remove();
          }, 3000);
        }, index * 150);
      });
    }
  </script>
</body>
</html>
