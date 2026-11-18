<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EsHist - Eksplorasi Sejarah Pergerakan Nasional</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Plus Jakarta Sans & Merriweather -->
    <link href="https://fonts.googleapis.com/css2?family=Merriweather:ital,wght@0,700;0,900;1,400&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Font Awesome untuk Ikon -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['"Plus Jakarta Sans"', 'sans-serif'],
                        serif: ['"Merriweather"', 'serif'],
                    },
                    colors: {
                        brand: {
                            red: '#991B1B',
                            darkred: '#7F1D1D',
                            gold: '#D97706',
                            cream: '#FFFBEB',
                            slate: '#1E293B'
                        }
                    }
                }
            }
        }
    </script>

    <style>
        /* Custom styles untuk efek 3D Flip pada Game Mencocokkan Tokoh & Organisasi */
        .perspective-1000 {
            perspective: 1000px;
        }
        .transform-style-3d {
            transform-style: preserve-3d;
        }
        .backface-hidden {
            backface-visibility: hidden;
        }
        .rotate-y-180 {
            transform: rotateY(180deg);
        }
        .card-flipped {
            transform: rotateY(180deg);
        }
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        ::-webkit-scrollbar-thumb {
            background: #991B1B;
            border-radius: 4px;
        }
        
        /* Animasi Transisi Halus Antar Menu */
        @keyframes fadeInScale {
            from {
                opacity: 0;
                transform: translateY(12px) scale(0.99);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }
        .tab-section {
            animation: fadeInScale 0.35s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 font-sans antialiased selection:bg-brand-red selection:text-white">

    <!-- NAVBAR -->
    <nav class="sticky top-0 z-50 bg-white/95 backdrop-blur-md border-b border-slate-200 shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16 items-center">
                <!-- Logo EsHist -->
                <div class="flex items-center space-x-3 cursor-pointer" onclick="switchTab('beranda')">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-brand-red to-red-600 flex items-center justify-center text-white font-serif font-bold text-xl shadow-md">
                        E
                    </div>
                    <div>
                        <span class="font-serif font-black text-xl tracking-tight text-slate-900">Es<span class="text-brand-red">Hist</span></span>
                        <p class="text-[10px] text-slate-500 font-medium -mt-1">Explore History Indonesia</p>
                    </div>
                </div>

                <!-- Menu Desktop -->
                <div class="hidden lg:flex space-x-1">
                    <button onclick="switchTab('beranda')" id="nav-beranda" class="nav-btn px-3 py-2 rounded-lg text-sm font-semibold text-brand-red bg-red-50 transition">Beranda</button>
                    <button onclick="switchTab('cptp')" id="nav-cptp" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium text-slate-600 hover:text-brand-red hover:bg-slate-100 transition">CP & TP</button>
                    <button onclick="switchTab('materi')" id="nav-materi" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium text-slate-600 hover:text-brand-red hover:bg-slate-100 transition">Materi & Organisasi</button>
                    <button onclick="switchTab('video')" id="nav-video" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium text-slate-600 hover:text-brand-red hover:bg-slate-100 transition">Video Edukasi</button>
                    <button onclick="switchTab('game')" id="nav-game" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium text-slate-600 hover:text-brand-red hover:bg-slate-100 transition">Game Edukasi</button>
                    <button onclick="switchTab('evaluasi')" id="nav-evaluasi" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium text-slate-600 hover:text-brand-red hover:bg-slate-100 transition">Evaluasi (20 Soal)</button>
                    <button onclick="switchTab('pustaka')" id="nav-pustaka" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium text-slate-600 hover:text-brand-red hover:bg-slate-100 transition">Daftar Pustaka</button>
                </div>

                <!-- Tombol Menu Mobile -->
                <div class="lg:hidden">
                    <button id="mobile-menu-btn" class="p-2 rounded-lg text-slate-600 hover:bg-slate-100 focus:outline-none">
                        <i class="fas fa-bars text-xl"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Menu Mobile Dropdown -->
        <div id="mobile-menu" class="hidden lg:hidden bg-white border-b border-slate-200 px-4 pt-2 pb-4 space-y-1 shadow-lg">
            <button onclick="switchTab('beranda'); toggleMobileMenu()" class="block w-full text-left px-3 py-2.5 rounded-lg text-sm font-semibold text-slate-700 hover:bg-red-50 hover:text-brand-red">🏠 Beranda</button>
            <button onclick="switchTab('cptp'); toggleMobileMenu()" class="block w-full text-left px-3 py-2.5 rounded-lg text-sm font-semibold text-slate-700 hover:bg-red-50 hover:text-brand-red">🎯 CP & TP</button>
            <button onclick="switchTab('materi'); toggleMobileMenu()" class="block w-full text-left px-3 py-2.5 rounded-lg text-sm font-semibold text-slate-700 hover:bg-red-50 hover:text-brand-red">📚 Materi & Organisasi</button>
            <button onclick="switchTab('video'); toggleMobileMenu()" class="block w-full text-left px-3 py-2.5 rounded-lg text-sm font-semibold text-slate-700 hover:bg-red-50 hover:text-brand-red">🎬 Video Edukasi</button>
            <button onclick="switchTab('game'); toggleMobileMenu()" class="block w-full text-left px-3 py-2.5 rounded-lg text-sm font-semibold text-slate-700 hover:bg-red-50 hover:text-brand-red">🎮 Game Tokoh & Organisasi</button>
            <button onclick="switchTab('evaluasi'); toggleMobileMenu()" class="block w-full text-left px-3 py-2.5 rounded-lg text-sm font-semibold text-slate-700 hover:bg-red-50 hover:text-brand-red">📝 Evaluasi (20 Soal)</button>
            <button onclick="switchTab('pustaka'); toggleMobileMenu()" class="block w-full text-left px-3 py-2.5 rounded-lg text-sm font-semibold text-slate-700 hover:bg-red-50 hover:text-brand-red">📖 Daftar Pustaka</button>
        </div>
    </nav>

    <!-- KONTEN UTAMA -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 min-h-[calc(100vh-140px)]">

        <!-- 1. SECTION BERANDA -->
        <section id="sec-beranda" class="tab-section space-y-10">
            <!-- Hero Banner -->
            <div class="relative overflow-hidden rounded-3xl bg-gradient-to-br from-slate-900 via-brand-darkred to-brand-red text-white p-8 md:p-14 shadow-xl">
                <div class="relative z-10 max-w-3xl space-y-6">
                    <span class="inline-flex items-center px-3.5 py-1.5 rounded-full text-xs font-semibold bg-amber-500/20 text-amber-300 border border-amber-400/30">
                        <i class="fas fa-landmark mr-2"></i> Media Pembelajaran Sejarah Interaktif
                    </span>
                    <h1 class="font-serif text-3xl sm:text-4xl md:text-5xl font-black leading-tight">
                        Masa Pergerakan Nasional Indonesia (1908–1942)
                    </h1>
                    <p class="text-slate-200 text-base sm:text-lg leading-relaxed">
                        Selamat datang di <strong>EsHist</strong>. Pelajari bagaimana perubahan strategi perjuangan bangsa Indonesia dari perlawanan fisik kedaerahan menuju perjuangan modern melalui organisasi nasional yang terstruktur dan visioner.
                    </p>
                    <div class="flex flex-wrap gap-4 pt-2">
                        <button onclick="switchTab('materi')" class="px-6 py-3.5 bg-amber-500 hover:bg-amber-400 text-slate-900 font-bold rounded-xl shadow-lg transition transform hover:-translate-y-0.5 flex items-center">
                            <i class="fas fa-book-open mr-2"></i> Mulai Belajar Materi
                        </button>
                        <button onclick="switchTab('game')" class="px-6 py-3.5 bg-white/15 hover:bg-white/25 text-white font-semibold rounded-xl backdrop-blur-sm border border-white/20 transition flex items-center">
                            <i class="fas fa-gamepad mr-2"></i> Mainkan Game Sejarah
                        </button>
                    </div>
                </div>
                <!-- Dekorasi Latar -->
                <div class="hidden lg:block absolute right-8 bottom-0 opacity-15 text-[220px] font-serif font-black select-none pointer-events-none">
                    1908
                </div>
            </div>

            <!-- Grid Navigasi Fitur EsHist -->
            <div>
                <h2 class="text-xl font-bold text-slate-800 mb-5 flex items-center">
                    <span class="w-2 h-6 bg-brand-red rounded-full mr-3"></span> Jelajahi Fitur Pembelajaran EsHist
                </h2>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
                    <div onclick="switchTab('cptp')" class="group bg-white p-6 rounded-2xl border border-slate-200 shadow-sm hover:shadow-md hover:border-brand-red/40 transition cursor-pointer">
                        <div class="w-12 h-12 rounded-xl bg-blue-50 text-blue-600 flex items-center justify-center text-xl mb-4 group-hover:scale-110 transition">
                            <i class="fas fa-bullseye"></i>
                        </div>
                        <h3 class="font-bold text-lg text-slate-900 mb-2">CP & TP Pembelajaran</h3>
                        <p class="text-sm text-slate-600">Pahami Capaian Pembelajaran dan Tujuan Pembelajaran Kurikulum Merdeka materi Pergerakan Nasional.</p>
                    </div>
                    <div onclick="switchTab('materi')" class="group bg-white p-6 rounded-2xl border border-slate-200 shadow-sm hover:shadow-md hover:border-brand-red/40 transition cursor-pointer">
                        <div class="w-12 h-12 rounded-xl bg-red-50 text-brand-red flex items-center justify-center text-xl mb-4 group-hover:scale-110 transition">
                            <i class="fas fa-scroll"></i>
                        </div>
                        <h3 class="font-bold text-lg text-slate-900 mb-2">Materi & Organisasi Detail</h3>
                        <p class="text-sm text-slate-600">Kupas tuntas faktor pendorong, periodisasi, hingga 10 organisasi penting seperti Budi Utomo, SI, IP, PNI, dll.</p>
                    </div>
                    <div onclick="switchTab('video')" class="group bg-white p-6 rounded-2xl border border-slate-200 shadow-sm hover:shadow-md hover:border-brand-red/40 transition cursor-pointer">
                        <div class="w-12 h-12 rounded-xl bg-amber-50 text-amber-600 flex items-center justify-center text-xl mb-4 group-hover:scale-110 transition">
                            <i class="fas fa-play-circle"></i>
                        </div>
                        <h3 class="font-bold text-lg text-slate-900 mb-2">Video Edukasi</h3>
                        <p class="text-sm text-slate-600">Simak video pembelajaran YouTube tentang kebangkitan nasional dan Kongres Pemuda II (Sumpah Pemuda).</p>
                    </div>
                    <div onclick="switchTab('game')" class="group bg-white p-6 rounded-2xl border border-slate-200 shadow-sm hover:shadow-md hover:border-brand-red/40 transition cursor-pointer">
                        <div class="w-12 h-12 rounded-xl bg-emerald-50 text-emerald-600 flex items-center justify-center text-xl mb-4 group-hover:scale-110 transition">
                            <i class="fas fa-puzzle-piece"></i>
                        </div>
                        <h3 class="font-bold text-lg text-slate-900 mb-2">Game Tokoh & Organisasi</h3>
                        <p class="text-sm text-slate-600">Uji ketelitianmu mencocokkan kartu Tokoh Sentral dengan Organisasi Pergerakan Nasional yang dipimpinnya.</p>
                    </div>
                    <div onclick="switchTab('evaluasi')" class="group bg-white p-6 rounded-2xl border border-slate-200 shadow-sm hover:shadow-md hover:border-brand-red/40 transition cursor-pointer">
                        <div class="w-12 h-12 rounded-xl bg-purple-50 text-purple-600 flex items-center justify-center text-xl mb-4 group-hover:scale-110 transition">
                            <i class="fas fa-tasks"></i>
                        </div>
                        <h3 class="font-bold text-lg text-slate-900 mb-2">Evaluasi (20 Soal)</h3>
                        <p class="text-sm text-slate-600">Kerjakan 20 soal latihan pilihan ganda lengkap dengan tombol mulai, skor otomatis, dan pembahasan.</p>
                    </div>
                    <div onclick="switchTab('pustaka')" class="group bg-white p-6 rounded-2xl border border-slate-200 shadow-sm hover:shadow-md hover:border-brand-red/40 transition cursor-pointer">
                        <div class="w-12 h-12 rounded-xl bg-slate-100 text-slate-700 flex items-center justify-center text-xl mb-4 group-hover:scale-110 transition">
                            <i class="fas fa-book"></i>
                        </div>
                        <h3 class="font-bold text-lg text-slate-900 mb-2">Daftar Pustaka</h3>
                        <p class="text-sm text-slate-600">Referensi akademik dan buku sejarah terpercaya yang digunakan dalam penyusunan materi EsHist.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- 2. SECTION CP & TP -->
        <section id="sec-cptp" class="tab-section hidden space-y-8">
            <div class="bg-white rounded-3xl p-6 sm:p-10 border border-slate-200 shadow-sm">
                <div class="border-b border-slate-100 pb-6 mb-6">
                    <span class="text-xs font-bold uppercase tracking-wider text-brand-red bg-red-50 px-3 py-1 rounded-full">Kurikulum Merdeka • Fase F (Kelas XI)</span>
                    <h2 class="font-serif text-2xl sm:text-3xl font-bold text-slate-900 mt-3">Capaian Pembelajaran (CP) & Tujuan Pembelajaran (TP)</h2>
                </div>

                <div class="bg-amber-50/70 border-l-4 border-amber-500 p-6 rounded-r-2xl mb-8">
                    <h3 class="font-bold text-lg text-amber-900 flex items-center mb-2">
                        <i class="fas fa-award mr-2 text-amber-600"></i> Capaian Pembelajaran (CP)
                    </h3>
                    <p class="text-slate-700 leading-relaxed text-sm sm:text-base">
                        Pada akhir fase ini, peserta didik mampu mengembangkan konsep-konsep dasar sejarah untuk mengkaji peristiwa sejarah dalam lintasan lokal, nasional, dan global. Melalui literasi, diskusi, kunjungan langsung ke tempat bersejarah, dan penelitian berbasis proyek kolaboratif peserta didik mampu <strong>menganalisis serta mengevaluasi berbagai peristiwa sejarah yang terjadi di Indonesia meliputi masa Pergerakan Nasional Indonesia</strong>, menumbuhkan kesadaran kebangsaan, serta merefleksikan nilai-nilai perjuangan tokoh pergerakan dalam kehidupan berbangsa masa kini.
                    </p>
                </div>

                <div>
                    <h3 class="font-bold text-lg text-slate-900 flex items-center mb-4">
                        <i class="fas fa-list-check mr-2 text-brand-red"></i> Tujuan Pembelajaran (TP)
                    </h3>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div class="p-5 rounded-2xl bg-slate-50 border border-slate-200 flex items-start space-x-4">
                            <div class="w-8 h-8 rounded-full bg-brand-red text-white font-bold flex items-center justify-center shrink-0 text-sm">1</div>
                            <div>
                                <h4 class="font-bold text-slate-800 text-sm sm:text-base">Menganalisis Faktor Pendorong</h4>
                                <p class="text-xs sm:text-sm text-slate-600 mt-1">Peserta didik mampu menganalisis faktor internal dan eksternal lahirnya kesadaran nasionalisme dan pergerakan nasional di Indonesia.</p>
                            </div>
                        </div>
                        <div class="p-5 rounded-2xl bg-slate-50 border border-slate-200 flex items-start space-x-4">
                            <div class="w-8 h-8 rounded-full bg-brand-red text-white font-bold flex items-center justify-center shrink-0 text-sm">2</div>
                            <div>
                                <h4 class="font-bold text-slate-800 text-sm sm:text-base">Mengklasifikasikan Strategi Perjuangan</h4>
                                <p class="text-xs sm:text-sm text-slate-600 mt-1">Peserta didik mampu membedakan strategi perjuangan organisasi pergerakan nasional pada periode awal, radikal, hingga moderat/bertahan.</p>
                            </div>
                        </div>
                        <div class="p-5 rounded-2xl bg-slate-50 border border-slate-200 flex items-start space-x-4">
                            <div class="w-8 h-8 rounded-full bg-brand-red text-white font-bold flex items-center justify-center shrink-0 text-sm">3</div>
                            <div>
                                <h4 class="font-bold text-slate-800 text-sm sm:text-base">Mengevaluasi Peran Organisasi & Tokoh</h4>
                                <p class="text-xs sm:text-sm text-slate-600 mt-1">Peserta didik mampu mengidentifikasi asas, tujuan, serta peran penting berbagai organisasi pergerakan nasional dalam membentuk identitas keindonesiaan.</p>
                            </div>
                        </div>
                        <div class="p-5 rounded-2xl bg-slate-50 border border-slate-200 flex items-start space-x-4">
                            <div class="w-8 h-8 rounded-full bg-brand-red text-white font-bold flex items-center justify-center shrink-0 text-sm">4</div>
                            <div>
                                <h4 class="font-bold text-slate-800 text-sm sm:text-base">Merefleksikan Nilai Persatuan</h4>
                                <p class="text-xs sm:text-sm text-slate-600 mt-1">Peserta didik mampu menyimpulkan makna peristiwa Kongres Pemuda II (Sumpah Pemuda 1928) sebagai tonggak persatuan bangsa Indonesia.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 3. SECTION MATERI & ORGANISASI DETAIL -->
        <section id="sec-materi" class="tab-section hidden space-y-8">
            <div class="bg-white rounded-3xl p-6 sm:p-10 border border-slate-200 shadow-sm space-y-8">
                <div>
                    <span class="text-xs font-bold uppercase tracking-wider text-brand-red bg-red-50 px-3 py-1 rounded-full">Modul Pembelajaran Mendalam</span>
                    <h2 class="font-serif text-2xl sm:text-3xl font-bold text-slate-900 mt-3">Hakikat & Dinamika Pergerakan Nasional (1908–1942)</h2>
                </div>
                
                <div class="space-y-4 text-slate-700 leading-relaxed text-sm sm:text-base">
                    <p>
                        <strong>Pergerakan Nasional</strong> adalah fase sejarah perjuangan bangsa Indonesia dalam menentang kolonialisme dan imperialisme Belanda yang ditandai dengan munculnya kesadaran kolektif sebagai satu bangsa (nasionalisme). Istilah <em>"pergerakan"</em> merujuk pada dinamika perubahan sosial-politik masyarakat pribumi yang mulai meninggalkan pola perlawanan tradisional menuju gerakan modern yang terorganisir.
                    </p>
                    <p>
                        Tonggak lahirnya pergerakan nasional ditandai oleh berdirinya <strong>Budi Utomo pada 20 Mei 1908</strong>. Sejak saat itu, perjuangan tidak lagi mengandalkan kekuatan senjata secara sporadis di tingkat lokal, melainkan memanfaatkan kekuatan intelektual, diplomasi politik, jalur pendidikan, penguatan ekonomi kerakyatan, serta penyebaran gagasan melalui media pers berbahasa Melayu.
                    </p>
                </div>

                <!-- Tabel Perbandingan Perjuangan Sebelum & Sesudah 1908 -->
                <div class="overflow-hidden rounded-2xl border border-slate-200">
                    <div class="bg-slate-800 text-white px-5 py-3 font-bold text-sm flex items-center">
                        <i class="fas fa-balance-scale mr-2 text-amber-400"></i> Transformasi Strategi Perjuangan Bangsa Indonesia
                    </div>
                    <div class="overflow-x-auto">
                        <table class="w-full text-left border-collapse text-xs sm:text-sm">
                            <thead>
                                <tr class="bg-slate-100 text-slate-800 border-b border-slate-200">
                                    <th class="p-3.5 font-bold w-1/4">Aspek Perjuangan</th>
                                    <th class="p-3.5 font-bold w-3/8 text-red-900">Sebelum Tahun 1908 (Tradisional)</th>
                                    <th class="p-3.5 font-bold w-3/8 text-emerald-900">Sesudah Tahun 1908 (Pergerakan Nasional)</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-slate-200 bg-white">
                                <tr>
                                    <td class="p-3.5 font-semibold text-slate-900">Sifat & Cakupan</td>
                                    <td class="p-3.5 text-slate-600">Kedaerahan (lokal), terpisah-pisah antar kerajaan/daerah sehingga mudah diadu domba (<em>devide et impera</em>).</td>
                                    <td class="p-3.5 text-slate-700">Nasional, menyatukan berbagai suku, agama, dan daerah dalam satu identitas keindonesiaan.</td>
                                </tr>
                                <tr>
                                    <td class="p-3.5 font-semibold text-slate-900">Kepemimpinan</td>
                                    <td class="p-3.5 text-slate-600">Bergantung pada tokoh kharismatik (raja, sultan, bangsawan, atau ulama). Jika pemimpin tertangkap, perlawanan padam.</td>
                                    <td class="p-3.5 text-slate-700">Dipimpin oleh golongan terpelajar (kaum intelektual) dengan sistem kaderisasi yang berkesinambungan.</td>
                                </tr>
                                <tr>
                                    <td class="p-3.5 font-semibold text-slate-900">Bentuk Perlawanan</td>
                                    <td class="p-3.5 text-slate-600">Perlawanan fisik menggunakan senjata tradisional melawan persenjataan modern Belanda.</td>
                                    <td class="p-3.5 text-slate-700">Perjuangan modern melalui organisasi politik, diplomasi, mogok kerja, pers, dan pendidikan.</td>
                                </tr>
                                <tr>
                                    <td class="p-3.5 font-semibold text-slate-900">Visi & Tujuan</td>
                                    <td class="p-3.5 text-slate-600">Mengusir penjajah dari wilayah kerajaan masing-masing.</td>
                                    <td class="p-3.5 text-slate-700">Mencapai Indonesia Merdeka yang berdaulat sebagai satu negara-bangsa (<em>nation-state</em>).</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Faktor Internal & Eksternal -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 pt-2">
                    <div class="bg-red-50/60 p-6 rounded-2xl border border-red-100">
                        <h3 class="font-bold text-lg text-brand-darkred mb-3 flex items-center">
                            <i class="fas fa-house-user mr-2"></i> Faktor Internal (Dari Dalam Negeri)
                        </h3>
                        <ul class="space-y-3 text-sm text-slate-700 list-disc pl-5">
                            <li><strong>Penderitaan Akibat Kolonialisme:</strong> Eksploitasi ekonomi melalui Sistem Tanam Paksa (<em>Cultuurstelsel</em>), Politik Pintu Terbuka, pajak berat, serta diskriminasi rasial hukum kolonial menimbulkan kesengsaraan kolektif.</li>
                            <li><strong>Lahirnya Golongan Terpelajar (Elit Baru):</strong> Kebijakan <em>Politik Etis</em> (Trilogi Van Deventer: Edukasi, Irigasi, Emigrasi) membuka akses sekolah Barat (STOVIA, OSVIA, RHS, THS) yang melahirkan intelektual pribumi berwawasan luas.</li>
                            <li><strong>Kenangan Kejayaan Masa Lampau:</strong> Memori sejarah kebesaran Kerajaan Sriwijaya dan Majapahit sebagai negara maritim dan nusantara yang berdaulat menumbuhkan harga diri bangsa.</li>
                            <li><strong>Perkembangan Pers & Bahasa Melayu:</strong> Surat kabar seperti <em>Medan Prijaji</em> (R.M. Tirto Adhi Soerjo), <em>Oetoesan Hindia</em>, dan <em>De Express</em> menjadi ruang publik penyebaran ide kemerdekaan.</li>
                        </ul>
                    </div>

                    <div class="bg-blue-50/60 p-6 rounded-2xl border border-blue-100">
                        <h3 class="font-bold text-lg text-blue-900 mb-3 flex items-center">
                            <i class="fas fa-globe-asia mr-2"></i> Faktor Eksternal (Dari Luar Negeri)
                        </h3>
                        <ul class="space-y-3 text-sm text-slate-700 list-disc pl-5">
                            <li><strong>Kemenangan Jepang atas Rusia (1905):</strong> Keberhasilan Jepang mengalahkan kekaisaran Rusia membuktikan bahwa bangsa Asia mampu menandingi bangsa Eropa, meruntuhkan mitos superioritas kulit putih.</li>
                            <li><strong>Kebangkitan Nasionalisme Asia-Afrika:</strong> Gerakan <em>Swadeshi</em> dan <em>Satyagraha</em> Mahatma Gandhi di India, Revolusi Tiongkok (Sun Yat Sen), gerakan Jose Rizal di Filipina, dan Gerakan Turki Muda.</li>
                            <li><strong>Masuknya Paham-Paham Baru Eropa:</strong> Liberalisme, Demokrasi, Nasionalisme, Sosialisme, dan Pan-Islamisme yang diserap oleh mahasiswa Indonesia yang menempuh studi di negeri Belanda.</li>
                            <li><strong>Deklarasi Woodrow Wilson (1918):</strong> Prinsip <em>Right of Self-Determination</em> (hak menentukan nasib sendiri bagi setiap bangsa) pasca Perang Dunia I memperkuat legitimasi tuntutan kemerdekaan.</li>
                        </ul>
                    </div>
                </div>

                <!-- Periodisasi -->
                <div class="bg-slate-900 text-white p-6 sm:p-8 rounded-2xl space-y-4">
                    <h3 class="font-bold text-lg text-amber-400 flex items-center">
                        <i class="fas fa-layer-group mr-2"></i> Periodisasi & Strategi Pergerakan Nasional
                    </h3>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 text-sm">
                        <div class="bg-white/10 p-5 rounded-xl border border-white/10 space-y-2">
                            <span class="inline-block px-2.5 py-0.5 rounded bg-amber-500/20 text-amber-300 text-xs font-bold">1908 – 1920</span>
                            <h4 class="font-bold text-white text-base">1. Masa Pembentukan (Awal)</h4>
                            <p class="text-slate-300 text-xs leading-relaxed">
                                Organisasi masih berfokus pada perbaikan sosial, budaya, pendidikan, dan ekonomi rakyat. Strateginya bersifat <strong>kooperatif</strong> (bersedia bekerja sama dengan pemerintah kolonial demi kemajuan pribumi). Contoh: Budi Utomo, Sarekat Islam awal, Muhammadiyah.
                            </p>
                        </div>
                        <div class="bg-white/10 p-5 rounded-xl border border-white/10 space-y-2">
                            <span class="inline-block px-2.5 py-0.5 rounded bg-red-500/20 text-red-300 text-xs font-bold">1920 – 1930</span>
                            <h4 class="font-bold text-white text-base">2. Masa Radikal (Non-Kooperatif)</h4>
                            <p class="text-slate-300 text-xs leading-relaxed">
                                Kekecewaan terhadap janji palsu Belanda (<em>Janji November 1918</em>) memicu lahirnya organisasi radikal. Strateginya <strong>non-kooperatif</strong> (menolak duduk di Volksraad), mengandalkan kekuatan sendiri (<em>self-help</em>), dan menuntut tegas Indonesia Merdeka. Contoh: Indische Partij, PI, PNI.
                            </p>
                        </div>
                        <div class="bg-white/10 p-5 rounded-xl border border-white/10 space-y-2">
                            <span class="inline-block px-2.5 py-0.5 rounded bg-emerald-500/20 text-emerald-300 text-xs font-bold">1930 – 1942</span>
                            <h4 class="font-bold text-white text-base">3. Masa Moderat (Bertahan)</h4>
                            <p class="text-slate-300 text-xs leading-relaxed">
                                Akibat tindakan represif Gubernur Jenderal De Jonge yang menangkap dan mengasingkan tokoh radikal (Soekarno, Hatta, Sjahrir), organisasi mengubah taktik menjadi <strong>kooperatif moderat</strong> dengan memanfaatkan dewan perwakilan (Volksraad) untuk memperjuangkan otonomi dan parlemen. Contoh: Parindra, Gerindo, GAPI.
                            </p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Eksplorasi 10 Organisasi -->
            <div class="bg-white rounded-3xl p-6 sm:p-10 border border-slate-200 shadow-sm">
                <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 mb-6">
                    <div>
                        <h2 class="font-serif text-2xl font-bold text-slate-900">Profil Lengkap 10 Organisasi Pergerakan Nasional</h2>
                        <p class="text-sm text-slate-600 mt-1">Gunakan filter periode di bawah ini untuk mempelajari asas, strategi, dan sejarah tiap organisasi secara detail.</p>
                    </div>
                    <!-- Filter Buttons -->
                    <div class="flex flex-wrap gap-2">
                        <button onclick="filterOrg('semua', this)" class="org-filter-btn px-3.5 py-1.5 rounded-full text-xs font-bold bg-brand-red text-white transition">Semua (10)</button>
                        <button onclick="filterOrg('awal', this)" class="org-filter-btn px-3.5 py-1.5 rounded-full text-xs font-semibold bg-slate-100 text-slate-600 hover:bg-slate-200 transition">Masa Awal</button>
                        <button onclick="filterOrg('radikal', this)" class="org-filter-btn px-3.5 py-1.5 rounded-full text-xs font-semibold bg-slate-100 text-slate-600 hover:bg-slate-200 transition">Masa Radikal</button>
                        <button onclick="filterOrg('moderat', this)" class="org-filter-btn px-3.5 py-1.5 rounded-full text-xs font-semibold bg-slate-100 text-slate-600 hover:bg-slate-200 transition">Masa Moderat</button>
                        <button onclick="filterOrg('pemuda', this)" class="org-filter-btn px-3.5 py-1.5 rounded-full text-xs font-semibold bg-slate-100 text-slate-600 hover:bg-slate-200 transition">Pemuda & Pendidikan</button>
                    </div>
                </div>

                <div id="org-container" class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <!-- Diisi via JavaScript -->
                </div>
            </div>
        </section>

        <!-- 4. SECTION VIDEO EDUKASI -->
        <section id="sec-video" class="tab-section hidden space-y-8">
            <div class="bg-white rounded-3xl p-6 sm:p-10 border border-slate-200 shadow-sm">
                <div class="mb-6">
                    <span class="text-xs font-bold uppercase tracking-wider text-red-700 bg-red-50 px-3 py-1 rounded-full">
                        <i class="fab fa-youtube mr-1"></i> Video Pembelajaran YouTube
                    </span>
                    <h2 class="font-serif text-2xl sm:text-3xl font-bold text-slate-900 mt-3">Video Edukasi Pergerakan Nasional</h2>
                    <p class="text-sm text-slate-600 mt-1">Pilih salah satu episode video pembelajaran di bawah ini untuk memutar materi sejarah langsung dari YouTube.</p>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                    <!-- Pemutar Video YouTube Utama -->
                    <div class="lg:col-span-2 space-y-4">
                        <div class="relative w-full aspect-video rounded-2xl overflow-hidden bg-slate-950 shadow-lg border border-slate-200">
                            <iframe id="youtube-player" class="w-full h-full" src="https://www.youtube.com/embed/BsncD-RLDJ0" title="Video Pembelajaran Pergerakan Nasional" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                        </div>

                        <!-- Deskripsi Video Aktif -->
                        <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200 flex flex-col sm:flex-row sm:items-center justify-between gap-4">
                            <div>
                                <span id="video-channel" class="text-xs font-bold text-brand-red uppercase tracking-wide">Channel: Octavianus Yonatan (Motion Graphic)</span>
                                <h3 id="video-title" class="font-bold text-lg text-slate-900 mt-0.5">1. Sejarah Organisasi Budi Utomo (1908)</h3>
                                <p id="video-desc" class="text-sm text-slate-600 mt-1.5 leading-relaxed">
                                    Animasi grafis (Motion Graphic) interaktif yang mengupas secara komprehensif latar belakang lahirnya kesadaran nasionalisme modern di Hindia Belanda, peran penting dr. Wahidin Sudirohusodo dengan gerakan Studiefonds-nya, hingga berdirinya Budi Utomo pada 20 Mei 1908 oleh dr. Soetomo dan kawan-kawan mahasiswa STOVIA di Batavia.
                                </p>
                            </div>
                            <a id="youtube-direct-link" href="https://www.youtube.com/watch?v=BsncD-RLDJ0" target="_blank" rel="noopener noreferrer" class="shrink-0 px-4 py-2.5 rounded-xl bg-red-600 hover:bg-red-700 text-white text-xs font-bold shadow-sm transition flex items-center justify-center">
                                <i class="fab fa-youtube mr-1.5 text-sm"></i> Buka di YouTube
                            </a>
                        </div>
                    </div>

                    <!-- Daftar Playlist Video YouTube -->
                    <div class="space-y-3">
                        <h4 class="font-bold text-sm uppercase tracking-wider text-slate-500">Daftar Video Edukasi</h4>
                        
                        <button onclick="selectVideoEpisode(0, this)" class="video-item-btn w-full text-left p-4 rounded-2xl border-2 border-brand-red bg-red-50/50 transition flex items-start space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-brand-red text-white flex items-center justify-center shrink-0 mt-0.5">
                                <i class="fas fa-play text-xs"></i>
                            </div>
                            <div>
                                <span class="text-xs font-bold text-brand-red">Video 01 • 06:58</span>
                                <h5 class="font-bold text-sm text-slate-900">Sejarah Organisasi Budi Utomo</h5>
                                <p class="text-xs text-slate-500 mt-0.5">Motion Graphic Kebangkitan Nasional</p>
                            </div>
                        </button>

                        <button onclick="selectVideoEpisode(1, this)" class="video-item-btn w-full text-left p-4 rounded-2xl border border-slate-200 bg-white hover:bg-slate-50 transition flex items-start space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-slate-200 text-slate-700 flex items-center justify-center shrink-0 mt-0.5">
                                <i class="fas fa-play text-xs"></i>
                            </div>
                            <div>
                                <span class="text-xs font-bold text-slate-500">Video 02 • 26:49</span>
                                <h5 class="font-bold text-sm text-slate-900">Budi Utomo, Sarekat Islam & Indische Partij</h5>
                                <p class="text-xs text-slate-500 mt-0.5">Materi Lengkap Sejarah Kelas XI</p>
                            </div>
                        </button>

                        <button onclick="selectVideoEpisode(2, this)" class="video-item-btn w-full text-left p-4 rounded-2xl border border-slate-200 bg-white hover:bg-slate-50 transition flex items-start space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-slate-200 text-slate-700 flex items-center justify-center shrink-0 mt-0.5">
                                <i class="fas fa-play text-xs"></i>
                            </div>
                            <div>
                                <span class="text-xs font-bold text-slate-500">Video 03 • 12:52</span>
                                <h5 class="font-bold text-sm text-slate-900">Organisasi Pergerakan Hingga Sumpah Pemuda</h5>
                                <p class="text-xs text-slate-500 mt-0.5">Perjalanan Menuju Persatuan 1928</p>
                            </div>
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- 5. SECTION GAME TOKOH & ORGANISASI -->
        <section id="sec-game" class="tab-section hidden space-y-6">
            <div class="bg-white rounded-3xl p-6 sm:p-10 border border-slate-200 shadow-sm">
                <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 border-b border-slate-100 pb-6 mb-6">
                    <div>
                        <span class="text-xs font-bold uppercase tracking-wider text-emerald-700 bg-emerald-50 px-3 py-1 rounded-full">Gamifikasi Sejarah</span>
                        <h2 class="font-serif text-2xl sm:text-3xl font-bold text-slate-900 mt-2">Game Tokoh & Organisasi Pergerakan</h2>
                        <p class="text-sm text-slate-600 mt-1">Buka kartu dan pasangkan setiap <strong>Kartu Tokoh</strong> dengan <strong>Kartu Organisasi</strong> yang didirikan atau dipimpinnya!</p>
                    </div>
                    <!-- Statistik Game -->
                    <div class="flex items-center space-x-3 bg-slate-50 p-3 rounded-2xl border border-slate-200">
                        <div class="text-center px-3">
                            <span class="block text-[11px] font-semibold text-slate-500 uppercase">Langkah</span>
                            <span id="game-moves" class="font-bold text-xl text-slate-900">0</span>
                        </div>
                        <div class="h-8 w-px bg-slate-200"></div>
                        <div class="text-center px-3">
                            <span class="block text-[11px] font-semibold text-slate-500 uppercase">Pasangan</span>
                            <span id="game-matches" class="font-bold text-xl text-emerald-600">0/6</span>
                        </div>
                        <button onclick="initMemoryGame()" class="px-4 py-2.5 bg-brand-red hover:bg-brand-darkred text-white text-xs font-bold rounded-xl shadow transition flex items-center">
                            <i class="fas fa-redo mr-1.5"></i> Acak Ulang
                        </button>
                    </div>
                </div>

                <!-- Legenda Kartu -->
                <div class="flex flex-wrap items-center justify-center gap-4 mb-5 text-xs">
                    <span class="inline-flex items-center px-3 py-1 rounded-full bg-amber-50 text-amber-800 border border-amber-200 font-semibold">
                        <i class="fas fa-user-tie mr-1.5 text-amber-600"></i> Kartu Tokoh Pergerakan
                    </span>
                    <span class="inline-flex items-center px-3 py-1 rounded-full bg-blue-50 text-blue-800 border border-blue-200 font-semibold">
                        <i class="fas fa-landmark mr-1.5 text-blue-600"></i> Kartu Organisasi Pergerakan
                    </span>
                </div>

                <!-- Fakta Sejarah -->
                <div id="game-fact-box" class="hidden mb-6 p-4 rounded-2xl bg-emerald-50 border border-emerald-200 text-emerald-900 flex items-center justify-between">
                    <div class="flex items-center space-x-3">
                        <i class="fas fa-lightbulb text-amber-500 text-xl shrink-0"></i>
                        <p id="game-fact-text" class="text-sm font-medium"></p>
                    </div>
                </div>

                <!-- Grid Kartu Game -->
                <div id="memory-grid" class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-3 sm:gap-4 max-w-4xl mx-auto">
                    <!-- Diisi via JavaScript -->
                </div>

                <!-- Modal Kemenangan Game -->
                <div id="game-win-banner" class="hidden mt-8 p-6 rounded-2xl bg-gradient-to-r from-emerald-600 to-teal-600 text-white text-center space-y-3 shadow-lg">
                    <div class="text-4xl">🏆</div>
                    <h3 class="font-serif text-2xl font-bold">Hebat! Semua Tokoh & Organisasinya Berhasil Dipasangkan!</h3>
                    <p id="game-win-summary" class="text-sm text-emerald-100"></p>
                    <button onclick="initMemoryGame()" class="mt-2 px-6 py-2.5 bg-white text-emerald-700 font-bold rounded-xl shadow hover:bg-emerald-50 transition">
                        Main Lagi
                    </button>
                </div>
            </div>
        </section>

        <!-- 6. SECTION EVALUASI (20 SOAL) -->
        <section id="sec-evaluasi" class="tab-section hidden space-y-8">
            <div class="bg-white rounded-3xl p-6 sm:p-10 border border-slate-200 shadow-sm">
                
                <!-- Layar Pembuka Evaluasi -->
                <div id="quiz-start-screen" class="py-8 sm:py-12 px-4 text-center max-w-2xl mx-auto space-y-6">
                    <div class="w-20 h-20 rounded-3xl bg-purple-100 text-purple-700 flex items-center justify-center text-3xl mx-auto shadow-inner">
                        <i class="fas fa-clipboard-check"></i>
                    </div>
                    <div class="space-y-2">
                        <span class="text-xs font-bold uppercase tracking-wider text-purple-700 bg-purple-50 px-3 py-1 rounded-full">Uji Kompetensi Sejarah</span>
                        <h2 class="font-serif text-2xl sm:text-4xl font-bold text-slate-900">Evaluasi Pergerakan Nasional</h2>
                        <p class="text-sm sm:text-base text-slate-600 leading-relaxed pt-1">
                            Uji pemahamanmu mengenai faktor pendorong, periodisasi strategi perjuangan, tokoh, serta organisasi Pergerakan Nasional Indonesia.
                        </p>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 text-left bg-slate-50 p-5 rounded-2xl border border-slate-200">
                        <div class="flex items-center space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-red-100 text-brand-red flex items-center justify-center shrink-0">
                                <i class="fas fa-list-ol"></i>
                            </div>
                            <div>
                                <span class="block text-xs text-slate-500">Jumlah Soal</span>
                                <strong class="text-sm text-slate-900">20 Pilihan Ganda</strong>
                            </div>
                        </div>
                        <div class="flex items-center space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-amber-100 text-amber-700 flex items-center justify-center shrink-0">
                                <i class="fas fa-award"></i>
                            </div>
                            <div>
                                <span class="block text-xs text-slate-500">Skor Maksimal</span>
                                <strong class="text-sm text-slate-900">100 Poin (5/soal)</strong>
                            </div>
                        </div>
                        <div class="flex items-center space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center shrink-0">
                                <i class="fas fa-book-reader"></i>
                            </div>
                            <div>
                                <span class="block text-xs text-slate-500">Fasilitas</span>
                                <strong class="text-sm text-slate-900">Kunci & Pembahasan</strong>
                            </div>
                        </div>
                    </div>

                    <div class="pt-2">
                        <button onclick="startQuiz()" class="px-8 py-4 bg-brand-red hover:bg-brand-darkred text-white font-bold text-base rounded-2xl shadow-lg hover:shadow-xl transition transform hover:-translate-y-0.5 inline-flex items-center">
                            <i class="fas fa-play-circle mr-2.5 text-lg"></i> Start Evaluasi Sekarang
                        </button>
                    </div>
                </div>

                <!-- Area Soal Evaluasi -->
                <div id="quiz-active-screen" class="hidden">
                    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 border-b border-slate-100 pb-6 mb-6">
                        <div>
                            <span class="text-xs font-bold uppercase tracking-wider text-purple-700 bg-purple-50 px-3 py-1 rounded-full">Uji Kompetensi</span>
                            <h2 class="font-serif text-2xl sm:text-3xl font-bold text-slate-900 mt-2">Evaluasi Pembelajaran (20 Soal)</h2>
                            <p class="text-sm text-slate-600 mt-1">Pilih satu jawaban yang paling tepat pada setiap soal, lalu klik tombol <strong>Selesai & Lihat Nilai</strong> di bagian bawah.</p>
                        </div>
                        <div class="bg-slate-100 px-4 py-2.5 rounded-xl text-sm font-semibold text-slate-700 shrink-0">
                            Terjawab: <span id="quiz-answered-count" class="text-brand-red font-bold">0</span> / 20
                        </div>
                    </div>

                    <!-- Hasil Skor Evaluasi -->
                    <div id="quiz-result-box" class="hidden mb-8 p-6 sm:p-8 rounded-2xl bg-gradient-to-br from-slate-900 to-brand-darkred text-white shadow-xl">
                        <div class="flex flex-col md:flex-row items-center justify-between gap-6">
                            <div class="space-y-2 text-center md:text-left">
                                <span class="px-3 py-1 rounded-full bg-amber-400/20 text-amber-300 text-xs font-bold">Hasil Evaluasi EsHist</span>
                                <h3 id="quiz-predicate" class="font-serif text-2xl sm:text-3xl font-bold">Sangat Memuaskan!</h3>
                                <p id="quiz-feedback" class="text-sm text-slate-200 max-w-xl"></p>
                            </div>
                            <div class="flex items-center space-x-6 bg-white/10 p-5 rounded-2xl backdrop-blur-sm border border-white/15">
                                <div class="text-center">
                                    <span class="block text-xs text-slate-300">Skor Akhir</span>
                                    <span id="quiz-final-score" class="text-4xl font-black text-amber-400">100</span>
                                </div>
                                <div class="h-12 w-px bg-white/20"></div>
                                <div class="text-sm space-y-1">
                                    <p class="text-emerald-300 font-semibold"><i class="fas fa-check-circle mr-1"></i> Benar: <span id="quiz-correct-count">0</span></p>
                                    <p class="text-red-300 font-semibold"><i class="fas fa-times-circle mr-1"></i> Salah: <span id="quiz-wrong-count">0</span></p>
                                </div>
                            </div>
                        </div>
                        <div class="mt-6 pt-4 border-t border-white/15 flex flex-wrap gap-3">
                            <button onclick="resetQuiz()" class="px-5 py-2.5 bg-white text-slate-900 font-bold text-sm rounded-xl hover:bg-slate-100 transition">
                                <i class="fas fa-redo mr-1.5"></i> Kerjakan Ulang Evaluasi
                            </button>
                            <span class="text-xs text-slate-300 self-center">Gulir ke bawah untuk melihat kunci jawaban & pembahasan setiap nomor.</span>
                        </div>
                    </div>

                    <!-- Container 20 Soal -->
                    <div id="quiz-questions-container" class="space-y-6">
                        <!-- Diisi via JavaScript -->
                    </div>

                    <!-- Tombol Submit -->
                    <div class="mt-8 pt-6 border-t border-slate-200 flex flex-col sm:flex-row items-center justify-between gap-4">
                        <p id="quiz-warning-msg" class="text-sm text-red-600 font-medium hidden">
                            <i class="fas fa-exclamation-triangle mr-1"></i> Harap jawab semua 20 soal terlebih dahulu sebelum melihat nilai!
                        </p>
                        <button id="submit-quiz-btn" onclick="submitQuiz()" class="w-full sm:w-auto ml-auto px-8 py-4 bg-brand-red hover:bg-brand-darkred text-white font-bold rounded-2xl shadow-lg transition transform hover:-translate-y-0.5 flex items-center justify-center">
                            <i class="fas fa-paper-plane mr-2"></i> Selesai & Lihat Nilai
                        </button>
                    </div>
                </div>

            </div>
        </section>

        <!-- 7. SECTION DAFTAR PUSTAKA -->
        <section id="sec-pustaka" class="tab-section hidden space-y-8">
            <div class="bg-white rounded-3xl p-6 sm:p-10 border border-slate-200 shadow-sm">
                <div class="border-b border-slate-100 pb-6 mb-6">
                    <span class="text-xs font-bold uppercase tracking-wider text-slate-700 bg-slate-100 px-3 py-1 rounded-full">Referensi Akademik</span>
                    <h2 class="font-serif text-2xl sm:text-3xl font-bold text-slate-900 mt-3">Daftar Pustaka</h2>
                    <p class="text-sm text-slate-600 mt-1">Sumber literatur sejarah dan buku teks resmi yang menjadi rujukan dalam pengembangan konten EsHist.</p>
                </div>

                <div class="space-y-4 text-sm sm:text-base text-slate-700">
                    <div class="p-4 rounded-2xl bg-slate-50 border border-slate-200/80 hover:border-slate-300 transition pl-8 -indent-4">
                        Abdullah, Taufik & Lapian, A.B. (Ed.). (2012). <em>Indonesia Dalam Arus Sejarah Jilid 5: Masa Pergerakan Kebangsaan</em>. Jakarta: Ichtiar Baru van Hoeve & Kementerian Pendidikan dan Kebudayaan RI.
                    </div>
                    <div class="p-4 rounded-2xl bg-slate-50 border border-slate-200/80 hover:border-slate-300 transition pl-8 -indent-4">
                        Kartodirdjo, Sartono. (1999). <em>Pengantar Sejarah Indonesia Baru: Sejarah Pergerakan Nasional dari Kolonialisme sampai Nasionalisme (Jilid 2)</em>. Jakarta: Gramedia Pustaka Utama.
                    </div>
                    <div class="p-4 rounded-2xl bg-slate-50 border border-slate-200/80 hover:border-slate-300 transition pl-8 -indent-4">
                        Kementerian Pendidikan, Kebudayaan, Riset, dan Teknologi. (2021). <em>Sejarah untuk SMA/SMK Kelas XI</em>. Jakarta: Pusat Kurikulum dan Perbukuan, Badan Penelitian dan Pengembangan dan Perbukuan.
                    </div>
                    <div class="p-4 rounded-2xl bg-slate-50 border border-slate-200/80 hover:border-slate-300 transition pl-8 -indent-4">
                        Nagazumi, Akira. (1989). <em>Bangkitnya Nasionalisme Indonesia: Budi Utomo 1908-1918</em>. Jakarta: Pustaka Utama Grafiti.
                    </div>
                    <div class="p-4 rounded-2xl bg-slate-50 border border-slate-200/80 hover:border-slate-300 transition pl-8 -indent-4">
                        Poesponegoro, Marwati Djoened & Notosusanto, Nugroho. (2008). <em>Sejarah Nasional Indonesia Jilid V: Zaman Kebangkitan Nasional dan Masa Hindia Belanda</em>. Jakarta: Balai Pustaka.
                    </div>
                    <div class="p-4 rounded-2xl bg-slate-50 border border-slate-200/80 hover:border-slate-300 transition pl-8 -indent-4">
                        Ricklefs, M.C. (2008). <em>Sejarah Indonesia Modern 1200–2008</em>. Jakarta: Serambi Ilmu Semesta.
                    </div>
                    <div class="p-4 rounded-2xl bg-slate-50 border border-slate-200/80 hover:border-slate-300 transition pl-8 -indent-4">
                        Suryanegara, Ahmad Mansur. (2014). <em>Api Sejarah 1: Mahakarya Perjuangan Ulama dan Santri dalam Menegakkan Negara Kesatuan Republik Indonesia</em>. Bandung: Surya Dinasti.
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- FOOTER -->
    <footer class="bg-slate-900 text-slate-400 py-8 border-t border-slate-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row items-center justify-between gap-4 text-xs sm:text-sm">
            <div class="flex items-center space-x-2">
                <span class="font-serif font-bold text-white text-base">Es<span class="text-red-500">Hist</span></span>
                <span>• Media Pembelajaran Interaktif Sejarah Indonesia</span>
            </div>
            <p>© 2026 EsHist Edukasi. Jas Merah — Jangan Sekali-kali Meninggalkan Sejarah.</p>
        </div>
    </footer>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        // ==========================================
        // 1. NAVIGASI TAB & MENU MOBILE DENGAN TRANSISI
        // ==========================================
        function switchTab(tabName) {
            // Sembunyikan semua section
            document.querySelectorAll('.tab-section').forEach(sec => {
                sec.classList.add('hidden');
                sec.style.opacity = '0';
            });
            
            // Tampilkan section terpilih
            const targetSec = document.getElementById('sec-' + tabName);
            if (targetSec) {
                targetSec.classList.remove('hidden');
                void targetSec.offsetWidth;
                targetSec.style.opacity = '1';
            }

            // Update gaya tombol navigasi desktop
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('text-brand-red', 'bg-red-50', 'font-semibold');
                btn.classList.add('text-slate-600', 'font-medium');
            });
            const activeBtn = document.getElementById('nav-' + tabName);
            if (activeBtn) {
                activeBtn.classList.remove('text-slate-600', 'font-medium');
                activeBtn.classList.add('text-brand-red', 'bg-red-50', 'font-semibold');
            }

            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('hidden');
        }

        document.getElementById('mobile-menu-btn').addEventListener('click', toggleMobileMenu);

        // ==========================================
        // 2. DATA & RENDER ORGANISASI PERGERAKAN NASIONAL
        // ==========================================
        const organizationsData = [
            {
                name: "Budi Utomo (BU)",
                date: "20 Mei 1908",
                category: "awal",
                badge: "Masa Awal • Kooperatif",
                founders: "dr. Soetomo, dr. Wahidin Sudirohusodo, Gunawan Mangunkusumo, Soeradji",
                asas: "Sosial, budaya, dan pendidikan untuk kemajuan masyarakat Jawa dan Madura.",
                detail: "Organisasi modern pertama di Indonesia yang didirikan oleh para pelajar sekolah dokter STOVIA di Batavia. Gagasan awalnya dicetuskan oleh dr. Wahidin Sudirohusodo yang berkeliling Jawa menggalang dana pendidikan (<em>Studiefonds</em>). Pada Kongres Pertama di Yogyakarta (Oktober 1908), R.T. Tirtokusumo terpilih sebagai ketua umum, sedangkan dr. Soetomo memimpin pengurus pusat di Batavia."
            },
            {
                name: "Sarekat Islam (SI)",
                date: "1911 (SDI) / 1912 (SI)",
                category: "awal",
                badge: "Masa Awal • Ekonomi & Massa",
                founders: "H. Samanhudi, H.O.S. Tjokroaminoto, H. Agus Salim, Abdul Muis",
                asas: "Persaudaraan umat Islam, penguatan ekonomi pribumi, dan kemajuan rakyat.",
                detail: "Berawal dari Sarekat Dagang Islam (SDI) yang didirikan H. Samanhudi di Surakarta untuk melindungi pedagang batik pribumi dari monopoli pedagang asing. Tahun 1912, di bawah H.O.S. Tjokroaminoto, nama diubah menjadi Sarekat Islam agar keanggotaannya meluas ke seluruh lapisan masyarakat dan menjadi organisasi massa pertama dengan ratusan ribu anggota."
            },
            {
                name: "Indische Partij (IP)",
                date: "25 Desember 1912",
                category: "radikal",
                badge: "Masa Radikal • Non-Kooperatif",
                founders: "Tiga Serangkai (E.F.E. Douwes Dekker, dr. Cipto Mangunkusumo, Suwardi Suryaningrat)",
                asas: "Nasionalisme Hindia (<em>Indische Nationalisme</em>) tanpa membedakan ras, suku, dan agama.",
                detail: "Organisasi politik murni pertama di Hindia Belanda yang secara terang-terangan menuntut kemerdekaan penuh dengan semboyan <em>'Indie los van Holland'</em> (Hindia bebas dari Belanda) dan <em>'Indie voor Indiers'</em>. Karena dianggap berbahaya dan menolak status badan hukum, pemerintah kolonial membubarkan IP pada Maret 1913 dan mengasingkan Tiga Serangkai ke Belanda."
            },
            {
                name: "Muhammadiyah",
                date: "18 November 1912",
                category: "awal",
                badge: "Sosial • Keagamaan & Pendidikan",
                founders: "K.H. Ahmad Dahlan",
                asas: "Islam berlandaskan Al-Qur'an dan Sunnah dengan semangat pembaruan (tajdid).",
                detail: "Didirikan di Kampung Kauman, Yogyakarta, sebagai gerakan pembaruan Islam modern. Muhammadiyah menggabungkan pendidikan agama dengan ilmu pengetahuan umum, mendirikan sekolah-sekolah modern (HIS met de Qur'an), rumah sakit (PKU), panti asuhan, serta organisasi perempuan Aisyiyah (1917)."
            },
            {
                name: "Nahdlatul Ulama (NU)",
                date: "31 Januari 1926",
                category: "awal",
                badge: "Keagamaan • Kebangsaan & Pesantren",
                founders: "K.H. Hasyim Asy'ari, K.H. Wahab Chasbullah, K.H. Bisri Syansuri",
                asas: "Islam Ahlussunnah wal Jama'ah dengan jaringan ulama dan pesantren Nusantara.",
                detail: "Didirikan di Surabaya sebagai wadah persatuan para ulama pesantren untuk menjaga tradisi keislaman, mengembangkan pendidikan pesantren, serta memperkuat solidaritas ekonomi dan kebangsaan umat di tengah tekanan kolonialisme Belanda."
            },
            {
                name: "Taman Siswa",
                date: "3 Juli 1922",
                category: "pemuda",
                badge: "Pendidikan Nasional • Kemandirian",
                founders: "Ki Hajar Dewantara (Suwardi Suryaningrat)",
                asas: "Pendidikan merdeka berakar pada kebudayaan bangsa sendiri (<em>Tut Wuri Handayani</em>).",
                detail: "Didirikan di Yogyakarta sebagai perlawanan kultural terhadap sistem pendidikan kolonial yang diskriminatif. Dengan semboyan <em>Ing Ngarsa Sung Tuladha, Ing Madya Mangun Karsa, Tut Wuri Handayani</em>, Taman Siswa menanamkan rasa cinta tanah air dan keberanian melawan Ordonansi Sekolah Liar (1932)."
            },
            {
                name: "Perhimpunan Indonesia (PI)",
                date: "1908 (IV) / 1925 (PI)",
                category: "radikal",
                badge: "Masa Radikal • Mahasiswa di Belanda",
                founders: "Mohammad Hatta, Nazir Pamuntjak, Achmad Soebardjo, Ali Sastroamidjojo, Iwa Kusumasumantri",
                asas: "Persatuan nasional, solidaritas, non-kooperasi, dan swadaya (<em>self-help</em>).",
                detail: "Organisasi mahasiswa Indonesia di negeri Belanda (semula bernama <em>Indische Vereeniging</em>). PI menjadi pelopor penggunaan istilah 'Indonesia' sebagai identitas nasional yang merdeka dan menyuarakan hak kemerdekaan Indonesia di forum internasional melalui majalah <em>Indonesia Merdeka</em>."
            },
            {
                name: "Partai Nasional Indonesia (PNI)",
                date: "4 Juli 1927",
                category: "radikal",
                badge: "Masa Radikal • Marhaenisme",
                founders: "Ir. Soekarno, dr. Cipto Mangunkusumo, Mr. Sartono, Mr. Iskaq Tjokroadisuryo",
                asas: "Marhaenisme (sosio-nasionalisme dan sosio-demokrasi).",
                detail: "Didirikan di Bandung untuk mencapai Indonesia Merdeka melalui strategi non-kooperatif dan mobilisasi massa. Kepopuleran PNI membuat Belanda menangkap Ir. Soekarno pada Desember 1929. Di pengadilan Landraad Bandung, Soekarno membacakan pleidoi legendaris berjudul <em>'Indonesia Menggugat'</em>."
            },
            {
                name: "Perhimpunan Pelajar-Pelajar Indonesia (PPPI)",
                date: "September 1926",
                category: "pemuda",
                badge: "Organisasi Pemuda • Persatuan",
                founders: "Soegondo Djojopoespito, Sigit, Djoko Marsaid, Mohammad Yamin",
                asas: "Persatuan pemuda dan pelajar seluruh Indonesia di atas kepentingan kedaerahan.",
                detail: "Wadah mahasiswa dari berbagai perguruan tinggi di Batavia dan Bandung yang menjembatani fusi organisasi pemuda daerah (Jong Java, Jong Sumatranen Bond, Jong Celebes, Jong Ambon, dll). PPPI memprakarsai Kongres Pemuda II tanggal 27–28 Oktober 1928 yang melahirkan ikrar Sumpah Pemuda."
            },
            {
                name: "Gabungan Politik Indonesia (GAPI)",
                date: "21 Mei 1939",
                category: "moderat",
                badge: "Masa Moderat • Kooperatif Taktis",
                founders: "Mohammad Husni Thamrin, Amir Sjarifuddin, Abikusno Tjokrosujoso",
                asas: "Hak menentukan nasib sendiri, persatuan nasional, dan demokrasi parlementer.",
                detail: "Federasi dari berbagai partai politik nasionalis (Parindra, Gerindo, PSII, Pasundan, dll) yang dibentuk menjelang Perang Dunia II. GAPI melancarkan aksi besar dengan semboyan <em>'Indonesia Berparlemen'</em>, menuntut pembentukan parlemen sejati bagi Indonesia."
            }
        ];

        function renderOrganizations(filter = 'semua') {
            const container = document.getElementById('org-container');
            container.innerHTML = '';

            const filtered = filter === 'semua' 
                ? organizationsData 
                : organizationsData.filter(org => org.category === filter);

            filtered.forEach(org => {
                const card = `
                    <div class="p-6 rounded-2xl bg-slate-50 border border-slate-200 hover:border-brand-red/50 hover:bg-white hover:shadow-md transition flex flex-col justify-between">
                        <div>
                            <div class="flex flex-wrap items-center justify-between gap-2 mb-3">
                                <span class="text-xs font-bold px-3 py-1 rounded-full bg-red-100 text-brand-darkred">${org.badge}</span>
                                <span class="text-xs font-semibold text-slate-500"><i class="far fa-calendar-alt mr-1"></i> ${org.date}</span>
                            </div>
                            <h3 class="font-serif text-xl font-bold text-slate-900 mb-2">${org.name}</h3>
                            <div class="mb-3 px-3 py-2 rounded-xl bg-amber-50/80 border border-amber-200/70 text-xs text-amber-950">
                                <strong>Asas & Haluan:</strong> ${org.asas}
                            </div>
                            <p class="text-sm text-slate-600 leading-relaxed mb-4">${org.detail}</p>
                        </div>
                        <div class="pt-3 border-t border-slate-200/80 text-xs text-slate-700">
                            <strong class="text-slate-900"><i class="fas fa-users mr-1 text-brand-red"></i> Tokoh Pendiri/Penggerak:</strong> ${org.founders}
                        </div>
                    </div>
                `;
                container.innerHTML += card;
            });
        }

        function filterOrg(category, btnEl) {
            document.querySelectorAll('.org-filter-btn').forEach(btn => {
                btn.classList.remove('bg-brand-red', 'text-white', 'font-bold');
                btn.classList.add('bg-slate-100', 'text-slate-600', 'font-semibold');
            });
            if (btnEl) {
                btnEl.classList.remove('bg-slate-100', 'text-slate-600', 'font-semibold');
                btnEl.classList.add('bg-brand-red', 'text-white', 'font-bold');
            }
            renderOrganizations(category);
        }

        // ==========================================
        // 3. VIDEO EDUKASI YOUTUBE
        // ==========================================
        const videoEpisodes = [
            {
                youtubeId: "BsncD-RLDJ0",
                channel: "Channel: Octavianus Yonatan (Motion Graphic)",
                title: "1. Sejarah Organisasi Budi Utomo (1908)",
                desc: "Animasi grafis (Motion Graphic) interaktif yang mengupas secara komprehensif latar belakang lahirnya kesadaran nasionalisme modern di Hindia Belanda, peran penting dr. Wahidin Sudirohusodo dengan gerakan Studiefonds-nya, hingga berdirinya Budi Utomo pada 20 Mei 1908 oleh dr. Soetomo dan kawan-kawan mahasiswa STOVIA di Batavia."
            },
            {
                youtubeId: "BGMCaCwEdTE",
                channel: "Channel: Portal Sekolah",
                title: "2. Organisasi Pergerakan: Budi Utomo, Sarekat Islam & Indische Partij",
                desc: "Video pembelajaran mendalam untuk kelas sejarah SMA/SMK yang mengulas secara sistematis perkembangan awal pergerakan nasional, dinamika ekonomi kerakyatan Sarekat Islam di bawah H. Samanhudi dan H.O.S. Tjokroaminoto, serta radikalisme politik Indische Partij yang dipelopori oleh Tiga Serangkai."
            },
            {
                youtubeId: "FKxBksbWwHg",
                channel: "Channel: Viva Historia",
                title: "3. Organisasi Pergerakan Nasional Hingga Sumpah Pemuda",
                desc: "Rangkuman visual perjalanan pergerakan nasional Indonesia dari fase pembentukan, fase radikal dan non-kooperatif, hingga kristalisasi persatuan pemuda dari berbagai daerah dalam Kongres Pemuda II yang melahirkan ikrar Sumpah Pemuda pada 28 Oktober 1928."
            }
        ];

        function selectVideoEpisode(epIndex, btnElement) {
            const ep = videoEpisodes[epIndex];
            if (!ep) return;

            document.getElementById('youtube-player').src = `https://www.youtube.com/embed/${ep.youtubeId}?autoplay=1`;
            document.getElementById('youtube-direct-link').href = `https://www.youtube.com/watch?v=${ep.youtubeId}`;
            document.getElementById('video-channel').textContent = ep.channel;
            document.getElementById('video-title').textContent = ep.title;
            document.getElementById('video-desc').textContent = ep.desc;

            document.querySelectorAll('.video-item-btn').forEach(btn => {
                btn.classList.remove('border-2', 'border-brand-red', 'bg-red-50/50');
                btn.classList.add('border', 'border-slate-200', 'bg-white');
                btn.querySelector('div').classList.remove('bg-brand-red', 'text-white');
                btn.querySelector('div').classList.add('bg-slate-200', 'text-slate-700');
            });

            if (btnElement) {
                btnElement.classList.remove('border', 'border-slate-200', 'bg-white');
                btnElement.classList.add('border-2', 'border-brand-red', 'bg-red-50/50');
                btnElement.querySelector('div').classList.remove('bg-slate-200', 'text-slate-700');
                btnElement.querySelector('div').classList.add('bg-brand-red', 'text-white');
            }
        }

        // ==========================================
        // 4. GAME MENCOCOKKAN TOKOH DENGAN ORGANISASINYA
        // ==========================================
        const tokohOrganisasiPairs = [
            {
                pairId: 'bu',
                tokohName: 'dr. Soetomo',
                tokohSub: 'Mahasiswa STOVIA',
                orgName: 'Budi Utomo (1908)',
                orgSub: 'Organisasi Modern Pertama',
                tokohSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#FEF3C7"/><circle cx="50" cy="38" r="16" fill="#78350F"/><path d="M24 82 C24 62, 76 62, 76 82" fill="#92400E"/><rect x="37" y="34" width="10" height="6" rx="2" fill="none" stroke="#FFF" stroke-width="2"/><rect x="53" y="34" width="10" height="6" rx="2" fill="none" stroke="#FFF" stroke-width="2"/><line x1="47" y1="37" x2="53" y2="37" stroke="#FFF" stroke-width="2"/></svg>`,
                orgSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#DBEAFE"/><polygon points="50,20 22,38 78,38" fill="#1E3A8A"/><rect x="28" y="40" width="8" height="28" fill="#1D4ED8"/><rect x="46" y="40" width="8" height="28" fill="#1D4ED8"/><rect x="64" y="40" width="8" height="28" fill="#1D4ED8"/><rect x="22" y="70" width="56" height="8" rx="2" fill="#1E3A8A"/></svg>`,
                fact: 'dr. Soetomo memimpin para pelajar STOVIA mendirikan organisasi modern pertama, Budi Utomo, pada tanggal 20 Mei 1908.'
            },
            {
                pairId: 'si',
                tokohName: 'H. Samanhudi',
                tokohSub: 'Pengusaha Batik Solo',
                orgName: 'Sarekat Dagang Islam',
                orgSub: 'Didirikan Tahun 1911',
                tokohSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#FEF3C7"/><path d="M32 28 L68 28 L64 16 L36 16 Z" fill="#1E293B"/><circle cx="50" cy="42" r="15" fill="#92400E"/><path d="M25 84 C25 64, 75 64, 75 84" fill="#B45309"/></svg>`,
                orgSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#DBEAFE"/><path d="M55 24 A24 24 0 1 0 74 62 A18 18 0 1 1 55 24 Z" fill="#047857"/><polygon points="66,30 69,38 77,38 71,43 73,51 66,46 59,51 61,43 55,38 63,38" fill="#D97706"/></svg>`,
                fact: 'H. Samanhudi mendirikan Sarekat Dagang Islam (SDI) di Solo tahun 1911 untuk memperkuat persatuan dan ekonomi pedagang pribumi.'
            },
            {
                pairId: 'ip',
                tokohName: 'Douwes Dekker',
                tokohSub: 'Tokoh Tiga Serangkai',
                orgName: 'Indische Partij (1912)',
                orgSub: 'Partai Politik Pertama',
                tokohSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#FEF3C7"/><circle cx="50" cy="39" r="15" fill="#7C2D12"/><path d="M25 84 C25 64, 75 64, 75 84" fill="#9A3412"/><path d="M41 45 Q50 51 59 45" stroke="#FFF" stroke-width="2.5" fill="none"/></svg>`,
                orgSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#DBEAFE"/><circle cx="50" cy="50" r="24" fill="none" stroke="#991B1B" stroke-width="5"/><polygon points="50,32 55,45 69,45 58,53 62,66 50,58 38,66 42,53 31,45 45,45" fill="#991B1B"/></svg>`,
                fact: 'E.F.E. Douwes Dekker bersama dr. Cipto Mangunkusumo dan Suwardi Suryaningrat mendirikan Indische Partij pada 25 Desember 1912.'
            },
            {
                pairId: 'muh',
                tokohName: 'K.H. Ahmad Dahlan',
                tokohSub: 'Ulama Pembaru Yogyakarta',
                orgName: 'Muhammadiyah (1912)',
                orgSub: 'Gerakan Pendidikan & Sosial',
                tokohSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#FEF3C7"/><path d="M30 28 Q50 14 70 28 Z" fill="#F8FAFC" stroke="#94A3B8" stroke-width="2"/><circle cx="50" cy="42" r="15" fill="#78350F"/><path d="M25 84 C25 64, 75 64, 75 84" fill="#065F46"/></svg>`,
                orgSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#DBEAFE"/><circle cx="50" cy="50" r="16" fill="#059669"/><g stroke="#059669" stroke-width="4" stroke-linecap="round"><line x1="50" y1="20" x2="50" y2="28"/><line x1="50" y1="72" x2="50" y2="80"/><line x1="20" y1="50" x2="28" y2="50"/><line x1="72" y1="50" x2="80" y2="50"/><line x1="29" y1="29" x2="35" y2="35"/><line x1="65" y1="65" x2="71" y2="71"/><line x1="71" y1="29" x2="65" y2="35"/><line x1="35" y1="65" x2="29" y2="71"/></g></svg>`,
                fact: 'K.H. Ahmad Dahlan mendirikan Muhammadiyah di Yogyakarta (18 November 1912) yang memadukan dakwah Islam dengan pendidikan modern.'
            },
            {
                pairId: 'pi',
                tokohName: 'Mohammad Hatta',
                tokohSub: 'Mahasiswa di Belanda',
                orgName: 'Perhimpunan Indonesia',
                orgSub: 'Pelopor Nama "Indonesia"',
                tokohSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#FEF3C7"/><circle cx="50" cy="39" r="15" fill="#1E293B"/><circle cx="43" cy="38" r="5" fill="none" stroke="#FFF" stroke-width="2"/><circle cx="57" cy="38" r="5" fill="none" stroke="#FFF" stroke-width="2"/><path d="M25 84 C25 64, 75 64, 75 84" fill="#334155"/></svg>`,
                orgSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#DBEAFE"/><circle cx="50" cy="50" r="24" fill="none" stroke="#1D4ED8" stroke-width="3"/><ellipse cx="50" cy="50" rx="11" ry="24" fill="none" stroke="#1D4ED8" stroke-width="2.5"/><line x1="26" y1="50" x2="74" y2="50" stroke="#1D4ED8" stroke-width="2.5"/></svg>`,
                fact: 'Mohammad Hatta memimpin Perhimpunan Indonesia (PI) di Belanda dan menyuarakan kemerdekaan Indonesia di forum internasional.'
            },
            {
                pairId: 'pni',
                tokohName: 'Ir. Soekarno',
                tokohSub: 'Penggagas Marhaenisme',
                orgName: 'Partai Nasional Indonesia',
                orgSub: 'PNI (4 Juli 1927)',
                tokohSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#FEF3C7"/><rect x="33" y="17" width="34" height="11" rx="2" fill="#0F172A"/><circle cx="50" cy="42" r="15" fill="#7F1D1D"/><path d="M25 84 C25 64, 75 64, 75 84" fill="#991B1B"/></svg>`,
                orgSvg: `<svg viewBox="0 0 100 100" class="w-14 h-14 mx-auto"><circle cx="50" cy="50" r="45" fill="#DBEAFE"/><path d="M30 70 L30 30 L70 30 L70 50 L30 50" fill="none" stroke="#991B1B" stroke-width="5" stroke-linejoin="round"/><rect x="30" y="30" width="40" height="10" fill="#DC2626"/><rect x="30" y="40" width="40" height="10" fill="#FFFFFF"/></svg>`,
                fact: 'Ir. Soekarno mendirikan Partai Nasional Indonesia (PNI) pada 4 Juli 1927 dengan strategi non-kooperatif dan asas Marhaenisme.'
            }
        ];

        let cards = [];
        let flippedCards = [];
        let matchedPairs = 0;
        let moves = 0;
        let lockBoard = false;

        function initMemoryGame() {
            const grid = document.getElementById('memory-grid');
            if (!grid) return;
            grid.innerHTML = '';
            document.getElementById('game-win-banner').classList.add('hidden');
            document.getElementById('game-fact-box').classList.add('hidden');

            flippedCards = [];
            matchedPairs = 0;
            moves = 0;
            lockBoard = false;

            document.getElementById('game-moves').textContent = '0';
            document.getElementById('game-matches').textContent = `0/${tokohOrganisasiPairs.length}`;

            const deck = [];
            tokohOrganisasiPairs.forEach(pair => {
                deck.push({
                    pairId: pair.pairId,
                    type: 'TOKOH',
                    title: pair.tokohName,
                    subtitle: pair.tokohSub,
                    svg: pair.tokohSvg,
                    fact: pair.fact
                });
                deck.push({
                    pairId: pair.pairId,
                    type: 'ORGANISASI',
                    title: pair.orgName,
                    subtitle: pair.orgSub,
                    svg: pair.orgSvg,
                    fact: pair.fact
                });
            });

            cards = deck.sort(() => Math.random() - 0.5);

            cards.forEach((card, index) => {
                const isTokoh = card.type === 'TOKOH';
                const badgeClass = isTokoh 
                    ? 'bg-amber-100 text-amber-800 border-amber-200' 
                    : 'bg-blue-100 text-blue-800 border-blue-200';
                const cardBorderClass = isTokoh ? 'border-amber-200' : 'border-blue-200';

                const cardEl = document.createElement('div');
                cardEl.className = 'perspective-1000 h-40 sm:h-48 cursor-pointer select-none';
                cardEl.dataset.pairId = card.pairId;
                cardEl.dataset.type = card.type;
                cardEl.dataset.index = index;

                cardEl.innerHTML = `
                    <div class="card-inner relative w-full h-full transition-transform duration-500 transform-style-3d">
                        <div class="absolute inset-0 backface-hidden rounded-2xl bg-gradient-to-br from-brand-red to-brand-darkred border-2 border-red-300/30 shadow-md flex flex-col items-center justify-center text-white p-3">
                            <div class="w-10 h-10 rounded-full bg-white/15 flex items-center justify-center mb-2">
                                <i class="fas fa-question text-amber-300 text-base"></i>
                            </div>
                            <span class="font-serif font-bold text-sm tracking-wide">EsHist</span>
                            <span class="text-[10px] text-red-200 mt-0.5">Buka Kartu</span>
                        </div>
                        <div class="face-back absolute inset-0 backface-hidden rotate-y-180 rounded-2xl bg-white border-2 ${cardBorderClass} shadow-md flex flex-col items-center justify-between p-2.5 text-center">
                            <span class="text-[9px] font-extrabold tracking-wider px-2 py-0.5 rounded-full border ${badgeClass}">
                                ${card.type}
                            </span>
                            ${card.svg}
                            <div>
                                <h4 class="font-bold text-xs sm:text-sm text-slate-900 leading-tight">${card.title}</h4>
                                <span class="block text-[10px] text-slate-500 mt-0.5 line-clamp-1">${card.subtitle}</span>
                            </div>
                        </div>
                    </div>
                `;

                cardEl.addEventListener('click', () => flipCard(cardEl, card));
                grid.appendChild(cardEl);
            });
        }

        function flipCard(cardEl, cardData) {
            if (lockBoard) return;
            const inner = cardEl.querySelector('.card-inner');
            if (inner.classList.contains('card-flipped')) return;

            inner.classList.add('card-flipped');
            flippedCards.push({ el: cardEl, data: cardData });

            if (flippedCards.length === 2) {
                moves++;
                document.getElementById('game-moves').textContent = moves;
                checkForMatch();
            }
        }

        function checkForMatch() {
            lockBoard = true;
            const [first, second] = flippedCards;

            if (first.data.pairId === second.data.pairId && first.data.type !== second.data.type) {
                matchedPairs++;
                document.getElementById('game-matches').textContent = `${matchedPairs}/${tokohOrganisasiPairs.length}`;
                
                [first, second].forEach(item => {
                    const backFace = item.el.querySelector('.face-back');
                    backFace.classList.remove('border-amber-200', 'border-blue-200', 'bg-white');
                    backFace.classList.add('border-emerald-500', 'bg-emerald-50/40');
                });

                const factBox = document.getElementById('game-fact-box');
                document.getElementById('game-fact-text').innerHTML = `<strong>Pasangan Tepat!</strong> ${first.data.fact}`;
                factBox.classList.remove('hidden');

                flippedCards = [];
                lockBoard = false;

                if (matchedPairs === tokohOrganisasiPairs.length) {
                    setTimeout(() => {
                        const winBanner = document.getElementById('game-win-banner');
                        document.getElementById('game-win-summary').textContent = `Kamu berhasil memasangkan seluruh 6 Tokoh dengan Organisasinya dalam ${moves} langkah!`;
                        winBanner.classList.remove('hidden');
                    }, 500);
                }
            } else {
                setTimeout(() => {
                    first.el.querySelector('.card-inner').classList.remove('card-flipped');
                    second.el.querySelector('.card-inner').classList.remove('card-flipped');
                    flippedCards = [];
                    lockBoard = false;
                }, 1000);
            }
        }

        // ==========================================
        // 5. EVALUASI 20 SOAL PILIHAN GANDA
        // ==========================================
        const quizQuestions = [
            {
                q: "Perubahan strategi perjuangan bangsa Indonesia setelah tahun 1908 ditandai dengan ciri utama berupa...",
                options: [
                    "Perlawanan fisik bersenjata yang dipimpin oleh raja-raja daerah",
                    "Perjuangan melalui organisasi modern, diplomasi, pendidikan, dan bersifat nasional",
                    "Ketergantungan pada bantuan militer dari negara-negara Eropa lainnya",
                    "Penolakan total terhadap seluruh bentuk pendidikan Barat di Hindia Belanda"
                ],
                answer: 1,
                explanation: "Sejak 1908 (berdirinya Budi Utomo), perjuangan bangsa Indonesia beralih dari perlawanan fisik kedaerahan menuju organisasi modern yang terstruktur dan bervisi nasional."
            },
            {
                q: "Salah satu faktor internal terpenting yang memicu lahirnya kesadaran nasionalisme di Indonesia adalah...",
                options: [
                    "Kemenangan Jepang atas Rusia pada tahun 1905",
                    "Keberhasilan revolusi Tiongkok di bawah Sun Yat Sen",
                    "Munculnya golongan terpelajar pribumi akibat Politik Etis",
                    "Terjadinya Perang Dunia I di kawasan Eropa"
                ],
                answer: 2,
                explanation: "Politik Etis (terutama bidang edukasi) melahirkan kaum terpelajar pribumi yang sadar akan nasib bangsanya dan mempelopori organisasi pergerakan."
            },
            {
                q: "Kemenangan Jepang atas Rusia pada tahun 1905 memberikan dampak psikologis besar bagi bangsa-bangsa di Asia, termasuk Indonesia, karena...",
                options: [
                    "Jepang memberikan bantuan senjata langsung kepada pejuang Indonesia",
                    "Membuktikan bahwa bangsa Asia mampu mengalahkan bangsa Eropa (kulit putih)",
                    "Rusia menyerahkan wilayah jajahan di Asia Tenggara kepada Jepang",
                    "Belanda langsung menarik pasukannya dari Hindia Belanda"
                ],
                answer: 1,
                explanation: "Kemenangan Jepang atas Rusia meruntuhkan mitos superioritas bangsa Eropa dan membangkitkan rasa percaya diri bangsa-bangsa Asia."
            },
            {
                q: "Organisasi modern pertama yang berdiri pada tanggal 20 Mei 1908 atas gagasan dr. Wahidin Sudirohusodo dan dipimpin dr. Soetomo adalah...",
                options: [
                    "Sarekat Dagang Islam",
                    "Indische Partij",
                    "Budi Utomo",
                    "Perhimpunan Indonesia"
                ],
                answer: 2,
                explanation: "Budi Utomo didirikan oleh para pelajar STOVIA pada 20 Mei 1908 yang kemudian diperingati sebagai Hari Kebangkitan Nasional."
            },
            {
                q: "Pada awal berdirinya, tujuan utama Sarekat Dagang Islam (SDI) yang didirikan oleh H. Samanhudi di Solo pada tahun 1911 adalah...",
                options: [
                    "Membentuk tentara rakyat untuk mengusir Belanda",
                    "Menghimpun pedagang batik pribumi agar mampu bersaing dengan pedagang asing",
                    "Mengirim mahasiswa pribumi untuk belajar ke negeri Belanda",
                    "Menuntut pembentukan parlemen di Hindia Belanda"
                ],
                answer: 1,
                explanation: "SDI didirikan H. Samanhudi untuk melindungi dan memajukan ekonomi pedagang batik pribumi dari persaingan monopoli pedagang asing."
            },
            {
                q: "Organisasi politik pertama di Hindia Belanda yang secara terang-terangan menuntut kemerdekaan dengan semboyan 'Indie los van Holland' adalah...",
                options: [
                    "Budi Utomo",
                    "Muhammadiyah",
                    "Indische Partij",
                    "Taman Siswa"
                ],
                answer: 2,
                explanation: "Indische Partij yang didirikan Tiga Serangkai pada 25 Desember 1912 merupakan organisasi politik pertama yang terang-terangan menuntut kemerdekaan Hindia dari Belanda."
            },
            {
                q: "Tokoh-tokoh yang dikenal sebagai 'Tiga Serangkai' pendiri Indische Partij adalah...",
                options: [
                    "Soekarno, Mohammad Hatta, dan Sutan Sjahrir",
                    "Douwes Dekker, dr. Cipto Mangunkusumo, dan Suwardi Suryaningrat",
                    "dr. Soetomo, Wahidin Sudirohusodo, dan Gunawan Mangunkusumo",
                    "H. Samanhudi, H.O.S. Tjokroaminoto, dan Agus Salim"
                ],
                answer: 1,
                explanation: "Tiga Serangkai terdiri dari E.F.E. Douwes Dekker (Danudirdja Setiabudi), dr. Cipto Mangunkusumo, dan Suwardi Suryaningrat (Ki Hajar Dewantara)."
            },
            {
                q: "Tulisan Suwardi Suryaningrat yang berjudul 'Als Ik Eens Nederlander Was' (Seandainya Aku Seorang Belanda) bertujuan untuk...",
                options: [
                    "Memuji kemajuan teknologi yang dibawa pemerintah kolonial Belanda",
                    "Mengkritik rencana Belanda merayakan 100 tahun kemerdekaannya dari Prancis di tanah jajahan",
                    "Meminta Belanda membangun lebih banyak sekolah teknik di Bandung",
                    "Mendukung pembentukan milisi pribumi untuk membantu tentara Belanda"
                ],
                answer: 1,
                explanation: "Artikel tersebut menyindir ketidakadilan pemerintah Belanda yang memungut biaya dari rakyat jajahan untuk merayakan kemerdekaan Belanda sendiri."
            },
            {
                q: "Organisasi keagamaan dan sosial modern yang didirikan oleh K.H. Ahmad Dahlan di Yogyakarta pada 18 November 1912 adalah...",
                options: [
                    "Nahdlatul Ulama",
                    "Muhammadiyah",
                    "Jong Islamieten Bond",
                    "Majelis Islam A'la Indonesia"
                ],
                answer: 1,
                explanation: "Muhammadiyah didirikan oleh K.H. Ahmad Dahlan dengan fokus pada pemurnian ajaran Islam, pendidikan modern, dan pelayanan sosial kesehatan."
            },
            {
                q: "Organisasi mahasiswa Indonesia di Belanda yang berperan besar mempopulerkan nama 'Indonesia' sebagai identitas nasional dan menerbitkan majalah 'Indonesia Merdeka' adalah...",
                options: [
                    "Perhimpunan Indonesia (PI)",
                    "Perhimpunan Pelajar-Pelajar Indonesia (PPPI)",
                    "Partai Nasional Indonesia (PNI)",
                    "Indische Sociaal Democratische Vereeniging (ISDV)"
                ],
                answer: 0,
                explanation: "Perhimpunan Indonesia (sebelumnya Indische Vereeniging) di bawah pimpinan Mohammad Hatta dkk. mempopulerkan nama Indonesia secara internasional."
            },
            {
                q: "Strategi perjuangan 'non-kooperatif' yang dianut oleh organisasi masa radikal pada tahun 1920-an memiliki arti...",
                options: [
                    "Bekerja sama dengan Belanda melalui kursi Volksraad",
                    "Menolak segala bentuk kerja sama dengan pemerintah kolonial Belanda dan mengandalkan kekuatan sendiri",
                    "Mengutamakan pembangunan koperasi simpan pinjam di pedesaan",
                    "Menyerahkan urusan kemerdekaan sepenuhnya kepada keputusan Ratu Belanda"
                ],
                answer: 1,
                explanation: "Non-kooperatif berarti menolak bekerja sama dengan pemerintah kolonial (seperti menolak duduk di Volksraad) dan berdiri di atas kaki sendiri (self-help)."
            },
            {
                q: "Partai Nasional Indonesia (PNI) yang didirikan pada 4 Juli 1927 oleh Ir. Soekarno berlandaskan pada asas...",
                options: [
                    "Kapitalisme Liberal",
                    "Marhaenisme",
                    "Pan-Islamisme",
                    "Feodalisme Jawa"
                ],
                answer: 1,
                explanation: "PNI berasaskan Marhaenisme (sosio-nasionalisme dan sosio-demokrasi) yang memperjuangkan nasib rakyat kecil (kaum Marhaen)."
            },
            {
                q: "Pidato pembelaan Ir. Soekarno di depan pengadilan kolonial Landraad Bandung pada tahun 1930 yang menggugat penindasan kolonialisme berjudul...",
                options: [
                    "Indonesia Vrij",
                    "Indonesia Menggugat",
                    "Mencapai Indonesia Merdeka",
                    "Di Bawah Bendera Revolusi"
                ],
                answer: 1,
                explanation: "'Indonesia Menggugat' adalah judul pidato pembelaan (pleidoi) Ir. Soekarno di pengadilan Landraad Bandung tahun 1930."
            },
            {
                q: "Organisasi kepemudaan pertama yang didirikan oleh para pelajar STOVIA pada tahun 1915 dengan nama awal 'Tri Koro Dharmo' kemudian berganti nama menjadi...",
                options: [
                    "Jong Sumatranen Bond",
                    "Jong Java",
                    "Jong Celebes",
                    "Pemuda Indonesia"
                ],
                answer: 1,
                explanation: "Tri Koro Dharmo yang didirikan dr. Satiman Wiryosanjoyo pada 1915 diubah namanya menjadi Jong Java pada kongres tahun 1918 agar cakupannya lebih luas."
            },
            {
                q: "Tokoh yang menjabat sebagai ketua panitia dalam pelaksanaan Kongres Pemuda II pada tanggal 27–28 Oktober 1928 adalah...",
                options: [
                    "Mohammad Yamin",
                    "Soegondo Djojopoespito",
                    "W.R. Supratman",
                    "Amir Sjarifuddin"
                ],
                answer: 1,
                explanation: "Soegondo Djojopoespito (dari PPPI) menjadi Ketua Kongres Pemuda II, sedangkan Mohammad Yamin bertindak sebagai sekretaris dan perumus teks Sumpah Pemuda."
            },
            {
                q: "Pada penutupan Kongres Pemuda II tanggal 28 Oktober 1928, untuk pertama kalinya diperdengarkan lagu kebangsaan 'Indonesia Raya' ciptaan W.R. Supratman menggunakan alat musik...",
                options: [
                    "Piano",
                    "Biola",
                    "Gitar akustik",
                    "Seruling bambu"
                ],
                answer: 1,
                explanation: "W.R. Supratman memperdengarkan melodi lagu 'Indonesia Raya' secara instrumental dengan biola untuk menghindari pembubaran oleh polisi kolonial Belanda."
            },
            {
                q: "Makna terpenting dari ikrar Sumpah Pemuda 28 Oktober 1928 bagi perjalanan sejarah bangsa Indonesia adalah...",
                options: [
                    "Berakhirnya kekuasaan Belanda di seluruh kepulauan Nusantara",
                    "Meleburnya sifat kedaerahan menjadi satu kesadaran kebangsaan: satu tanah air, satu bangsa, dan satu bahasa Indonesia",
                    "Terbentuknya tentara keamanan rakyat di setiap provinsi",
                    "Diakuinya kedaulatan Indonesia oleh Perserikatan Bangsa-Bangsa"
                ],
                answer: 1,
                explanation: "Sumpah Pemuda menjadi tonggak kristalisasi semangat persatuan nasional yang melampaui sekat-sekat kesukuan dan kedaerahan."
            },
            {
                q: "Kongres Perempuan Indonesia I yang diselenggarakan pada tanggal 22–25 Desember 1928 di Yogyakarta diperingati setiap tahunnya sebagai...",
                options: [
                    "Hari Kartini",
                    "Hari Ibu",
                    "Hari Kebangkitan Nasional",
                    "Hari Sumpah Pemuda"
                ],
                answer: 1,
                explanation: "Tanggal pembukaan Kongres Perempuan Indonesia I, yaitu 22 Desember, ditetapkan sebagai Hari Ibu untuk mengenang kebangkitan pergerakan perempuan Indonesia."
            },
            {
                q: "Pada tahun 1930-an, banyak organisasi pergerakan nasional mengubah taktiknya menjadi kooperatif/moderat karena...",
                options: [
                    "Belanda sudah menjanjikan kemerdekaan penuh pada tahun 1935",
                    "Tindakan represif pemerintah kolonial Belanda yang menangkap dan mengasingkan tokoh-tokoh radikal",
                    "Seluruh rakyat Indonesia telah sejahtera secara ekonomi",
                    "Tidak ada lagi tokoh pemuda yang berminat pada dunia politik"
                ],
                answer: 1,
                explanation: "Sikap keras Gubernur Jenderal De Jonge yang menangkap dan mengasingkan tokoh radikal (Soekarno, Hatta, Sjahrir) memaksa pergerakan bersikap taktis/moderat agar organisasi tetap hidup."
            },
            {
                q: "Tuntutan utama dari Gabungan Politik Indonesia (GAPI) yang dibentuk pada tahun 1939 di bawah pimpinan Mohammad Husni Thamrin adalah...",
                options: [
                    "Indonesia Berparlemen",
                    "Indonesia Merdeka Tanpa Syarat",
                    "Penghapusan Sistem Tanam Paksa",
                    "Pengembalian Irian Barat"
                ],
                answer: 0,
                explanation: "GAPI melancarkan aksi dengan semboyan 'Indonesia Berparlemen', menuntut pembentukan parlemen sejati yang dipilih oleh dan untuk rakyat Indonesia."
            }
        ];

        let userAnswers = new Array(quizQuestions.length).fill(null);
        let quizSubmitted = false;

        function startQuiz() {
            document.getElementById('quiz-start-screen').classList.add('hidden');
            document.getElementById('quiz-active-screen').classList.remove('hidden');
            renderQuiz();
            document.getElementById('sec-evaluasi').scrollIntoView({ behavior: 'smooth' });
        }

        function renderQuiz() {
            const container = document.getElementById('quiz-questions-container');
            if (!container) return;
            container.innerHTML = '';

            quizQuestions.forEach((item, qIndex) => {
                const optionLetters = ['A', 'B', 'C', 'D'];
                let optionsHTML = '';

                item.options.forEach((optText, optIndex) => {
                    const isSelected = userAnswers[qIndex] === optIndex;
                    let cardStyle = 'border-slate-200 bg-white hover:bg-slate-50';
                    let badgeStyle = 'bg-slate-100 text-slate-700';
                    let statusIcon = '';

                    if (quizSubmitted) {
                        if (optIndex === item.answer) {
                            cardStyle = 'border-emerald-500 bg-emerald-50/80 text-emerald-950 font-medium';
                            badgeStyle = 'bg-emerald-600 text-white';
                            statusIcon = '<i class="fas fa-check-circle text-emerald-600 ml-auto text-lg"></i>';
                        } else if (isSelected && optIndex !== item.answer) {
                            cardStyle = 'border-red-500 bg-red-50/80 text-red-950';
                            badgeStyle = 'bg-red-600 text-white';
                            statusIcon = '<i class="fas fa-times-circle text-red-600 ml-auto text-lg"></i>';
                        } else {
                            cardStyle = 'border-slate-200 bg-slate-50/50 opacity-70';
                        }
                    } else if (isSelected) {
                        cardStyle = 'border-brand-red bg-red-50/60 ring-1 ring-brand-red';
                        badgeStyle = 'bg-brand-red text-white';
                    }

                    optionsHTML += `
                        <button type="button" onclick="selectOption(${qIndex}, ${optIndex})" ${quizSubmitted ? 'disabled' : ''} 
                            class="w-full text-left p-3.5 sm:p-4 rounded-xl border ${cardStyle} transition flex items-center space-x-3">
                            <span class="w-7 h-7 rounded-lg ${badgeStyle} font-bold text-xs flex items-center justify-center shrink-0">
                                ${optionLetters[optIndex]}
                            </span>
                            <span class="text-sm leading-snug">${optText}</span>
                            ${statusIcon}
                        </button>
                    `;
                });

                const explanationHTML = quizSubmitted ? `
                    <div class="mt-4 p-4 rounded-xl bg-amber-50 border border-amber-200 text-xs sm:text-sm text-amber-950">
                        <strong class="text-amber-800"><i class="fas fa-info-circle mr-1"></i> Pembahasan:</strong> ${item.explanation}
                    </div>
                ` : '';

                const questionBlock = `
                    <div class="p-5 sm:p-6 rounded-2xl bg-slate-50/70 border border-slate-200">
                        <div class="flex items-start space-x-3 mb-4">
                            <span class="px-2.5 py-1 rounded-lg bg-slate-800 text-white font-bold text-xs shrink-0 mt-0.5">
                                No. ${qIndex + 1}
                            </span>
                            <h3 class="font-semibold text-slate-900 text-sm sm:text-base leading-relaxed">
                                ${item.q}
                            </h3>
                        </div>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
                            ${optionsHTML}
                        </div>
                        ${explanationHTML}
                    </div>
                `;

                container.innerHTML += questionBlock;
            });
        }

        function selectOption(qIndex, optIndex) {
            if (quizSubmitted) return;
            userAnswers[qIndex] = optIndex;
            
            const answeredCount = userAnswers.filter(ans => ans !== null).length;
            document.getElementById('quiz-answered-count').textContent = answeredCount;
            document.getElementById('quiz-warning-msg').classList.add('hidden');
            
            renderQuiz();
        }

        function submitQuiz() {
            const answeredCount = userAnswers.filter(ans => ans !== null).length;
            if (answeredCount < quizQuestions.length) {
                const warning = document.getElementById('quiz-warning-msg');
                warning.classList.remove('hidden');
                warning.innerHTML = `<i class="fas fa-exclamation-triangle mr-1"></i> Kamu baru menjawab ${answeredCount} dari 20 soal. Silakan lengkapi semua soal!`;
                return;
            }

            quizSubmitted = true;
            let correct = 0;
            quizQuestions.forEach((item, idx) => {
                if (userAnswers[idx] === item.answer) correct++;
            });

            const wrong = quizQuestions.length - correct;
            const score = Math.round((correct / quizQuestions.length) * 100);

            document.getElementById('quiz-final-score').textContent = score;
            document.getElementById('quiz-correct-count').textContent = correct;
            document.getElementById('quiz-wrong-count').textContent = wrong;

            let predicate = '';
            let feedback = '';
            if (score >= 90) {
                predicate = 'Istimewa! Ahli Sejarah Muda 🏆';
                feedback = 'Pemahamanmu tentang Pergerakan Nasional Indonesia sangat luar biasa. Pertahankan semangat belajarmu!';
            } else if (score >= 75) {
                predicate = 'Bagus Sekali! Lulus Kompetensi 🌟';
                feedback = 'Kamu sudah memahami sebagian besar konsep penting Pergerakan Nasional. Cek pembahasan untuk menyempurnakan pemahamanmu.';
            } else {
                predicate = 'Terus Semangat Belajar! 📚';
                feedback = 'Jangan berkecil hati! Baca kembali modul Materi & Organisasi di EsHist, lalu coba kerjakan evaluasi ini kembali.';
            }

            document.getElementById('quiz-predicate').textContent = predicate;
            document.getElementById('quiz-feedback').textContent = feedback;

            document.getElementById('quiz-result-box').classList.remove('hidden');
            document.getElementById('submit-quiz-btn').classList.add('hidden');

            renderQuiz();
            document.getElementById('sec-evaluasi').scrollIntoView({ behavior: 'smooth' });
        }

        function resetQuiz() {
            userAnswers = new Array(quizQuestions.length).fill(null);
            quizSubmitted = false;
            document.getElementById('quiz-answered-count').textContent = '0';
            document.getElementById('quiz-result-box').classList.add('hidden');
            document.getElementById('submit-quiz-btn').classList.remove('hidden');
            document.getElementById('quiz-active-screen').classList.add('hidden');
            document.getElementById('quiz-start-screen').classList.remove('hidden');
            document.getElementById('sec-evaluasi').scrollIntoView({ behavior: 'smooth' });
        }

        // ==========================================
        // INISIALISASI SAAT HALAMAN DIMUAT
        // ==========================================
        window.onload = function() {
            renderOrganizations('semua');
            initMemoryGame();
        };
    </script>
</body>
</html>
