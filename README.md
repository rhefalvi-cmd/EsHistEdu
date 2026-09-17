<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EsHist - Pembelajaran Interaktif Pergerakan Nasional (Kelas 11)</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Poppins', sans-serif; }
    </style>
</head>
<body class="bg-amber-50 text-slate-800 min-h-screen flex flex-col">

    <!-- Header / Navbar -->
    <header class="bg-amber-900 text-amber-100 shadow-md sticky top-0 z-50">
        <div class="max-w-6xl mx-auto px-4 py-4 flex flex-col md:flex-row justify-between items-center">
            <div class="flex items-center space-x-3 mb-3 md:mb-0">
                <span class="text-3xl">📜</span>
                <div>
                    <h1 class="text-xl font-bold tracking-wide">ESHIST</h1>
                    <p class="text-xs text-amber-300">E-Learning Sejarah Kelas XI - Pergerakan Nasional</p>
                </div>
            </div>
            <!-- Navigasi Menu (Tombol Headbar) -->
            <nav class="flex flex-wrap justify-center gap-1 bg-amber-950/40 p-1 rounded-xl relative z-50">
                <button type="button" onclick="switchTab('materi')" id="nav-materi" class="px-3 py-2 rounded-lg font-semibold text-xs md:text-sm transition bg-amber-700 text-white shadow cursor-pointer">Materi & Video</button>
                <button type="button" onclick="switchTab('timeline')" id="nav-timeline" class="px-3 py-2 rounded-lg font-semibold text-xs md:text-sm transition hover:bg-amber-800 cursor-pointer">Timeline</button>
                <button type="button" onclick="switchTab('game')" id="nav-game" class="px-3 py-2 rounded-lg font-semibold text-xs md:text-sm transition hover:bg-amber-800 cursor-pointer">🎮 Mini Game</button>
                <button type="button" onclick="switchTab('kuis')" id="nav-kuis" class="px-3 py-2 rounded-lg font-semibold text-xs md:text-sm transition hover:bg-amber-800 cursor-pointer">Kuis (10 Soal)</button>
                <button type="button" onclick="switchTab('evaluasi')" id="nav-evaluasi" class="px-3 py-2 rounded-lg font-semibold text-xs md:text-sm transition hover:bg-amber-800 cursor-pointer">Evaluasi (10 Soal)</button>
            </nav>
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="flex-grow max-w-6xl mx-auto px-4 py-8 w-full">

        <!-- TAB 1: MATERI -->
        <section id="tab-materi" class="space-y-6 block">
            <div class="bg-white rounded-2xl p-6 md:p-8 shadow-sm border border-amber-200">
                <span class="bg-amber-100 text-amber-800 text-xs font-semibold px-3 py-1 rounded-full uppercase tracking-wider">Bab Pembelajaran</span>
                <h2 class="text-2xl md:text-3xl font-bold text-amber-950 mt-2">Latar Belakang & Tumbuhnya Kesadaran Nasional</h2>
                <p class="mt-4 text-slate-600 leading-relaxed">
                    Pergerakan nasional adalah istilah yang digunakan untuk periode pada paruh pertama abad ke-20 di Indonesia di mana rakyat Indonesia mulai menyadari diri sebagai bangsa yang dijajah oleh Belanda dan berjuang bersama untuk mencapai kemerdekaan.
                </p>
                
                <div class="grid md:grid-cols-2 gap-6 mt-6">
                    <div class="bg-amber-50/60 p-5 rounded-xl border border-amber-100">
                        <h3 class="font-bold text-amber-900 mb-2">🌍 Faktor Internal (Dari Dalam)</h3>
                        <ul class="list-disc list-inside space-y-1 text-sm text-slate-700">
                            <li class="mb-1">Penderitaan rakyat akibat penjajahan yang berkepanjangan.</li>
                            <li class="mb-1">Munculnya kaum terpelajar/intelektual hasil Politik Etis (1901).</li>
                            <li class="mb-1">Kenangan kejayaan masa lampau (Sriwijaya & Majapahit).</li>
                            <li class="mb-1">Kesadaran akan pentingnya persatuan nasional melampaui batas suku.</li>
                        </ul>
                    </div>
                    <div class="bg-amber-50/60 p-5 rounded-xl border border-amber-100">
                        <h3 class="font-bold text-amber-900 mb-2">🌐 Faktor Eksternal (Dari Luar)</h3>
                        <ul class="list-disc list-inside space-y-1 text-sm text-slate-700">
                            <li class="mb-1">Kemenangan Jepang atas Rusia (1905) yang membangkitkan rasa percaya diri bangsa Asia.</li>
                            <li class="mb-1">Kebangkitan nasional negara tetangga (Filipina, India, Cina/Sun Yat-sen).</li>
                            <li class="mb-1">Pengaruh paham-paham baru di dunia (Nasionalisme, Liberalisme, Sosialisme).</li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- Video Pembelajaran -->
            <div class="bg-white rounded-2xl p-6 md:p-8 shadow-sm border border-amber-200">
                <h3 class="text-xl font-bold text-amber-950 mb-2">🎬 Video Pembelajaran Sejarah</h3>
                <p class="text-sm text-slate-600 mb-4">Saksikan video ringkasan materi pergerakan nasional untuk memperdalam pemahaman Anda.</p>
                <div class="relative w-full overflow-hidden rounded-xl shadow-md border border-amber-200" style="padding-top: 56.25%;">
                    <iframe class="absolute top-0 left-0 w-full h-full" src="https://www.youtube.com/embed/dQw4w9WgXcQ" title="Video Pembelajaran Pergerakan Nasional" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>
            </div>

            <!-- Galeri Foto Sejarah -->
            <div class="bg-white rounded-2xl p-6 md:p-8 shadow-sm border border-amber-200">
                <h3 class="text-xl font-bold text-amber-950 mb-4">📸 Galeri Tokoh & Peristiwa Bersejarah</h3>
                <div class="grid sm:grid-cols-2 md:grid-cols-3 gap-6">
                    <div class="bg-amber-50/50 border border-amber-200 rounded-xl overflow-hidden shadow-sm flex flex-col">
                        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1d/Stovia_studenten.jpg/640px-Stovia_studenten.jpg" alt="STOVIA" class="w-full h-48 object-cover">
                        <div class="p-4 flex flex-col flex-grow">
                            <h4 class="font-bold text-amber-900 text-sm">Gedung STOVIA Batavia</h4>
                            <p class="text-xs text-slate-600 mt-1">Tempat lahirnya organisasi Budi Utomo oleh para pelajar kedokteran pribumi tahun 1908.</p>
                        </div>
                    </div>
                    <div class="bg-amber-50/50 border border-amber-200 rounded-xl overflow-hidden shadow-sm flex flex-col">
                        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Tiga_Serangkai.jpg/640px-Tiga_Serangkai.jpg" alt="Tiga Serangkai" class="w-full h-48 object-cover">
                        <div class="p-4 flex flex-col flex-grow">
                            <h4 class="font-bold text-amber-900 text-sm">Tiga Serangkai Indische Partij</h4>
                            <p class="text-xs text-slate-600 mt-1">Douwes Dekker, Tjipto Mangoenkoesoemo, dan Ki Hajar Dewantara.</p>
                        </div>
                    </div>
                    <div class="bg-amber-50/50 border border-amber-200 rounded-xl overflow-hidden shadow-sm flex flex-col">
                        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Kongres_Pemuda_II.jpg/640px-Kongres_Pemuda_II.jpg" alt="Sumpah Pemuda" class="w-full h-48 object-cover">
                        <div class="p-4 flex flex-col flex-grow">
                            <h4 class="font-bold text-amber-900 text-sm">Kongres Pemuda II (1928)</h4>
                            <p class="text-xs text-slate-600 mt-1">Momen pengikraran Sumpah Pemuda penyatu bangsa.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- TAB 2: TIMELINE -->
        <section id="tab-timeline" class="hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 md:p-8 shadow-sm border border-amber-200">
                <h2 class="text-2xl font-bold text-amber-950 mb-2">Garis Waktu Peristiwa Penting</h2>
                <p class="text-slate-600 text-sm mb-6">Klik tombol tahun di bawah ini untuk melihat detail peristiwa.</p>
                <div class="flex flex-wrap gap-2 mb-6" id="timeline-buttons"></div>
                <div id="timeline-detail" class="bg-amber-50 p-6 rounded-xl border border-amber-200 transition-all duration-300">
                    <span id="tl-year" class="bg-amber-800 text-white text-xs font-bold px-3 py-1 rounded-full">Tahun</span>
                    <h3 id="tl-title" class="text-xl font-bold text-amber-950 mt-2">Judul Peristiwa</h3>
                    <p id="tl-desc" class="text-slate-700 mt-2 text-sm md:text-base leading-relaxed">Deskripsi lengkap peristiwa.</p>
                </div>
            </div>
        </section>

        <!-- TAB 3: MINI GAME -->
        <section id="tab-game" class="hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 md:p-8 shadow-sm border border-amber-200 max-w-2xl mx-auto text-center">
                <span class="bg-amber-100 text-amber-800 text-xs font-semibold px-3 py-1 rounded-full uppercase tracking-wider">Tantangan Kilat</span>
                <h2 class="text-2xl font-bold text-amber-950 mt-2">🎮 Mini Game: Tebak Peristiwa Sejarah</h2>
                <p class="text-sm text-slate-600 mt-1">Uji cepat daya ingatmu seputar tokoh dan tonggak sejarah!</p>

                <div id="game-card" class="mt-6 p-6 rounded-2xl bg-amber-50 border border-amber-200 text-left">
                    <div class="flex justify-between items-center mb-4 text-xs font-bold text-amber-800">
                        <span id="game-progress">Tantangan 1 / 4</span>
                        <span id="game-score">Skor: 0</span>
                    </div>
                    <p id="game-question" class="text-lg font-bold text-slate-900 mb-4">Pertanyaan game...</p>
                    <div id="game-options" class="space-y-3"></div>
                </div>

                <div id="game-feedback" class="mt-4 hidden p-3 rounded-xl text-sm font-semibold"></div>

                <div id="game-finish" class="hidden mt-6 p-6 bg-amber-900 text-amber-100 rounded-2xl">
                    <h3 class="text-2xl font-bold mb-2">🎉 Permainan Selesai!</h3>
                    <p id="game-final-score" class="text-lg mb-4">Skor Akhir Anda: 0</p>
                    <button type="button" onclick="restartGame()" class="bg-amber-600 hover:bg-amber-500 text-white font-bold px-6 py-2 rounded-xl transition cursor-pointer">Main Lagi</button>
                </div>
            </div>
        </section>

        <!-- TAB 4: KUIS LATIHAN -->
        <section id="tab-kuis" class="hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 md:p-8 shadow-sm border border-amber-200 max-w-2xl mx-auto">
                <div id="quiz-container">
                    <div class="flex justify-between items-center mb-4 border-b pb-3">
                        <h2 class="text-xl font-bold text-amber-950">Kuis Latihan Pemahaman (10 Soal)</h2>
                        <span id="quiz-progress" class="text-sm font-semibold text-amber-700">Soal 1 dari 10</span>
                    </div>

                    <div id="question-box">
                        <p id="question-text" class="text-lg font-medium text-slate-800 mb-4">Pertanyaan kuis...</p>
                        <div id="options-container" class="space-y-3"></div>
                    </div>

                    <div id="feedback-box" class="mt-6 hidden p-4 rounded-xl text-sm"></div>

                    <div class="mt-6 flex justify-end">
                        <button type="button" id="next-btn" onclick="nextQuestion()" class="hidden bg-amber-800 hover:bg-amber-900 text-white font-semibold px-6 py-2 rounded-xl transition cursor-pointer">Selanjutnya</button>
                    </div>
                </div>

                <div id="quiz-result" class="hidden text-center py-8">
                    <div class="text-5xl mb-3">🏆</div>
                    <h3 class="text-2xl font-bold text-amber-950">Kuis Latihan Selesai!</h3>
                    <p id="score-text" class="text-lg text-slate-700 mt-2">Skor Anda: 0 dari 10</p>
                    <button type="button" onclick="restartQuiz()" class="mt-6 bg-amber-800 hover:bg-amber-900 text-white font-semibold px-6 py-2 rounded-xl transition cursor-pointer">Ulangi Kuis Latihan</button>
                </div>
            </div>
        </section>

        <!-- TAB 5: EVALUASI AKHIR -->
        <section id="tab-evaluasi" class="hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 md:p-8 shadow-sm border border-amber-200 max-w-3xl mx-auto">
                <div class="border-b pb-4 mb-6">
                    <h2 class="text-2xl font-bold text-amber-950">Evaluasi Akhir Pembelajaran (10 Soal)</h2>
                    <p class="text-sm text-slate-600 mt-1">Jawablah seluruh 10 soal pilihan ganda di bawah ini dengan teliti.</p>
                </div>

                <div id="eval-questions-container" class="space-y-8"></div>

                <div id="eval-submit-container" class="mt-8 pt-4 border-t text-center">
                    <button type="button" onclick="submitEvaluation()" class="bg-amber-900 hover:bg-amber-950 text-white font-bold px-8 py-3 rounded-xl shadow-md transition cursor-pointer">Kumpul dan Lihat Hasil Evaluasi</button>
                </div>

                <div id="eval-result-box" class="hidden mt-6 p-6 rounded-2xl bg-amber-50 border border-amber-300 text-center">
                    <h3 class="text-2xl font-bold text-amber-950 mb-2">📊 Hasil Evaluasi Anda</h3>
                    <p id="eval-score-text" class="text-xl font-semibold text-amber-800 my-2">Skor: 0 / 100</p>
                    <p id="eval-desc-text" class="text-sm text-slate-700 mb-6"></p>
                    <button type="button" onclick="resetEvaluation()" class="bg-amber-800 hover:bg-amber-900 text-white font-semibold px-6 py-2 rounded-xl transition cursor-pointer">Ulangi Evaluasi</button>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="bg-amber-950 text-amber-200 py-6 mt-12 border-t border-amber-900 text-xs">
        <div class="max-w-6xl mx-auto px-4 flex flex-col md:flex-row justify-between items-center gap-4 text-center md:text-left">
            <div>
                <p class="font-bold text-amber-100 text-sm">EsHist &copy; 2026</p>
                <p class="text-amber-400 mt-1">Platform Pembelajaran Interaktif Sejarah Indonesia</p>
            </div>
            <div class="flex flex-col items-center md:items-end">
                <span class="text-amber-300 font-semibold mb-2">Universitas Negeri Malang (UM):</span>
                <div class="flex flex-wrap justify-center gap-3">
                    <a href="https://um.ac.id" target="_blank" class="hover:text-white underline">Website UM</a>
                    <span>•</span>
                    <a href="https://linktr.ee/UM1954" target="_blank" class="hover:text-white underline">Linktree Resmi UM</a>
                    <span>•</span>
                    <a href="https://instagram.com/universitasnegerimalang" target="_blank" class="hover:text-white underline">Instagram UM</a>
                    <span>•</span>
                    <a href="https://www.youtube.com/c/UniversitasNegeriMalangOfficial" target="_blank" class="hover:text-white underline">YouTube UM</a>
                </div>
            </div>
        </div>
    </footer>

    <!-- Logika JavaScript -->
    <script>
        // --- 1. NAVIGASI TAB ---
        function switchTab(tabId) {
            const tabs = ['materi', 'timeline', 'game', 'kuis', 'evaluasi'];
            tabs.forEach(id => {
                const section = document.getElementById('tab-' + id);
                const navBtn = document.getElementById('nav-' + id);
                if (section) section.classList.add('hidden');
                if (navBtn) {
                    navBtn.classList.remove('bg-amber-700', 'text-white', 'shadow');
                    navBtn.classList.add('hover:bg-amber-800');
                }
            });

            const activeSection = document.getElementById('tab-' + tabId);
            const activeNav = document.getElementById('nav-' + tabId);
            
            if (activeSection) activeSection.classList.remove('hidden');
            if (activeNav) {
                activeNav.classList.add('bg-amber-700', 'text-white', 'shadow');
                activeNav.classList.remove('hover:bg-amber-800');
            }
            
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // --- 2. TIMELINE DATA ---
        const timelineData = [
            { year: "1908", title: "Berdirinya Budi Utomo", desc: "Didirikan oleh dr. Wahidin Sudirohusodo dan Sutomo di STOVIA Batavia. Tonggak awal kebangkitan nasional." },
            { year: "1912", title: "Sarekat Islam & Indische Partij", desc: "Sarekat Dagang Islam diubah menjadi SI, dan Tiga Serangkai mendirikan Indische Partij." },
            { year: "1926", title: "Kongres Pemuda I", desc: "Diadakan di Batavia untuk menyatukan visi organisasi pemuda kedaerahan." },
            { year: "1928", title: "Sumpah Pemuda", desc: "Momen monumental ikrar Satu Nusa, Satu Bangsa, dan Satu Bahasa: Indonesia." },
            { year: "1942", title: "Akhir Kolonial Belanda", desc: "Jepang masuk menggantikan kekuasaan Belanda seiring Perang Dunia II." }
        ];

        function initTimeline() {
            const btnContainer = document.getElementById('timeline-buttons');
            if (!btnContainer) return;
            btnContainer.innerHTML = '';
            timelineData.forEach((item, index) => {
                const btn = document.createElement('button');
                btn.type = 'button';
                btn.className = `px-4 py-2 rounded-xl text-sm font-bold border transition cursor-pointer ${index === 0 ? 'bg-amber-800 text-white border-amber-800' : 'bg-white text-amber-900 border-amber-300 hover:bg-amber-50'}`;
                btn.innerText = item.year;
                btn.onclick = () => selectTimeline(index, btn);
                btnContainer.appendChild(btn);
            });
            if (btnContainer.children[0]) selectTimeline(0, btnContainer.children[0]);
        }

        function selectTimeline(index, element) {
            const btnContainer = document.getElementById('timeline-buttons');
            if (!btnContainer) return;
            Array.from(btnContainer.children).forEach(b => {
                b.className = 'px-4 py-2 rounded-xl text-sm font-bold border bg-white text-amber-900 border-amber-300 hover:bg-amber-50 cursor-pointer';
            });
            element.className = 'px-4 py-2 rounded-xl text-sm font-bold border bg-amber-800 text-white border-amber-800 cursor-pointer';

            const data = timelineData[index];
            document.getElementById('tl-year').innerText = data.year;
            document.getElementById('tl-title').innerText = data.title;
            document.getElementById('tl-desc').innerText = data.desc;
        }

        // --- 3. MINI GAME ---
        const gameData = [
            { q: "Siapa tokoh yang memimpin pendirian Budi Utomo di STOVIA?", options: ["Dr. Sutomo", "Soekarno", "HOS Tjokroaminoto", "Ki Hajar Dewantara"], answer: 0 },
            { q: "Tanggal berapakah Sumpah Pemuda diikrarkan?", options: ["20 Mei 1908", "28 Oktober 1928", "17 Agustus 1945", "1 Juni 1945"], answer: 1 },
            { q: "Partai politik pertama di Indonesia yang terang-terangan menuntut kemerdekaan adalah...", options: ["Budi Utomo", "Sarekat Islam", "Indische Partij", "Gerindo"], answer: 2 },
            { q: "Lagu Indonesia Raya pertama kali diperdengarkan pada acara...", options: ["Kongres Pemuda II", "Sidang BPUPKI", "Proklamasi", "Kongres Budi Utomo"], answer: 0 }
        ];

        let currentGameStep = 0;
        let gameScoreVal = 0;

        function loadGameQuestion() {
            if (currentGameStep >= gameData.length) {
                document.getElementById('game-card').classList.add('hidden');
                document.getElementById('game-feedback').classList.add('hidden');
                document.getElementById('game-finish').classList.remove('hidden');
                document.getElementById('game-final-score').innerText = `Skor Akhir Anda: ${gameScoreVal} dari ${gameData.length * 25}`;
                return;
            }

            const currentG = gameData[currentGameStep];
            document.getElementById('game-progress').innerText = `Tantangan ${currentGameStep + 1} / ${gameData.length}`;
            document.getElementById('game-score').innerText = `Skor: ${gameScoreVal}`;
            document.getElementById('game-question').innerText = currentG.q;

            const optContainer = document.getElementById('game-options');
            optContainer.innerHTML = '';
            currentG.options.forEach((opt, idx) => {
                const btn = document.createElement('button');
                btn.type = 'button';
                btn.className = 'w-full text-left p-3 rounded-xl border border-amber-300 bg-white hover:bg-amber-100 font-medium text-slate-800 transition cursor-pointer';
                btn.innerText = opt;
                btn.onclick = () => checkGameAnswer(idx, currentG.answer);
                optContainer.appendChild(btn);
            });
            document.getElementById('game-feedback').classList.add('hidden');
        }

        function checkGameAnswer(selected, correct) {
            const feedback = document.getElementById('game-feedback');
            feedback.classList.remove('hidden');
            if (selected === correct) {
                gameScoreVal += 25;
                feedback.className = 'mt-4 p-3 rounded-xl text-sm font-semibold bg-green-100 text-green-900 border border-green-300';
                feedback.innerText = '✨ Benar! +25 Poin';
            } else {
                feedback.className = 'mt-4 p-3 rounded-xl text-sm font-semibold bg-red-100 text-red-900 border border-red-300';
                feedback.innerText = '❌ Kurang tepat!';
            }

            setTimeout(() => {
                currentGameStep++;
                loadGameQuestion();
            }, 1000);
        }

        function restartGame() {
            currentGameStep = 0;
            gameScoreVal = 0;
            document.getElementById('game-card').classList.remove('hidden');
            document.getElementById('game-finish').classList.add('hidden');
            loadGameQuestion();
        }

        // --- 4. KUIS LATIHAN ---
        const quizData = [
            { question: "Organisasi modern pertama di Indonesia yang lahir pada tanggal 20 Mei 1908 adalah...", options: ["Sarekat Islam", "Budi Utomo", "Indische Partij", "Perhimpunan Indonesia"], answer: 1, explanation: "Budi Utomo didirikan pada 20 Mei 1908 oleh para pelajar STOVIA." },
            { question: "Faktor internal utama yang mendorong munculnya pergerakan nasional adalah...", options: ["Kemenangan Jepang atas Rusia", "Penderitaan rakyat akibat penjajahan", "Pengaruh Revolusi Prancis", "Masuknya paham liberalisme"], answer: 1, explanation: "Penderitaan akibat kolonialisme memicu kesadaran melawan bersama." },
            { question: "Tokoh motor penggerak Indische Partij bersama Tjipto dan Ki Hajar Dewantara adalah...", options: ["Soekarno", "Douwes Dekker", "HOS Tjokroaminoto", "Mohammad Hatta"], answer: 1, explanation: "Ketiganya dikenal sebagai Tiga Serangkai." },
            { question: "Sumpah Pemuda menegaskan ikrar satu nusa, bangsa, dan bahasa terjadi tahun...", options: ["1908", "1912", "1928", "1945"], answer: 2, explanation: "Sumpah Pemuda dicetuskan pada Kongres Pemuda II tahun 1928." },
            { question: "Sikap organisasi pergerakan yang menolak bekerja sama dengan Belanda disebut...", options: ["Kooperatif", "Radikal / Non-Kooperatif", "Moderat", "Liberal"], answer: 1, explanation: "Non-kooperatif berarti jalur perjuangan tanpa kompromi." },
            { question: "Politik Etis dicetuskan oleh pemerintah kolonial Belanda pada tahun...", options: ["1901", "1908", "1928", "1942"], answer: 0, explanation: "Politik Etis atau Politik Balas Budi dimulai tahun 1901." },
            { question: "Siapakah tokoh pencipta lagu kebangsaan 'Indonesia Raya'?", options: ["W.R. Supratman", "Ibu Soed", "Kusbini", "C. Simanjuntak"], answer: 0, explanation: "W.R. Supratman menciptakan lagu Indonesia Raya." },
            { question: "Perhimpunan Indonesia (PI) adalah organisasi mahasiswa Indonesia yang awalnya didirikan di negara...", options: ["Jerman", "Belanda", "Prancis", "Jepang"], answer: 1, explanation: "Perhimpunan Indonesia didirikan di negeri Belanda oleh para pelajar Indonesia." },
            { question: "Organisasi Sarekat Islam dipimpin oleh tokoh karismatik bernama...", options: ["H.O.S. Tjokroaminoto", "Dr. Wahidin Sudirohusodo", "Sutan Sjahrir", "Amir Sjarifuddin"], answer: 0, explanation: "H.O.S. Tjokroaminoto adalah pemimpin besar Sarekat Islam." },
            { question: "Tujuan utama berdirinya Budi Utomo pada awal pembentukannya adalah...", options: ["Merebut kemerdekaan secara militer", "Memajukan pengajaran, pertanian, dan kebudayaan", "Mendirikan partai politik radikal", "Mengusir seluruh bangsa Eropa"], answer: 1, explanation: "Fokus awal Budi Utomo adalah bidang sosial, budaya, dan pendidikan." }
        ];

        let currentQuestion = 0;
        let score = 0;
        let answered = false;

        function loadQuestion() {
            answered = false;
            const q = quizData[currentQuestion];
            document.getElementById('quiz-progress').innerText = `Soal ${currentQuestion + 1} dari ${quizData.length}`;
            document.getElementById('question-text').innerText = q.question;
            
            const optionsContainer = document.getElementById('options-container');
            optionsContainer.innerHTML = '';
            
            q.options.forEach((opt, idx) => {
                const btn = document.createElement('button');
                btn.type = 'button';
                btn.className = 'w-full text-left p-3 rounded-xl border border-amber-200 bg-amber-50/50 hover:bg-amber-100 font-medium text-slate-700 transition cursor-pointer';
                btn.innerText = opt;
                btn.onclick = () => selectAnswer(idx);
                optionsContainer.appendChild(btn);
            });

            document.getElementById('feedback-box').classList.add('hidden');
            document.getElementById('next-btn').classList.add('hidden');
        }

        function selectAnswer(selectedIndex) {
            if (answered) return;
            answered = true;

            const q = quizData[currentQuestion];
            const buttons = document.getElementById('options-container').children;
            const feedbackBox = document.getElementById('feedback-box');

            if (selectedIndex === q.answer) {
                score++;
                buttons[selectedIndex].className = 'w-full text-left p-3 rounded-xl border border-green-300 bg-green-100 font-medium text-green-900';
                feedbackBox.className = 'mt-6 p-4 rounded-xl text-sm bg-green-50 border border-green-200 text-green-800';
                feedbackBox.innerHTML = `<strong>Benar!</strong> ${q.explanation}`;
            } else {
                buttons[selectedIndex].className = 'w-full text-left p-3 rounded-xl border border-red-300 bg-red-100 font-medium text-red-900';
                buttons[q.answer].className = 'w-full text-left p-3 rounded-xl border border-green-300 bg-green-100 font-medium text-green-900';
                feedbackBox.className = 'mt-6 p-4 rounded-xl text-sm bg-red-50 border border-red-200 text-red-800';
                feedbackBox.innerHTML = `<strong>Kurang tepat.</strong> ${q.explanation}`;
            }

            feedbackBox.classList.remove('hidden');
            document.getElementById('next-btn').classList.remove('hidden');
        }

        function nextQuestion() {
            currentQuestion++;
            if (currentQuestion < quizData.length) {
                loadQuestion();
            } else {
                document.getElementById('quiz-container').classList.add('hidden');
                document.getElementById('quiz-result').classList.remove('hidden');
                document.getElementById('score-text').innerText = `Skor Anda: ${score} dari ${quizData.length} (${score * 10} poin)`;
            }
        }

        function restartQuiz() {
            currentQuestion = 0;
            score = 0;
            document.getElementById('quiz-container').classList.remove('hidden');
            document.getElementById('quiz-result').classList.add('hidden');
            loadQuestion();
        }

        // --- 5. EVALUASI AKHIR ---
        const evaluasiData = [
            { q: "Politik Etis pada 1901 memicu pergerakan nasional lewat program utamanya di bidang...", options: ["Irigasi", "Migrasi", "Edukasi (pendidikan pribumi)", "Kerja rodi"], answer: 2 },
            { q: "Organisasi pertama yang menggunakan nama 'Indonesia' secara tegas di luar negeri adalah...", options: ["Budi Utomo", "Perhimpunan Indonesia (PI)", "Indische Partij", "PNI"], answer: 1 },
            { q: "Kemenangan Jepang atas Rusia pada tahun 1905 memicu kebangkitan karena...", options: ["Bagikan senjata gratis", "Mematahkan mitos supremasi kulit putih atas Asia", "Jepang langsung merdekakan Indonesia", "Rusia sekutu dekat Belanda"], answer: 1 },
            { q: "Pencipta lagu Indonesia Raya yang diperdengarkan di Kongres Pemuda II adalah...", options: ["W.R. Supratman", "Ibu Soed", "C. Simanjuntak", "Kusbini"], answer: 0 },
            { q: "Strategi perjuangan mengirim wakil duduk di dewan rakyat bentukan Belanda disebut...", options: ["Non-kooperatif", "Radikal", "Kooperatif (Moderat)", "Gerilya"], answer: 2 },
            { q: "Douwes Dekker, Tjipto Mangoenkoesoemo, dan Ki Hajar Dewantara mendirikan partai bernama...", options: ["Indische Partij", "Budi Utomo", "Sarekat Islam", "Partai Komunis Indonesia"], answer: 0 },
            { q: "Kongres Pemuda I yang bertujuan menyatukan organisasi pemuda diselenggarakan pada tahun...", options: ["1908", "1912", "1926", "1928"], answer: 2 },
            { q: "Dewan Rakyat bentukan pemerintah kolonial Belanda tempat kaum moderat duduk berjuang disebut...", options: ["Volksraad", "Budi Utomo", "Stovia", "Parindra"], answer: 0 },
            { q: "Organisasi pergerakan nasional yang didirikan oleh Douwes Dekker memiliki ciri khas bersifat...", options: ["Kedaerahan suku", "Indis (Nasional untuk semua golongan)", "Keagamaan eksklusif", "Kooperatif penuh dengan gubernur"], answer: 1 },
            { q: "Faktor eksternal kebangkitan nasional yang berasal dari daratan Cina dipelopori oleh...", options: ["Sun Yat-sen", "Mahatma Gandhi", "Jose Rizal", "Emilio Aguinaldo"], answer: 0 }
        ];

        function initEvaluation() {
            const container = document.getElementById('eval-questions-container');
            if (!container) return;
            container.innerHTML = '';
            evaluasiData.forEach((item, index) => {
                let optionsHtml = '';
                item.options.forEach((opt, optIdx) => {
                    optionsHtml += `
                        <label class="flex items-center space-x-3 p-3 rounded-xl border border-amber-200 bg-amber-50/40 hover:bg-amber-100 cursor-pointer transition text-sm text-slate-700">
                            <input type="radio" name="eval-${index}" value="${optIdx}" class="w-4 h-4 text-amber-800">
                            <span>${opt}</span>
                        </label>`;
                });
                container.innerHTML += `
                    <div class="p-5 rounded-2xl bg-white border border-amber-200 shadow-sm">
                        <p class="font-bold text-amber-950 mb-3">Soal ${index + 1}. ${item.q}</p>
                        <div class="space-y-2">${optionsHtml}</div>
                    </div>`;
            });
        }

        function submitEvaluation() {
            let correctCount = 0;
            let allAnswered = true;

            evaluasiData.forEach((item, index) => {
                if (!document.querySelector(`input[name="eval-${index}"]:checked`)) allAnswered = false;
            });

            if (!allAnswered) {
                alert("Harap jawab semua 10 soal evaluasi terlebih dahulu!");
                return;
            }

            evaluasiData.forEach((item, index) => {
                const selected = document.querySelector(`input[name="eval-${index}"]:checked`);
                if (parseInt(selected.value) === item.answer) correctCount++;
            });

            const finalScore = correctCount * 10;
            document.getElementById('eval-score-text').innerText = `Skor Anda: ${finalScore} / 100 (${correctCount} benar dari 10 soal)`;
            
            let message = "";
            if (finalScore === 100) {
                message = "Luar biasa! Penguasaan materi sejarah pergerakan nasional Anda sangat sempurna!";
            } else if (finalScore >= 80) {
                message = "Sangat baik! Anda sudah memahami sebagian besar materi dengan sangat baik.";
            } else if (finalScore >= 60) {
                message = "Cukup baik, namun disarankan untuk membaca ulang bagian materi.";
            } else {
                message = "Perlu belajar lebih giat lagi. Silakan pelajari kembali tab Materi dan Video.";
            }
            document.getElementById('eval-desc-text').innerText = message;

            document.getElementById('eval-submit-container').classList.add('hidden');
            document.getElementById('eval-result-box').classList.remove('hidden');
            window.scrollTo({ top: document.body.scrollHeight, behavior: 'smooth' });
        }

        function resetEvaluation() {
            initEvaluation();
            document.getElementById('eval-submit-container').classList.remove('hidden');
            document.getElementById('eval-result-box').classList.add('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // Inisialisasi awal saat halaman dimuat
        window.addEventListener('DOMContentLoaded', () => {
            initTimeline();
            loadGameQuestion();
            loadQuestion();
            initEvaluation();
        });
    </script>
</body>
</html>
