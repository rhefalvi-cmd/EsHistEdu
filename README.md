<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EsHist - Sejarah Pergerakan Nasional</title>
    <style>
        :root {
            --primary: #004d40;
            --secondary: #00796b;
            --light: #e0f2f1;
            --dark: #00251a;
            --accent: #ffb300;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
            color: #333;
        }
        header {
            background-color: var(--primary);
            color: white;
            padding: 20px;
            text-align: center;
        }
        nav {
            display: flex;
            justify-content: center;
            background-color: var(--dark);
            padding: 10px;
            flex-wrap: wrap;
        }
        nav button {
            background: none;
            border: none;
            color: white;
            padding: 10px 20px;
            margin: 5px;
            cursor: pointer;
            font-size: 16px;
            border-radius: 5px;
            transition: background 0.3s;
        }
        nav button:hover, nav button.active {
            background-color: var(--secondary);
            border-bottom: 3px solid var(--accent);
        }
        .container {
            max-width: 1000px;
            margin: 20px auto;
            padding: 20px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        .section { display: none; }
        .section.active { display: block; }
        
        /* --- MAP SECTION (BARU) --- */
        .map-container {
            position: relative;
            width: 100%;
            max-width: 900px;
            margin: 0 auto;
            border: 2px solid var(--light);
            border-radius: 8px;
            background-color: #cce7ff; /* Warna laut */
            overflow: hidden;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        .base-map {
            width: 100%;
            display: block;
        }
        .map-marker {
            position: absolute;
            transform: translate(-50%, -50%);
            cursor: pointer;
            z-index: 10;
        }
        .map-marker img {
            width: 55px;
            height: 55px;
            border-radius: 50%;
            border: 3px solid var(--primary);
            box-shadow: 0 4px 8px rgba(0,0,0,0.4);
            object-fit: cover;
            transition: transform 0.3s, border-color 0.3s;
        }
        .map-marker:hover img {
            transform: scale(1.3);
            border-color: var(--accent);
            z-index: 20;
        }
        .marker-label {
            display: none;
            position: absolute;
            bottom: -30px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.8);
            color: white;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 12px;
            white-space: nowrap;
            font-weight: bold;
            z-index: 21;
        }
        .map-marker:hover .marker-label {
            display: block;
        }

        /* --- MEDIA SECTION --- */
        .media-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }
        .media-item { width: 100%; border-radius: 8px; }
        .dynamic-info {
            background: var(--light);
            padding: 20px;
            border-radius: 8px;
            border-left: 5px solid var(--accent);
        }
        
        /* --- QUIZ & GAME SECTION --- */
        .quiz-container { margin-top: 20px; }
        .question { font-weight: bold; margin-bottom: 10px; }
        .options { margin-bottom: 20px; }
        .option {
            display: block;
            background: var(--light);
            padding: 10px;
            margin: 5px 0;
            border-radius: 5px;
            cursor: pointer;
            border: 1px solid var(--secondary);
        }
        .option:hover { background: var(--secondary); color: white; }
        #quiz-result { font-size: 20px; font-weight: bold; color: var(--primary); text-align: center; }

        .game-board {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
            max-width: 600px;
            margin: 0 auto;
        }
        .card {
            background-color: var(--secondary);
            height: 100px;
            display: flex;
            justify-content: center;
            align-items: center;
            color: transparent;
            font-size: 14px;
            font-weight: bold;
            cursor: pointer;
            border-radius: 8px;
            text-align: center;
            padding: 5px;
            transition: 0.3s;
            user-select: none;
        }
        .card.flipped {
            background-color: var(--light);
            color: var(--dark);
            border: 2px solid var(--primary);
        }
        .card.matched {
            background-color: #a5d6a7;
            color: var(--dark);
            cursor: default;
        }

        /* --- FOOTER --- */
        footer {
            background-color: var(--dark);
            color: white;
            text-align: center;
            padding: 20px;
            margin-top: 40px;
        }
        .sosmed-links a {
            color: #80cbc4;
            text-decoration: none;
            margin: 0 10px;
            font-weight: bold;
        }
        .sosmed-links a:hover { color: white; }

        @media(max-width: 768px) {
            .media-grid { grid-template-columns: 1fr; }
            .map-marker img { width: 40px; height: 40px; }
        }
    </style>
</head>
<body>

<header>
    <h1>EsHist</h1>
    <p>Evaluasi Sejarah Pergerakan Nasional Indonesia</p>
</header>

<!-- NAVIGASI SUDAH DIPERBAIKI MENGGUNAKAN 'this' -->
<nav id="navbar">
    <button class="active" onclick="showSection('peta', this)">Peta Interaktif</button>
    <button onclick="showSection('media', this)">Materi & Media</button>
    <button onclick="showSection('quiz', this)">Kuis Evaluasi</button>
    <button onclick="showSection('game', this)">Game Mencocokkan</button>
</nav>

<div class="container">
    
    <!-- PETA INTERAKTIF SECTION -->
    <div id="peta" class="section active">
        <h2>Peta Sejarah Pergerakan Nasional</h2>
        <p><strong>Instruksi:</strong> Arahkan kursor atau klik pada foto tokoh/peristiwa di peta untuk melihat detail materi pergerakan di kota tersebut.</p>
        
        <div class="map-container">
            <!-- Gambar Peta Indonesia Polos -->
            <img src="https://upload.wikimedia.org/wikipedia/commons/2/21/Indonesia_blank_map.svg" alt="Peta Indonesia" class="base-map">
            
            <!-- Marker Jakarta (Sumpah Pemuda) -->
            <div class="map-marker" style="top: 73%; left: 32%;" onclick="goToMateri('jakarta')">
                <img src="https://upload.wikimedia.org/wikipedia/commons/e/ea/Sumpah_Pemuda_1928.jpg" alt="Sumpah Pemuda">
                <span class="marker-label">Jakarta (Sumpah Pemuda)</span>
            </div>
            
            <!-- Marker Bandung (PNI/Soekarno) -->
            <div class="map-marker" style="top: 77%; left: 34%;" onclick="goToMateri('bandung')">
                <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/14/Presiden_Sukarno.jpg/400px-Presiden_Sukarno.jpg" alt="Soekarno PNI">
                <span class="marker-label">Bandung (PNI)</span>
            </div>

            <!-- Marker Yogyakarta (Ki Hajar Dewantara / Budi Utomo) -->
            <div class="map-marker" style="top: 80%; left: 39%;" onclick="goToMateri('yogya')">
                <img src="https://upload.wikimedia.org/wikipedia/commons/3/30/Ki_Hadjar_Dewantara_potrait.jpg" alt="Ki Hajar Dewantara">
                <span class="marker-label">Yogyakarta (Taman Siswa)</span>
            </div>

            <!-- Marker Surabaya (Tjokroaminoto / Sarekat Islam) -->
            <div class="map-marker" style="top: 78%; left: 45%;" onclick="goToMateri('surabaya')">
                <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Oemar_Said_Tjokroaminoto.jpg" alt="Tjokroaminoto">
                <span class="marker-label">Surabaya (Sarekat Islam)</span>
            </div>
        </div>
    </div>

    <!-- MATERI & MEDIA SECTION -->
    <div id="media" class="section">
        <h2>Materi & Galeri Pergerakan Nasional</h2>
        
        <!-- Kotak ini akan berubah isinya sesuai gambar di peta yang diklik -->
        <div id="materi-dynamic-info" class="dynamic-info" style="margin-bottom: 20px;">
            <h3>Ringkasan Umum</h3>
            <p>Masa Pergerakan Nasional (1908-1945) ditandai dengan lahirnya organisasi-organisasi modern seperti Budi Utomo, Sarekat Islam, Indische Partij, dan PNI. Puncaknya adalah ikrar Sumpah Pemuda pada 28 Oktober 1928 yang menyatukan tekad pemuda Indonesia.</p>
        </div>

        <div class="media-grid">
            <iframe class="media-item" height="300" src="https://www.youtube.com/embed/5F2v_d9lU5g?si=UvA80dZtZ-N4Mty0" title="YouTube video" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            
            <img class="media-item" style="height: 300px; object-fit: cover;" src="https://upload.wikimedia.org/wikipedia/commons/e/ea/Sumpah_Pemuda_1928.jpg" alt="Sumpah Pemuda">
            <img class="media-item" style="height: 300px; object-fit: cover;" src="https://upload.wikimedia.org/wikipedia/commons/f/f6/Budi_Utomo.jpg" alt="Budi Utomo">
        </div>
    </div>

    <!-- KUIS EVALUASI SECTION -->
    <div id="quiz" class="section">
        <h2>Kuis Evaluasi (20 Soal)</h2>
        <div id="quiz-container"></div>
        <button onclick="submitQuiz()" style="padding: 10px 20px; background: var(--primary); color: white; border: none; border-radius: 5px; cursor: pointer; margin-top: 20px;">Selesai & Cek Nilai</button>
        <p id="quiz-result"></p>
    </div>

    <!-- GAME MENGCOCOKKAN SECTION -->
    <div id="game" class="section">
        <h2>Game Mencocokkan Tokoh & Organisasi</h2>
        <p>Klik kartu untuk menemukan pasangan yang tepat! (Misal: "Budi Utomo" berpasangan dengan "1908")</p>
        <div class="game-board" id="game-board"></div>
        <button onclick="initGame()" style="padding: 10px 20px; background: var(--primary); color: white; border: none; border-radius: 5px; cursor: pointer; margin-top: 20px; display: block; margin-left: auto; margin-right: auto;">Mulai Ulang Game</button>
    </div>
</div>

<footer>
    <h3>Universitas Negeri Malang (UM)</h3>
    <div class="sosmed-links">
        <a href="https://um.ac.id" target="_blank">Website</a> |
        <a href="https://www.instagram.com/universitasnegerimalang/" target="_blank">Instagram</a> |
        <a href="https://twitter.com/UM_1954" target="_blank">Twitter / X</a> |
        <a href="https://www.youtube.com/@UniversitasNegeriMalangOfficial" target="_blank">YouTube</a> |
        <a href="https://www.facebook.com/UniversitasNegeriMalang" target="_blank">Facebook</a>
    </div>
    <p style="margin-top: 15px; font-size: 12px;">&copy; 2026 EsHist - Dibuat untuk Tujuan Edukasi</p>
</footer>

<script>
    // --- FUNGSI NAVIGASI YANG DIPERBAIKI ---
    function showSection(id, btnElement) {
        // Sembunyikan semua konten
        document.querySelectorAll('.section').forEach(sec => sec.classList.remove('active'));
        
        // Hilangkan style aktif di semua tombol navigasi
        document.querySelectorAll('nav button').forEach(btn => btn.classList.remove('active'));
        
        // Tampilkan konten yang dipilih
        document.getElementById(id).classList.add('active');
        
        // Berikan style aktif pada tombol yang diklik
        if(btnElement) {
            btnElement.classList.add('active');
        }
    }

    // --- FUNGSI KLIK PETA MENUJU MATERI ---
    function goToMateri(locationId) {
        // 1. Pindah ke Tab Materi (Tombol ke-2 di navbar)
        const btnMateri = document.querySelectorAll('nav button')[1];
        showSection('media', btnMateri);

        // 2. Mengubah teks info materi sesuai dengan gambar kota yang diklik
        const dynamicInfo = document.getElementById('materi-dynamic-info');
        
        if (locationId === 'jakarta') {
            dynamicInfo.innerHTML = "<h3>Jakarta (Batavia) - Sumpah Pemuda</h3><p>Jakarta menjadi pusat pergerakan pemuda yang melahirkan <strong>Sumpah Pemuda</strong> pada Kongres Pemuda II, 28 Oktober 1928. Peristiwa ini menyatukan seluruh organisasi kepemudaan kedaerahan menjadi satu identitas: Indonesia. Di sini pulalah WR Supratman pertama kali menggemakan lagu Indonesia Raya.</p>";
        } else if (locationId === 'bandung') {
            dynamicInfo.innerHTML = "<h3>Bandung - Partai Nasional Indonesia (PNI)</h3><p>Di Bandung, Ir. Soekarno mendirikan <strong>Partai Nasional Indonesia (PNI)</strong> pada 4 Juli 1927. Bandung juga menjadi saksi bisu saat Soekarno membacakan pledoi fenomenalnya berjudul <i>'Indonesia Menggugat'</i> saat ia diadili oleh pemerintah kolonial Belanda.</p>";
        } else if (locationId === 'yogya') {
            dynamicInfo.innerHTML = "<h3>Yogyakarta - Taman Siswa & Muhammadiyah</h3><p>Yogyakarta merupakan kota penting dalam pergerakan bidang pendidikan dan sosial-keagamaan. Di sinilah K.H. Ahmad Dahlan mendirikan <strong>Muhammadiyah</strong> (1912), dan Ki Hajar Dewantara mendirikan perguruan <strong>Taman Siswa</strong> (1922) untuk melawan diskriminasi pendidikan Belanda.</p>";
        } else if (locationId === 'surabaya') {
            dynamicInfo.innerHTML = "<h3>Surabaya - Sarekat Islam</h3><p>Surabaya adalah dapur pergerakan nasional. Di bawah pimpinan H.O.S Tjokroaminoto, <strong>Sarekat Islam (SI)</strong> bermarkas di sini dan berkembang menjadi organisasi massa terbesar pertama di Indonesia. Rumah Tjokroaminoto di Peneleh menjadi tempat kos sekaligus 'sekolah politik' bagi tokoh-tokoh besar seperti Soekarno, Semaoen, dan Kartosoewirjo.</p>";
        }
    }

    // --- KUIS EVALUASI (20 Soal Tetap Sama) ---
    const questions = [
        { q: "Organisasi pergerakan nasional pertama di Indonesia yang berdiri pada 20 Mei 1908 adalah?", a: ["Sarekat Islam", "Budi Utomo", "Indische Partij", "PNI"], ans: 1 },
        { q: "Siapakah tokoh pendiri Sarekat Dagang Islam?", a: ["H.O.S Tjokroaminoto", "Ki Hajar Dewantara", "K.H. Samanhudi", "Soekarno"], ans: 2 },
        { q: "Tiga Serangkai pendiri Indische Partij adalah Douwes Dekker, Cipto Mangunkusumo, dan...", a: ["Soepomo", "Ki Hajar Dewantara", "Moh. Hatta", "Sutan Syahrir"], ans: 1 },
        { q: "Sumpah Pemuda diikrarkan pada tanggal?", a: ["20 Mei 1908", "17 Agustus 1945", "28 Oktober 1928", "2 Mei 1889"], ans: 2 },
        { q: "Siapa ketua Kongres Pemuda II yang menghasilkan Sumpah Pemuda?", a: ["Sugondo Djojopuspito", "Moh. Yamin", "W.R. Supratman", "Amir Sjarifuddin"], ans: 0 },
        { q: "Partai Nasional Indonesia (PNI) didirikan di Bandung pada tahun 1927 oleh?", a: ["Moh. Hatta", "Soekarno", "Agus Salim", "Sutan Syahrir"], ans: 1 },
        { q: "Perhimpunan Indonesia (PI) di Belanda awalnya bernama?", a: ["Indische Partij", "Indische Vereeniging", "Jong Java", "Volksraad"], ans: 1 },
        { q: "Lagu Indonesia Raya pertama kali diperdengarkan secara instrumental menggunakan biola oleh?", a: ["Ibu Sud", "W.R. Supratman", "Ismail Marzuki", "C. Simanjuntak"], ans: 1 },
        { q: "Organisasi keagamaan Muhammadiyah didirikan di Yogyakarta pada tahun 1912 oleh?", a: ["K.H. Hasyim Asy'ari", "K.H. Ahmad Dahlan", "Agus Salim", "Wahid Hasyim"], ans: 1 },
        { q: "Organisasi Nahdlatul Ulama (NU) didirikan pada tahun?", a: ["1912", "1926", "1905", "1928"], ans: 1 },
        { q: "GAPI (Gabungan Politik Indonesia) memiliki tuntutan utama yaitu?", a: ["Indonesia Merdeka", "Indonesia Berparlemen", "Indonesia Raya", "Indonesia Bersatu"], ans: 1 },
        { q: "Tokoh yang dijuluki Bapak Pendidikan Nasional dan mendirikan Taman Siswa adalah?", a: ["Soekarno", "Moh. Hatta", "Ki Hajar Dewantara", "Douwes Dekker"], ans: 2 },
        { q: "Artikel terkenal Ki Hajar Dewantara yang mengkritik pemerintah kolonial berjudul?", a: ["Als ik een Nederlander was", "Indonesia Menggugat", "Max Havelaar", "Habis Gelap Terbitlah Terang"], ans: 0 },
        { q: "Organisasi pemuda Trikoro Dharmo kemudian berubah nama menjadi?", a: ["Jong Sumatranen Bond", "Jong Java", "Jong Ambon", "Pemuda Indonesia"], ans: 1 },
        { q: "Pemberontakan pertama PKI melawan kolonial Belanda terjadi pada tahun?", a: ["1948", "1965", "1926", "1914"], ans: 2 },
        { q: "Tulisan pembelaan (pledoi) Soekarno saat diadili di Bandung dikenal dengan nama?", a: ["Indonesia Menggugat", "Zaman Peralihan", "Masyarakat Baru", "Sarinah"], ans: 0 },
        { q: "Sarekat Islam pecah menjadi SI Putih dan SI Merah. SI Merah disusupi oleh paham?", a: ["Nasionalis", "Agamis", "Komunis/Marxis", "Fasis"], ans: 2 },
        { q: "Tokoh pejuang emansipasi wanita dari Jawa Barat yang mendirikan Sekolah Keutamaan Istri adalah?", a: ["R.A. Kartini", "Dewi Sartika", "Cut Nyak Dien", "Martha Christina Tiahahu"], ans: 1 },
        { q: "Dewan Rakyat yang dibentuk Belanda pada tahun 1918 disebut?", a: ["Volksraad", "Raad van Indie", "Gouverneur Generaal", "Binnenlands Bestuur"], ans: 0 },
        { q: "Majalah yang diterbitkan oleh Perhimpunan Indonesia di Belanda adalah?", a: ["Oetoesan Hindia", "Hindia Poetra (Indonesia Merdeka)", "De Expres", "Bintang Hindia"], ans: 1 }
    ];

    const quizContainer = document.getElementById("quiz-container");
    questions.forEach((q, index) => {
        let html = `<div class="question">${index + 1}. ${q.q}</div><div class="options">`;
        q.a.forEach((opt, i) => {
            html += `<label class="option"><input type="radio" name="q${index}" value="${i}"> ${opt}</label>`;
        });
        html += `</div>`;
        quizContainer.innerHTML += html;
    });

    function submitQuiz() {
        let score = 0;
        questions.forEach((q, index) => {
            const selected = document.querySelector(`input[name="q${index}"]:checked`);
            if (selected && parseInt(selected.value) === q.ans) score++;
        });
        const finalScore = (score / questions.length) * 100;
        document.getElementById("quiz-result").innerText = `Nilai Anda: ${finalScore} / 100 (${score} Benar dari 20 Soal)`;
    }

    // --- GAME MENGCOCOKKAN (Tetap Sama) ---
    const gameBoard = document.getElementById("game-board");
    const cardPairs = [
        { id: 1, text: "Budi Utomo" }, { id: 1, text: "20 Mei 1908" },
        { id: 2, text: "Ki Hajar Dewantara" }, { id: 2, text: "Taman Siswa" },
        { id: 3, text: "Sumpah Pemuda" }, { id: 3, text: "28 Oktober 1928" },
        { id: 4, text: "Soekarno" }, { id: 4, text: "PNI" },
        { id: 5, text: "W.R. Supratman" }, { id: 5, text: "Indonesia Raya" },
        { id: 6, text: "Douwes Dekker" }, { id: 6, text: "Indische Partij" },
        { id: 7, text: "K.H. Ahmad Dahlan" }, { id: 7, text: "Muhammadiyah" },
        { id: 8, text: "Dewi Sartika" }, { id: 8, text: "Keutamaan Istri" }
    ];

    let firstCard = null;
    let secondCard = null;
    let lockBoard = false;

    function initGame() {
        gameBoard.innerHTML = "";
        firstCard = null;
        secondCard = null;
        lockBoard = false;
        
        const shuffled = cardPairs.sort(() => 0.5 - Math.random());
        shuffled.forEach(item => {
            const card = document.createElement("div");
            card.classList.add("card");
            card.dataset.id = item.id;
            card.innerText = item.text;
            card.addEventListener("click", flipCard);
            gameBoard.appendChild(card);
        });
    }

    function flipCard() {
        if (lockBoard) return;
        if (this === firstCard) return;

        this.classList.add("flipped");

        if (!firstCard) {
            firstCard = this;
            return;
        }

        secondCard = this;
        lockBoard = true;
        checkForMatch();
    }

    function checkForMatch() {
        let isMatch = firstCard.dataset.id === secondCard.dataset.id;
        isMatch ? disableCards() : unflipCards();
    }

    function disableCards() {
        firstCard.classList.add("matched");
        secondCard.classList.add("matched");
        resetBoard();
    }

    function unflipCards() {
        setTimeout(() => {
            firstCard.classList.remove("flipped");
            secondCard.classList.remove("flipped");
            resetBoard();
        }, 1000);
    }

    function resetBoard() {
        [firstCard, secondCard, lockBoard] = [null, null, false];
    }

    window.onload = initGame;
</script>

</body>
</html>
