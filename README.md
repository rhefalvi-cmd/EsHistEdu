<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EsHist - Pembelajaran Interaktif Pergerakan Nasional (Kelas 11)</title>
    <!-- Tailwind CSS untuk Desain Modern -->
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
            <!-- Navigasi Menu Ditambah Tab Evaluasi -->
            <nav class="flex flex-wrap justify-center gap-1 bg-amber-950/40 p-1 rounded-xl">
                <button onclick="switchTab('materi')" id="nav-materi" class="px-3 py-2 rounded-lg font-semibold text-xs md:text-sm transition bg-amber-700 text-white shadow">Materi</button>
                <button onclick="switchTab('timeline')" id="nav-timeline" class="px-3 py-2 rounded-lg font-semibold text-xs md:text-sm transition hover:bg-amber-800">Timeline</button>
                <button onclick="switchTab('kuis')" id="nav-kuis" class="px-3 py-2 rounded-lg font-semibold text-xs md:text-sm transition hover:bg-amber-800">Kuis Latihan</button>
                <button onclick="switchTab('evaluasi')" id="nav-evaluasi" class="px-3 py-2 rounded-lg font-semibold text-xs md:text-sm transition hover:bg-amber-800">Evaluasi Akhir</button>
            </nav>
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="flex-grow max-w-6xl mx-auto px-4 py-8 w-full">

        <!-- TAB 1: MATERI -->
        <section id="tab-materi" class="space-y-6">
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

            <div class="bg-white rounded-2xl p-6 md:p-8 shadow-sm border border-amber-200">
                <h2 class="text-2xl font-bold text-amber-950 mb-4">Fase-Fase Pergerakan Nasional</h2>
                <div class="space-y-4">
                    <div class="border-l-4 border-amber-600 pl-4 py-1">
                        <h4 class="font-bold text-amber-900">1. Masa Awal Pergerakan (1908 – 1920-an)</h4>
                        <p class="text-sm text-slate-600">Fase pendirian organisasi modern pertama bercorak sosial, budaya, dan pendidikan (Budi Utomo, Sarekat Islam, Indische Partij).</p>
                    </div>
                    <div class="border-l-4 border-amber-700 pl-4 py-1">
                        <h4 class="font-bold text-amber-900">2. Masa Radikal / Non-Kooperatif (1920-an – 1930)</h4>
                        <p class="text-sm text-slate-600">Organisasi bersikap keras dan menolak bekerja sama dengan pemerintah kolonial Belanda karena menuntut kemerdekaan mutlak (PKI, PNI, PI).</p>
                    </div>
                    <div class="border-l-4 border-amber-800 pl-4 py-1">
                        <h4 class="font-bold text-amber-900">3. Masa Moderat / Kooperatif (1930-an – 1942)</h4>
                        <p class="text-sm text-slate-600">Organisasi bersikap lebih lunak, bersedia duduk di dalam Volksraad (Dewan Rakyat) demi memperjuangkan kemajuan secara bertahap (Parindra, Gerindo).</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- TAB 2: TIMELINE INTERAKTIF -->
        <section id="tab-timeline" class="hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 md:p-8 shadow-sm border border-amber-200">
                <h2 class="text-2xl font-bold text-amber-950 mb-2">Garis Waktu Peristiwa Penting</h2>
                <p class="text-slate-600 text-sm mb-6">Klik tombol tahun di bawah ini untuk melihat detail peristiwa penting pergerakan nasional.</p>

                <!-- Tombol Tahun -->
                <div class="flex flex-wrap gap-2 mb-6" id="timeline-buttons">
                    <!-- Dimasukkan lewat JS -->
                </div>

                <!-- Kartu Detail Timeline -->
                <div id="timeline-detail" class="bg-amber-50 p-6 rounded-xl border border-amber-200 transition-all duration-300">
                    <span id="tl-year" class="bg-amber-800 text-white text-xs font-bold px-3 py-1 rounded-full">Tahun</span>
                    <h3 id="tl-title" class="text-xl font-bold text-amber-950 mt-2">Judul Peristiwa</h3>
                    <p id="tl-desc" class="text-slate-700 mt-2 text-sm md:text-base leading-relaxed">Deskripsi lengkap peristiwa akan muncul di sini.</p>
                </div>
            </div>
        </section>

        <!-- TAB 3: KUIS LATIHAN INTERAKTIF -->
        <section id="tab-kuis" class="hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 md:p-8 shadow-sm border border-amber-200 max-w-2xl mx-auto">
                <div id="quiz-container">
                    <div class="flex justify-between items-center mb-4 border-b pb-3">
                        <h2 class="text-xl font-bold text-amber-950">Kuis Latihan Pemahaman</h2>
                        <span id="quiz-progress" class="text-sm font-semibold text-amber-700">Soal 1 dari 5</span>
                    </div>

                    <div id="question-box">
                        <p id="question-text" class="text-lg font-medium text-slate-800 mb-4">Pertanyaan kuis akan tampil di sini...</p>
                        <div id="options-container" class="space-y-3">
                            <!-- Pilihan opsi via JS -->
                        </div>
                    </div>

                    <div id="feedback-box" class="mt-6 hidden p-4 rounded-xl text-sm"></div>

                    <div class="mt-6 flex justify-end">
                        <button id="next-btn" onclick="nextQuestion()" class="hidden bg-amber-800 hover:bg-amber-900 text-white font-semibold px-6 py-2 rounded-xl transition">
                            Selanjutnya
                        </button>
                    </div>
                </div>

                <!-- Hasil Akhir Kuis -->
                <div id="quiz-result" class="hidden text-center py-8">
                    <div class="text-5xl mb-3">🏆</div>
                    <h3 class="text-2xl font-bold text-amber-950">Kuis Selesai!</h3>
                    <p id="score-text" class="text-lg text-slate-700 mt-2">Skor Anda: 0 dari 5</p>
                    <button onclick="restartQuiz()" class="mt-6 bg-amber-800 hover:bg-amber-900 text-white font-semibold px-6 py-2 rounded-xl transition">
                        Ulangi Kuis Latihan
                    </button>
                </div>
            </div>
        </section>

        <!-- TAB 4: EVALUASI AKHIR (UJIAN FORMATIF) -->
        <section id="tab-evaluasi" class="hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 md:p-8 shadow-sm border border-amber-200 max-w-3xl mx-auto">
                <div class="border-b pb-4 mb-6">
                    <h2 class="text-2xl font-bold text-amber-950">Evaluasi Akhir Pembelajaran</h2>
                    <p class="text-sm text-slate-600 mt-1">Jawablah seluruh soal pilihan ganda di bawah ini dengan teliti. Nilai akan dihitung secara otomatis setelah Anda menekan tombol kumpul.</p>
                </div>

                <!-- Daftar Soal Evaluasi -->
                <div id="eval-questions-container" class="space-y-8">
                    <!-- Dirender lewat JavaScript -->
                </div>

                <!-- Tombol Submit Evaluasi -->
                <div id="eval-submit-container" class="mt-8 pt-4 border-t text-center">
                    <button onclick="submitEvaluation()" class="bg-amber-900 hover:bg-amber-950 text-white font-bold px-8 py-3 rounded-xl shadow-md transition">
                        Kumpul dan Lihat Hasil Evaluasi
                    </button>
                </div>

                <!-- Hasil Skor Evaluasi -->
                <div id="eval-result-box" class="hidden mt-6 p-6 rounded-2xl bg-amber-50 border border-amber-300 text-center">
                    <h3 class="text-2xl font-bold text-amber-950 mb-2">📊 Hasil Evaluasi Anda</h3>
                    <p id="eval-score-text" class="text-xl font-semibold text-amber-800 my-2">Skor: 0 / 100</p>
                    <p id="eval-desc-text" class="text-sm text-slate-700 mb-6"></p>
                    <button onclick="resetEvaluation()" class="bg-amber-800 hover:bg-amber-900 text-white font-semibold px-6 py-2 rounded-xl transition">
                        Ulangi Evaluasi
                    </button>
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
            ['materi', 'timeline', 'kuis', 'evaluasi'].forEach(id => {
                document.getElementById('tab-' + id).classList.add('hidden');
                document.getElementById('nav-' + id).classList.remove('bg-amber-700', 'text-white', 'shadow');
                document.getElementById('nav-' + id).classList.add('hover:bg-amber-800');
            });
            document.getElementById('tab-' + tabId).classList.remove('hidden');
            document.getElementById('nav-' + tabId).classList.add('bg-amber-700', 'text-white', 'shadow');
            document.getElementById('nav-' + tabId).classList.remove('hover:bg-amber-800');
            
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // --- 2. TIMELINE DATA ---
        const timelineData = [
            {
                year: "1908",
                title: "Berdirinya Budi Utomo",
                desc: "Didirikan oleh dr. Wahidin Sudirohusodo dan Sutomo di STOVIA Batavia. Dianggap sebagai tonggak awal kebangkitan nasional karena untuk pertama kalinya organisasi modern dengan kesadaran kebangsaan dibentuk."
            },
            {
                year: "1912",
                title: "Sarekat Islam & Indische Partij",
                desc: "Sarekat Dagang Islam diubah menjadi Sarekat Islam (SI) oleh H.O.S. Tjokroaminoto agar merangkul rakyat luas. Pada tahun yang sama, Tiga Serangkai (Douwes Dekker, Tjipto Mangoenkoesoemo, Ki Hajar Dewantara) mendirikan Indische Partij, partai politik pertama yang secara tegas menyuarakan kemerdekaan."
            },
            {
                year: "1926",
                title: "Kongres Pemuda I",
                desc: "Diadakan di Batavia untuk menyatukan berbagai organisasi pemuda kedaerahan (seperti Jong Java, Jong Sumatranen Bond) agar memiliki visi kebangsaan yang utuh."
            },
            {
                year: "1928",
                title: "Sumpah Pemuda (Kongres Pemuda II)",
                desc: "Momen monumental di mana para pemuda dari seluruh Nusantara mengikrarkan Satu Bangsa, Satu Tanah Air, dan Satu Bahasa: Indonesia. Lagu Indonesia Raya ciptaan W.R. Supratman juga diperdengarkan untuk pertama kalinya."
            },
            {
                year: "1942",
                title: "Akhir Masa Kolonial Belanda",
                desc: "Jentikan Perang Dunia II membuat Jepang masuk ke Indonesia, menandai runtuhnya kekuasaan Hindia Belanda dan dimulainya pendudukan militer Jepang."
            }
        ];

        function initTimeline() {
            const btnContainer = document.getElementById('timeline-buttons');
            timelineData.forEach((item, index) => {
                const btn = document.createElement('button');
                btn.className = `px-4 py-2 rounded-xl text-sm font-bold border transition ${index === 0 ? 'bg-amber-800 text-white border-amber-800' : 'bg-white text-amber-900 border-amber-300 hover:bg-amber-50'}`;
                btn.innerText = item.year;
                btn.onclick = () => selectTimeline(index, btn);
                btnContainer.appendChild(btn);
            });
            selectTimeline(0, btnContainer.children[0]);
        }

        function selectTimeline(index, element) {
            Array.from(document.getElementById('timeline-buttons').children).forEach(b => {
                b.className = 'px-4 py-2 rounded-xl text-sm font-bold border bg-white text-amber-900 border-amber-300 hover:bg-amber-50';
            });
            element.className = 'px-4 py-2 rounded-xl text-sm font-bold border bg-amber-800 text-white border-amber-800';

            const data = timelineData[index];
            document.getElementById('tl-year').innerText = data.year;
            document.getElementById('tl-title').innerText = data.title;
            document.getElementById('tl-desc').innerText = data.desc;
        }

        // --- 3. KUIS LATIHAN DATA & LOGIKA ---
        const quizData = [
            {
                question: "Organisasi modern pertama di Indonesia yang lahir pada tanggal 20 Mei 1908 adalah...",
                options: ["Sarekat Islam", "Budi Utomo", "Indische Partij", "Perhimpunan Indonesia"],
                answer: 1,
                explanation: "Budi Utomo didirikan pada 20 Mei 1908 oleh para pelajar STOVIA di bawah pimpinan Sutomo."
            },
            {
                question: "Faktor internal utama yang mendorong munculnya pergerakan nasional adalah...",
                options: ["Kemenangan Jepang atas Rusia", "Penderitaan rakyat akibat penjajahan", "Pengaruh Revolusi Prancis", "Masuknya paham liberalisme dari Eropa"],
                answer: 1,
                explanation: "Penderitaan rakyat akibat kolonialisme yang berkepanjangan memicu tumbuhnya kesadaran untuk melawan secara bersama-sama."
            },
            {
                question: "Siapa tokoh yang dikenal sebagai motor penggerak Indische Partij bersama Douwes Dekker dan Tjipto Mangoenkoesoemo?",
                options: ["Soekarno", "Ki Hajar Dewantara (Suwardi Suryaningrat)", "H.O.S. Tjokroaminoto", "Mohammad Hatta"],
                answer: 1,
                explanation: "Ketiganya dikenal sebagai 'Tiga Serangkai' pendiri Indische Partij."
            },
            {
                question: "Sumpah Pemuda yang menegaskan ikrar satu nusa, satu bangsa, dan satu bahasa terjadi pada tahun...",
                options: ["1908", "1912", "1928", "1945"],
                answer: 2,
                explanation: "Sumpah Pemuda dicetuskan pada Kongres Pemuda II tanggal 28 Oktober 1928."
            },
            {
                question: "Sikap organisasi pergerakan nasional yang menolak bekerja sama sama sekali dengan pemerintah kolonial Belanda disebut...",
                options: ["Kooperatif", "Radikal / Non-Kooperatif", "Moderat", "Liberal"],
                answer: 1,
                explanation: "Non-kooperatif berarti jalur perjuangan radikal tanpa kompromi dengan pihak penjajah."
            }
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
                btn.className = 'w-full text-left p-3 rounded-xl border border-amber-200 bg-amber-50/50 hover:bg-amber-100 font-medium text-slate-700 transition';
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
            const optionsContainer = document.getElementById('options-container');
            const buttons = optionsContainer.children;
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
                document.getElementById('score-text').innerText = `Skor Anda: ${score} dari ${quizData.length} (${score * 20} poin)`;
            }
        }

        function restartQuiz() {
            currentQuestion = 0;
            score = 0;
            document.getElementById('quiz-container').classList.remove('hidden');
            document.getElementById('quiz-result').classList.add('hidden');
            loadQuestion();
        }

        // --- 4. EVALUASI AKHIR DATA & LOGIKA ---
        const evaluasiData = [
            {
                q: "Politik Etis yang diterapkan oleh pemerintah kolonial Belanda pada tahun 1901 secara tidak langsung memicu pergerakan nasional melalui program...",
                options: ["Irigasi pertanian", "Migrasi/Transmigrasi", "Edukasi (pendidikan kaum pribumi)", "Kerja rodi pembangunan"],
                answer: 2
            },
            {
                q: "Organisasi pertama yang menggunakan nama 'Indonesia' secara tegas pada nama organisasi dan ruang lingkup perjuangannya di negeri Belanda adalah...",
                options: ["Budi Utomo", "Perhimpunan Indonesia (PI)", "Indische Partij", "Partai Nasional Indonesia (PNI)"],
                answer: 1
            },
            {
                q: "Salah satu faktor eksternal kebangkitan nasional di Indonesia adalah kemenangan Jepang atas Rusia pada tahun 1905. Hal ini penting karena...",
                options: ["Jepang membagikan senjata gratis ke Indonesia", "Mematahkan mitos supremasi bangsa kulit putih atas bangsa Asia", "Jepang langsung memerdekakan Indonesia", "Rusia adalah sekutu dekat Belanda"],
                answer: 1
            },
            {
                q: "Tokoh pencipta lagu kebangsaan 'Indonesia Raya' yang pertama kali diperdengarkan pada Kongres Pemuda II adalah...",
                options: ["W.R. Supratman", "Ibu Soed", "C. Simanjuntak", "Kusbini"],
                answer: 0
            },
            {
                q: "Strategi perjuangan organisasi yang bersedia mengirimkan wakilnya duduk di dalam dewan rakyat bentukan Belanda (Volksraad) dikenal sebagai metode...",
                options: ["Non-kooperatif", "Radikal", "Kooperatif (Moderat)", "Gerilya"],
                answer: 2
            }
        ];

        function initEvaluation() {
            const container = document.getElementById('eval-questions-container');
            container.innerHTML = '';
            
            evaluasiData.forEach((item, index) => {
                let optionsHtml = '';
                item.options.forEach((opt, optIdx) => {
                    optionsHtml += `
                        <label class="flex items-center space-x-3 p-3 rounded-xl border border-amber-200 bg-amber-50/40 hover:bg-amber-100 cursor-pointer transition text-sm text-slate-700">
                            <input type="radio" name="eval-${index}" value="${optIdx}" class="w-4 h-4 text-amber-800 focus:ring-amber-700">
                            <span>${opt}</span>
                        </label>
                    `;
                });

                container.innerHTML += `
                    <div class="p-5 rounded-2xl bg-white border border-amber-200 shadow-sm">
                        <p class="font-bold text-amber-950 mb-3">Soal ${index + 1}. ${item.q}</p>
                        <div class="space-y-2">${optionsHtml}</div>
                    </div>
                `;
            });
        }

        function submitEvaluation() {
            let correctCount = 0;
            let allAnswered = true;

            evaluasiData.forEach((item, index) => {
                const selected = document.querySelector(`input[name="eval-${index}"]:checked`);
                if (!selected) {
                    allAnswered = false;
                }
            });

            if (!allAnswered) {
                alert("Harap jawab semua soal evaluasi terlebih dahulu sebelum mengumpulkan!");
                return;
            }

            evaluasiData.forEach((item, index) => {
                const selected = document.querySelector(`input[name="eval-${index}"]:checked`);
                if (parseInt(selected.value) === item.answer) {
                    correctCount++;
                }
            });

            const finalScore = correctCount * 20; // 5 soal x 20 = 100
            
            // Tampilkan hasil
            document.getElementById('eval-score-text').innerText = `Skor Anda: ${finalScore} dari 100 (${correctCount} benar dari 5 soal)`;
            
            let message = "";
            if (finalScore === 100) {
                message = "Luar biasa! Penguasaan materi sejarah pergerakan nasional Anda sangat sempurna!";
            } else if (finalScore >= 80) {
                message = "Sangat baik! Anda sudah memahami sebagian besar materi dengan sangat baik.";
            } else if (finalScore >= 60) {
                message = "Cukup baik, namun disarankan untuk membaca ulang bagian materi dan timeline.";
            } else {
                message = "Perlu belajar lebih giat lagi. Silakan pelajari kembali tab Materi dan Kuis Latihan.";
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
        window.onload = () => {
            initTimeline();
            loadQuestion();
            initEvaluation();
        };
    </script>
</body>
</html>
