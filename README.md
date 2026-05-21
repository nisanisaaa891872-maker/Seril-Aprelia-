<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ruang Sandaran Hati</title>
    <style>
        /* Menggunakan font yang lembut dan ramah */
        @import url('https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700&display=swap');

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Nunito', sans-serif;
        }

        body {
            background-color: #F4F9F4; /* Putih dengan sedikit sentuhan hijau pastel halus */
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
            position: relative;
        }

        /* Desain Kartu Utama */
        .card {
            background-color: #FFFFFF; /* Putih Bersih */
            padding: 40px 30px;
            border-radius: 24px;
            box-shadow: 0 10px 30px rgba(46, 117, 89, 0.1);
            text-align: center;
            max-width: 450px;
            width: 90%;
            border: 4px solid #E8F5E9; /* Frame hijau sangat muda */
            position: relative;
            z-index: 10;
        }

        h1 {
            color: #1B4332; /* Hijau Tua yang Tegas namun Teduh */
            font-size: 1.6rem;
            margin-bottom: 15px;
            line-height: 1.4;
        }

        p {
            color: #52B788; /* Hijau Daun yang Menenangkan */
            font-size: 1rem;
            margin-bottom: 30px;
            font-weight: 600;
        }

        /* Area Tombol */
        .btn-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            height: 50px;
            position: relative;
        }

        .btn {
            padding: 12px 35px;
            font-size: 1rem;
            font-weight: 700;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: transform 0.2s, background-color 0.2s;
            box-shadow: 0 4px 10px rgba(46, 117, 89, 0.15);
        }

        .btn-oke {
            background-color: #2D6A4F; /* Hijau Utama */
            color: #FFFFFF;
        }

        .btn-oke:hover {
            background-color: #1B4332;
            transform: scale(1.05);
        }

        /* Tombol Tidak menggunakan posisi absolut agar bisa menghindar */
        .btn-tidak {
            background-color: #FFFFFF;
            color: #74C69D;
            border: 2px solid #74C69D;
            position: absolute;
            left: 55%; /* Posisi awal di samping tombol Oke */
        }

        /* Pesan Pop-up Sukses */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(27, 67, 50, 0.3);
            backdrop-filter: blur(5px);
            justify-content: center;
            align-items: center;
            z-index: 100;
        }

        .modal-content {
            background-color: #FFFFFF;
            padding: 40px;
            border-radius: 24px;
            text-align: center;
            max-width: 420px;
            width: 85%;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            border: 4px solid #74C69D;
            animation: popIn 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        @keyframes popIn {
            0% { transform: scale(0.7); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .modal-content h2 {
            color: #2D6A4F;
            margin-bottom: 15px;
            font-size: 1.5rem;
        }

        .modal-content p {
            color: #40916C;
            font-weight: 400;
            line-height: 1.6;
            margin-bottom: 25px;
        }

        /* Dekorasi Stiker Hati & Kedamaian (Floating Emojis) */
        .sticker {
            position: absolute;
            font-size: 2.5rem;
            user-select: none;
            pointer-events: none;
            opacity: 0.7;
            animation: float 4s ease-in-out infinite alternate;
        }

        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); }
            100% { transform: translateY(-20px) rotate(15deg); }
        }

        /* Mengatur sebaran posisi stiker di latar belakang */
        .s1 { top: 10%; left: 8%; animation-delay: 0s; }
        .s2 { top: 12%; right: 10%; animation-delay: 0.7s; }
        .s3 { bottom: 15%; left: 12%; animation-delay: 1.2s; }
        .s4 { bottom: 10%; right: 8%; animation-delay: 0.3s; }
        .s5 { top: 48%; left: 4%; animation-delay: 1.8s; }
        .s6 { top: 52%; right: 5%; animation-delay: 2.2s; }
    </style>
</head>
<body>

    <!-- Stiker Pendukung Tema Curhat & Hati -->
    <div class="sticker s1">💚</div>
    <div class="sticker s2">✨</div>
    <div class="sticker s3">🌈</div>
    <div class="sticker s4">🌱</div>
    <div class="sticker s5">☁️</div>
    <div class="sticker s6">🤗</div>

    <!-- Kartu Interaktif Utama -->
    <div class="card">
        <h1>Hari ini rasanya melelahkan ya? Mau dengar satu rahasia kecil untuk hatimu? 🕊️</h1>
        <p>Klik "Oke" untuk membuka pesannya...</p>
        
        <div class="btn-container" id="btnContainer">
            <button class="btn btn-oke" onclick="tampilkanPesan()">Oke</button>
            <button class="btn btn-tidak" id="btnTidak" onmouseover="hindariTombol()" onclick="hindariTombol()">Tidak</button>
        </div>
    </div>

    <!-- Modal Pesan Bijak / Saran Hati -->
    <div class="modal" id="modalPesan">
        <div class="modal-content">
            <h2>Ingatlah Ini Baik-baik... 💚</h2>
            <p>"Tidak apa-apa jika hari ini tidak berjalan sempurna. Kamu sudah berusaha sangat hebat sejauh ini. Izinkan hatimu beristirahat sejenak, karena hari esok selalu membawa harapan dan kekuatan yang baru untukmu."</p>
            <button class="btn btn-oke" onclick="tutupModal()">Terima Kasih</button>
        </div>
    </div>

    <script>
        const btnTidak = document.getElementById('btnTidak');
        const modalPesan = document.getElementById('modalPesan');

        // Fungsi membuat tombol "Tidak" kabur secara acak
        function hindariTombol() {
            const padding = 30; // Jarak aman dari tepi layar
            const batasX = window.innerWidth - btnTidak.offsetWidth - padding;
            const batasY = window.innerHeight - btnTidak.offsetHeight - padding;

            // Menghitung koordinat acak di dalam layar browser
            const acakX = Math.max(padding, Math.floor(Math.random() * batasX));
            const acakY = Math.max(padding, Math.floor(Math.random() * batasY));

            // Mengubah sistem posisi tombol menjadi fixed agar bebas berpindah tempat
            btn離開 = false;
            btnTidak.style.position = 'fixed';
            btnTidak.style.left = acakX + 'px';
            btnTidak.style.top = acakY + 'px';
        }

        // Menampilkan pesan positif
        function tampilkanPesan() {
            modalPesan.style.display = 'flex';
        }

        // Menutup pesan dan mengembalikan posisi awal tombol "Tidak"
        function tutupModal() {
            modalPesan.style.display = 'none';
            
            // Mengembalikan tombol "Tidak" ke tempat semula di dalam kartu
            btnTidak.style.position = 'absolute';
            btnTidak.style.left = '55%';
            btnTidak.style.top = '0';
        }
    </script>
</body>
</html>
# Seril-Aprelia-
