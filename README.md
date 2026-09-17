<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EsHist - Sejarah Pergerakan Nasional</title>
    <style>
        :root {
            --primary: #2C3E50;
            --secondary: #E67E22;
            --light: #ECF0F1;
            --dark: #27AE60;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f9f9f9;
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
            background-color: #34495E;
        }
        nav button {
            background: none;
            border: none;
            color: white;
            padding: 15px 20px;
            cursor: pointer;
            font-size: 16px;
            transition: 0.3s;
        }
        nav button:hover, nav button.active {
            background-color: var(--secondary);
        }
        .container {
            max-width: 1000px;
            margin: 20px auto;
            padding: 20px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        .section { display: none; }
        .section.active { display: block; }
        
        /* Media Section */
        .media-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        .media-grid img { width: 100%; border-radius: 8px; }
        .video-container { margin-top: 30px; text-align: center; }

        /* Game Section */
        .game-board {
            display: grid;
            grid-template-columns: repeat(4, 100px);
            gap: 10px;
            justify-content: center;
            margin-top: 20px;
        }
        .card {
            width: 100px;
            height: 100px;
            background-color: var(--primary);
            color: transparent;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            font-weight: bold;
            text-align: center;
            cursor: pointer;
            border-radius: 8px;
            user-select: none;
            transition: transform 0.3s;
        }
        .card.flipped {
            background-color: var(--light);
            color: var(--primary);
            border: 2px solid var(--primary);
            cursor: default;
        }
        .card.matched {
            background-color: var(--dark);
            color: white;
            border: none;
        }

        /* Quiz Section */
        .quiz-container { margin-top: 20px; }
        .question { margin-bottom: 20px; padding: 15px; background: var(--light); border-radius: 5px; }
        .question p { font-weight: bold; margin-top: 0; }
        .options label { display: block; margin-bottom: 8px; cursor: pointer; }
        button.submit-btn {
            background-color: var(--dark);
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
        }
        button.submit-btn:hover { background-color: #219653; }
        #quiz-result { margin-top: 20px; font-size: 18px; font-weight: bold; }

        /* Footer */
        footer {
            background-color: var(--primary);
            color: white;
            text-align: center;
            padding: 20px;
            margin-top: 40px;
        }
        .sosmed a {
            color: var(--secondary);
            text-decoration: none;
            margin: 0 10px;
            font-weight: bold;
        }
        .sosmed a:hover { color: white; }
    </style>
</head>
<body>

    <header>
        <h1>EsHist (Edu Sejarah History)</h1>
        <p>Platform Interaktif Belajar Sejarah Pergerakan Nasional</p>
    </header>

    <nav>
        <button class="active" onclick="showSection('materi')">Materi & Media</button>
        <button onclick="showSection('game')">Game Mencocokkan</button>
        <button onclick="showSection('evaluasi')">20 Soal Evaluasi</button>
    </nav>

    <div class="container">
        <!-- MATERI SECTION -->
        <div id="materi" class="section active">
            <h2>Materi Pergerakan Nasional</h2>
            <p>Masa pergerakan nasional Indonesia (1908-1942) merupakan tonggak penting kebangkitan kesadaran berbangsa. Ditandai dengan berdirinya Budi Utomo, disusul oleh Sarekat Islam, Indische Partij, hingga puncaknya pada Sumpah Pemuda 1928.</p>
            
            <div class="media-grid">
                <div>
                    <img src="https://upload.wikimedia.org/wikipedia/commons/4/4e/Sumpah_Pemuda_1928.jpg" alt="Sumpah Pemuda" onerror="this.src='https://placehold.co/400x250?text=Foto+Sumpah+Pemuda'">
                    <p style="text-align:center; font-size:14px;">Kongres Pemuda II (1928)</p>
                </div>
                <div>
                    <img src="https://upload.wikimedia.org/wikipedia/commons/e/ea/Budi_Utomo.jpg" alt="Budi Utomo" onerror="this.src='https://placehold.co/400x250?text=Tokoh+Budi+Utomo'">
                    <p style="text-align:center; font-size:14px;">Tokoh-Tokoh Budi Utomo</p>
                </div>
            </div>

            <div class="video-container">
                <h3>Video Pembelajaran</h3>
                <iframe width="100%" height="400" src="https://www.youtube.com/embed/6i61-X8Y7Fk" title="Sejarah Pergerakan Nasional" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            </div>
        </div>

        <!-- GAME SECTION -->
        <div id="game" class="section">
            <h2>Game Mencocokkan Gambar/Kata</h2>
            <p>Temukan pasangan kartu yang sama yang berkaitan dengan sejarah Pergerakan Nasional!</p>
            <div class="game-board" id="game-board"></div>
            <button onclick="resetGame()" class="submit-btn" style="margin-top:20px; display:block; margin-left:auto; margin-right:auto;">Ulangi Game</button>
        </div>

        <!-- EVALUASI SECTION -->
        <div id="evaluasi" class="section">
            <h2>Evaluasi Pergerakan Nasional</h2>
            <p>Kerjakan 20 soal di bawah ini untuk menguji pemahamanmu.</p>
            <div id="quiz-form" class="quiz-container"></div>
            <button class="submit-btn" onclick="calculateScore()">Cek Nilai</button>
            <div id="quiz-result"></div>
        </div>
    </div>

    <footer>
        <p>&copy; 2026 EsHist - Dibuat untuk Pembelajaran Sejarah</p>
        <p>Kunjungi Sosial Media Resmi <strong>Universitas Negeri Malang (UM)</strong>:</p>
        <div class="sosmed">
            <a href="https://um.ac.id/" target="_blank">Website</a> |
            <a href="https://www.instagram.com/universitasnegerimalang/" target="_blank">Instagram</a> |
            <a href="https://twitter.com/UM_1954" target="_blank">X (Twitter)</a> |
            <a href="https://www.facebook.com/UniversitasNegeriMalangOfficial" target="_blank">Facebook</a> |
            <a href="https://www.youtube.com/c/UniversitasNegeriMalangOfficial" target="_blank">YouTube</a>
        </div>
    </footer>

    <script>
        // --- NAVIGATION LOGIC ---
        function showSection(sectionId) {
            document.querySelectorAll('.section').forEach(sec => sec.classList.remove('active'));
            document.querySelectorAll('nav button').forEach(btn => btn.classList.remove('active'));
            document.getElementById(sectionId).classList.add('active');
            event.target.classList.add('active');
        }

        // --- MATCHING GAME LOGIC ---
        const gameItems = [
            'Budi Utomo', '1908',
            'Sumpah Pemuda', '1928',
            'Sarekat Islam', 'Tjokroaminoto',
            'Indische Partij', 'Tiga Serangkai',
            'Taman Siswa', 'Ki Hajar Dewantara',
            'Indonesia Raya', 'W.R. Supratman'
        ];
        // Create pairs
        let cards = [...gameItems, ...gameItems];
        let hasFlippedCard = false;
        let lockBoard = false;
        let firstCard, secondCard;

        function shuffle(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
        }

        function initGame() {
            const board = document.getElementById('game-board');
            board.innerHTML = '';
            shuffle(cards);
            cards.forEach(item => {
                const cardElement = document.createElement('div');
                cardElement.classList.add('card');
                cardElement.dataset.name = item;
                cardElement.innerText = item; // Visible when flipped
                cardElement.addEventListener('click', flipCard);
                board.appendChild(cardElement);
            });
        }

        function flipCard() {
            if (lockBoard) return;
            if (this === firstCard) return;

            this.classList.add('flipped');

            if (!hasFlippedCard) {
                hasFlippedCard = true;
                firstCard = this;
                return;
            }

            secondCard = this;
            checkForMatch();
        }

        function checkForMatch() {
            let isMatch = firstCard.dataset.name === secondCard.dataset.name;
            isMatch ? disableCards() : unflipCards();
        }

        function disableCards() {
Berikut adalah kode lengkap untuk website interaktif bernama **EsHist** (Evaluasi Sejarah). Website ini dirancang dalam satu file (Single Page Application) yang berisi materi video/foto, 20 soal kuis interaktif, game mencocokkan kartu (Memory Game), dan tautan sosial media Universitas Negeri Malang (UM).

Anda dapat menyalin kode di bawah ini, menempelkannya di aplikasi teks editor (seperti Notepad, VS Code, atau Sublime Text), lalu menyimpannya dengan nama `index.html`. Buka file tersebut menggunakan browser (Chrome, Firefox, dll).

```html
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
        }
        nav button {
            background: none;
            border: none;
            color: white;
            padding: 10px 20px;
            margin: 0 5px;
            cursor: pointer;
            font-size: 16px;
            border-radius: 5px;
            transition: background 0.3s;
        }
        nav button:hover, nav button.active {
            background-color: var(--secondary);
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
        
        /* Media Section */
        .media-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }
        .media-item { width: 100%; border-radius: 8px; }
        
        /* Quiz Section */
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

        /* Game Section */
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

        /* Footer & Sosmed */
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
    </style>
</head>
<body>

<header>
    <h1>EsHist</h1>
    <p>Evaluasi Sejarah Pergerakan Nasional Indonesia</p>
</header>

<nav>
    <button class="active" onclick="showSection('media')">Materi & Media</button>
    <button onclick="showSection('quiz')">Kuis Evaluasi</button>
    <button onclick="showSection('game')">Game Mencocokkan</button>
</nav>

<div class="container">
    <!-- MEDIA SECTION -->
    <div id="media" class="section active">
        <h2>Galeri Pergerakan Nasional</h2>
        <p>Pelajari video dan foto bersejarah berikut sebelum mengerjakan kuis dan game.</p>
        <div class="media-grid">
            <!-- Ganti src video dengan link YouTube Embed yang sesuai -->
            <iframe class="media-item" height="300" src="[https://www.youtube.com/embed/5F2v_d9lU5g?si=UvA80dZtZ-N4Mty0](https://www.youtube.com/embed/5F2v_d9lU5g?si=UvA80dZtZ-N4Mty0)" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            
            <!-- Ganti src img dengan link gambar yang relevan -->
            <img class="media-item" style="height: 300px; object-fit: cover;" src="[https://upload.wikimedia.org/wikipedia/commons/e/ea/Sumpah_Pemuda_1928.jpg](https://upload.wikimedia.org/wikipedia/commons/e/ea/Sumpah_Pemuda_1928.jpg)" alt="Sumpah Pemuda">
            
            <img class="media-item" style="height: 300px; object-fit: cover;" src="[https://upload.wikimedia.org/wikipedia/commons/f/f6/Budi_Utomo.jpg](https://upload.wikimedia.org/wikipedia/commons/f/f6/Budi_Utomo.jpg)" alt="Budi Utomo">
            
            <div style="background:var(--light); padding: 20px; border-radius:8px;">
                <h3>Ringkasan</h3>
                <p>Masa Pergerakan Nasional (1908-1945) ditandai dengan lahirnya organisasi-organisasi modern seperti Budi Utomo, Sarekat Islam, Indische Partij, dan PNI. Puncaknya adalah ikrar Sumpah Pemuda pada 28 Oktober 1928 yang menyatukan tekad pemuda Indonesia.</p>
            </div>
        </div>
    </div>

    <!-- QUIZ SECTION -->
    <div id="quiz" class="section">
        <h2>Kuis Evaluasi (20 Soal)</h2>
        <div id="quiz-container"></div>
        <button onclick="submitQuiz()" style="padding: 10px 20px; background: var(--primary); color: white; border: none; border-radius: 5px; cursor: pointer; margin-top: 20px;">Selesai & Cek Nilai</button>
        <p id="quiz-result"></p>
    </div>

    <!-- GAME SECTION -->
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
        <a href="[https://um.ac.id](https://um.ac.id)" target="_blank">Website</a> |
        <a href="[https://www.instagram.com/universitasnegerimalang/](https://www.instagram.com/universitasnegerimalang/)" target="_blank">Instagram</a> |
        <a href="[https://twitter.com/UM_1954](https://twitter.com/UM_1954)" target="_blank">Twitter / X</a> |
        <a href="[https://www.youtube.com/@UniversitasNegeriMalangOfficial](https://www.youtube.com/@UniversitasNegeriMalangOfficial)" target="_blank">YouTube</a> |
        <a href="[https://www.facebook.com/UniversitasNegeriMalang](https://www.facebook.com/UniversitasNegeriMalang)" target="_blank">Facebook</a>
    </div>
    <p style="margin-top: 15px; font-size: 12px;">&copy; 2026 EsHist - Dibuat untuk Tujuan Edukasi</p>
</footer>

<script>
    // --- NAVIGATION LOGIC ---
    function showSection(id) {
        document.querySelectorAll('.section').forEach(sec => sec.classList.remove('active'));
        document.querySelectorAll('nav button').forEach(btn => btn.classList.remove('active'));
        document.getElementById(id).classList.add('active');
        event.target.classList.add('active');
    }

    // --- QUIZ LOGIC ---
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

    // --- GAME LOGIC ---
    const gameBoard = document.getElementById("game-board");
    // Pasangan kartu (Tokoh/Organisasi dan Kata Kunci)
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
        
        // Acak kartu
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

    // Mulai game saat halaman dimuat
    window.onload = initGame;
</script>

</body>
</html>
