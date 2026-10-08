<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portal Manajemen - The Bonding Care</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        brandBlue: '#1a237e',
                        brandTeal: '#00695c',
                        brandGold: '#e6a100',
                        brandDarkBlue: '#0f172a',
                    }
                }
            }
        }
    </script>
    <style>
        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body class="bg-slate-100 font-sans text-slate-800 min-h-screen flex flex-col antialiased selection:bg-indigo-500 selection:text-white">

    <!-- LOGIN MODAL (ADMINISTRATOR AUTH) -->
    <div id="loginModal" class="fixed inset-0 bg-slate-900/80 backdrop-blur-sm flex items-center justify-center z-50 p-4 transition-all duration-300">
        <div class="bg-white rounded-2xl shadow-2xl max-w-md w-full border-t-8 border-brandBlue overflow-hidden transform transition-all">
            <div class="p-8 text-center">
                <!-- LOGO GAMBAR "file:///C:/Users/JAING/Desktop/Aplikasi%20The%20Bonding%20Cara/logo.jpg..jpg" -->
                <div class="w-24 h-24 rounded-full mx-auto flex items-center justify-center shadow-xl border-4 border-amber-300 mb-4 overflow-hidden bg-white">
                    <img src="file:///C:/Users/JAING/Desktop/Aplikasi%20The%20Bonding%20Cara/logo.jpg..jpg" alt="Logo The Bonding Care" class="w-full h-full object-cover">
                </div>
                <h2 class="text-2xl font-black text-brandBlue tracking-tight">The Bonding Care</h2>
                <p class="text-xs text-amber-600 font-bold uppercase tracking-wider mt-1">Portal Management System</p>
                <p class="text-xs text-slate-500 italic mt-2">"Building trust through emotional bonding"</p>

                <form id="loginForm" onsubmit="event.preventDefault(); handleLogin();" class="mt-6 space-y-4 text-left">
                    <div>
                        <label class="block text-xs font-bold text-slate-700 uppercase mb-1">Username Admin</label>
                        <div class="relative">
                            <span class="absolute inset-y-0 left-0 flex items-center pl-3.5 text-slate-400"><i class="fa-solid fa-user-gear"></i></span>
                            <input type="text" id="username" required value="admin" placeholder="Masukkan username" class="w-full pl-10 pr-4 py-2.5 bg-slate-50 border border-slate-300 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-brandBlue focus:bg-white transition">
                        </div>
                    </div>
                    <div>
                        <label class="block text-xs font-bold text-slate-700 uppercase mb-1">Password</label>
                        <div class="relative">
                            <span class="absolute inset-y-0 left-0 flex items-center pl-3.5 text-slate-400"><i class="fa-solid fa-key"></i></span>
                            <input type="password" id="password" required value="admin123" placeholder="••••••••" class="w-full pl-10 pr-4 py-2.5 bg-slate-50 border border-slate-300 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-brandBlue focus:bg-white transition">
                        </div>
                    </div>
                    
                    <div id="loginError" class="hidden p-3 bg-red-50 border-l-4 border-red-500 text-red-700 text-xs rounded">
                        <i class="fa-solid fa-triangle-exclamation mr-1"></i> Username atau password salah!
                    </div>

                    <button type="submit" class="w-full bg-gradient-to-r from-brandBlue to-indigo-900 hover:from-indigo-900 hover:to-brandBlue text-white font-bold py-3 rounded-lg shadow-lg hover:shadow-xl transition duration-200 text-sm flex items-center justify-center gap-2">
                        <i class="fa-solid fa-right-to-bracket"></i> Masuk Administrator
                    </button>
                </form>
            </div>
            <div class="bg-slate-50 px-6 py-3 border-t border-slate-100 text-center text-xs text-slate-400 font-medium">
                Default: Username <span class="text-slate-700 font-bold">admin</span> | Password <span class="text-slate-700 font-bold">admin123</span>
            </div>
        </div>
    </div>

    <!-- MAIN APP CONTAINER -->
    <div id="appContainer" class="hidden flex-col flex-1 min-h-screen">
        
        <!-- HEADER BRANDING BANNER -->
        <header class="bg-gradient-to-r from-teal-800 via-brandTeal to-brandBlue text-white shadow-xl relative z-10">
            <div class="max-w-7xl mx-auto px-4 py-4 sm:px-6 lg:px-8">
                <div class="flex flex-col md:flex-row items-center justify-between gap-4">
                    
                    <!-- Left: Logo & Title -->
                    <div class="flex items-center gap-4 text-center md:text-left">
                        <div class="w-16 h-16 sm:w-20 sm:h-20 bg-white rounded-full flex items-center justify-center border-2 border-amber-400 shadow-xl flex-shrink-0 overflow-hidden">
                            <img src="file:///C:/Users/JAING/Desktop/Aplikasi%20The%20Bonding%20Cara/logo.jpg..jpg" alt="Logo The Bonding Care" class="w-full h-full object-cover">
                        </div>
                        <div>
                            <div class="flex items-center justify-center md:justify-start gap-2">
                                <h1 class="text-lg sm:text-2xl font-black uppercase tracking-wider text-white">Selamat Datang di Portal Manajemen "THE BONDING CARE"</h1>
                            </div>
                            <p class="text-amber-300 italic font-semibold text-xs sm:text-sm mt-0.5">"Building trust through emotional bonding"</p>
                            <p class="text-teal-200 text-xs font-medium mt-0.5"><i class="fa-solid fa-hand-holding-heart text-amber-300 mr-1"></i> "Trust Each Other, Committed to Together"</p>
                        </div>
                    </div>

                    <!-- Right: Admin Status & Logout -->
                    <div class="flex items-center gap-3 bg-white/10 backdrop-blur-md px-4 py-2.5 rounded-xl border border-white/20">
                        <div class="text-right text-xs">
                            <p class="font-bold text-white"><i class="fa-solid fa-user-shield text-amber-400 mr-1"></i> Admin Portal</p>
                            <p class="text-emerald-300 text-[10px] font-semibold"><i class="fa-solid fa-circle text-[8px] mr-1 animate-pulse"></i> Sesi Aktif</p>
                        </div>
                        <button onclick="handleLogout()" class="bg-rose-600 hover:bg-rose-700 text-white text-xs px-3 py-2 rounded-lg font-bold shadow transition flex items-center gap-1.5">
                            <i class="fa-solid fa-power-off"></i> Keluar
                        </button>
                    </div>
                </div>
            </div>

            <!-- CONTACT & OFFICE BAR -->
            <div class="bg-slate-900/90 text-slate-300 text-xs py-2 px-4 border-t border-slate-800">
                <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-2">
                    <div class="flex items-center gap-2 text-center md:text-left">
                        <i class="fa-solid fa-location-dot text-amber-400"></i>
                        <span>Pondok Timur Mas Blok H3/21, Jl. Pondok Nila Mas I, Rt 008/Rw 13, Jaka Setia Bekasi Selatan, Kode Pos 17147</span>
                    </div>
                    <div class="flex items-center gap-4 font-medium">
                        <a href="https://wa.me/6283193293745" target="_blank" class="hover:text-amber-300 transition flex items-center gap-1">
                            <i class="fa-brands fa-whatsapp text-emerald-400"></i> WA: 0831 9329 3745
                        </a>
                        <a href="mailto:thebondingcare@gmail.com" class="hover:text-amber-300 transition flex items-center gap-1">
                            <i class="fa-solid fa-envelope text-amber-400"></i> thebondingcare@gmail.com
                        </a>
                    </div>
                </div>
            </div>
        </header>

        <!-- NAVIGATION MENU -->
        <nav class="bg-white shadow-md border-b border-slate-200 sticky top-0 z-30">
            <div class="max-w-7xl mx-auto px-4">
                <div class="flex items-center justify-between overflow-x-auto custom-scrollbar py-2 gap-1 text-xs sm:text-sm font-bold text-slate-600">
                    <button onclick="switchTab('beranda')" id="btn-beranda" class="nav-btn px-3.5 py-2 rounded-lg bg-brandBlue text-white flex items-center gap-1.5 whitespace-nowrap transition">
                        <i class="fa-solid fa-chart-line"></i> Beranda
                    </button>
                    <button onclick="switchTab('pasien')" id="btn-pasien" class="nav-btn px-3.5 py-2 rounded-lg hover:bg-slate-100 flex items-center gap-1.5 whitespace-nowrap transition">
                        <i class="fa-solid fa-hospital-user"></i> Profil Pasien
                    </button>
                    <button onclick="switchTab('perawat')" id="btn-perawat" class="nav-btn px-3.5 py-2 rounded-lg hover:bg-slate-100 flex items-center gap-1.5 whitespace-nowrap transition">
                        <i class="fa-solid fa-user-nurse"></i> Tim Perawat
                    </button>
                    <button onclick="switchTab('input-bonding')" id="btn-input-bonding" class="nav-btn px-3.5 py-2 rounded-lg hover:bg-slate-100 flex items-center gap-1.5 whitespace-nowrap transition">
                        <i class="fa-solid fa-heart-pulse"></i> Input Bonding
                    </button>
                    <button onclick="switchTab('layanan')" id="btn-layanan" class="nav-btn px-3.5 py-2 rounded-lg hover:bg-slate-100 flex items-center gap-1.5 whitespace-nowrap transition">
                        <i class="fa-solid fa-hand-holding-medical"></i> Layanan
                    </button>
                    <button onclick="switchTab('tarif')" id="btn-tarif" class="nav-btn px-3.5 py-2 rounded-lg hover:bg-slate-100 flex items-center gap-1.5 whitespace-nowrap transition">
                        <i class="fa-solid fa-tags"></i> Tarif Master
                    </button>
                    <button onclick="switchTab('laporan')" id="btn-laporan" class="nav-btn px-3.5 py-2 rounded-lg hover:bg-slate-100 flex items-center gap-1.5 whitespace-nowrap transition">
                        <i class="fa-solid fa-file-invoice-dollar"></i> Laporan
                    </button>
                    <button onclick="switchTab('users')" id="btn-users" class="nav-btn px-3.5 py-2 rounded-lg hover:bg-slate-100 flex items-center gap-1.5 whitespace-nowrap transition">
                        <i class="fa-solid fa-users-gear"></i> Manajemen User
                    </button>
                    <button onclick="switchTab('master')" id="btn-master" class="nav-btn px-3.5 py-2 rounded-lg hover:bg-slate-100 flex items-center gap-1.5 whitespace-nowrap transition">
                        <i class="fa-solid fa-database"></i> Data Master
                    </button>
                    <button onclick="switchTab('tentang')" id="btn-tentang" class="nav-btn px-3.5 py-2 rounded-lg hover:bg-slate-100 flex items-center gap-1.5 whitespace-nowrap transition">
                        <i class="fa-solid fa-circle-info"></i> Informasi
                    </button>
                </div>
            </div>
        </nav>

        <!-- CONTENT AREA -->
        <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 flex-1 w-full">

            <!-- 1. BERANDA (DASHBOARD) -->
            <section id="page-beranda" class="page-content space-y-6">
                <!-- STATS CARDS -->
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                    <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200 flex items-center justify-between">
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase tracking-wider">Total Pasien</p>
                            <h3 id="stat-pasien" class="text-3xl font-black text-brandBlue mt-1">0</h3>
                            <p class="text-[11px] text-emerald-600 font-semibold mt-1"><i class="fa-solid fa-circle-check"></i> Terdaftar aktif</p>
                        </div>
                        <div class="w-12 h-12 bg-blue-50 text-brandBlue rounded-xl flex items-center justify-center text-xl font-bold">
                            <i class="fa-solid fa-hospital-user"></i>
                        </div>
                    </div>

                    <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200 flex items-center justify-between">
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase tracking-wider">Tim Perawat</p>
                            <h3 id="stat-perawat" class="text-3xl font-black text-brandTeal mt-1">0</h3>
                            <p class="text-[11px] text-teal-600 font-semibold mt-1"><i class="fa-solid fa-user-check"></i> Siap On-Duty</p>
                        </div>
                        <div class="w-12 h-12 bg-teal-50 text-brandTeal rounded-xl flex items-center justify-center text-xl font-bold">
                            <i class="fa-solid fa-user-nurse"></i>
                        </div>
                    </div>

                    <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200 flex items-center justify-between">
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase tracking-wider">Jurnal Bonding</p>
                            <h3 id="stat-bonding" class="text-3xl font-black text-amber-600 mt-1">0</h3>
                            <p class="text-[11px] text-amber-600 font-semibold mt-1"><i class="fa-solid fa-notes-medical"></i> Catatan terinput</p>
                        </div>
                        <div class="w-12 h-12 bg-amber-50 text-amber-600 rounded-xl flex items-center justify-center text-xl font-bold">
                            <i class="fa-solid fa-heart-pulse"></i>
                        </div>
                    </div>

                    <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200 flex items-center justify-between">
                        <div>
                            <p class="text-xs font-bold text-slate-400 uppercase tracking-wider">Total Layanan</p>
                            <h3 id="stat-layanan" class="text-3xl font-black text-indigo-600 mt-1">0</h3>
                            <p class="text-[11px] text-indigo-600 font-semibold mt-1"><i class="fa-solid fa-hand-holding-medical"></i> Paket tersedia</p>
                        </div>
                        <div class="w-12 h-12 bg-indigo-50 text-indigo-600 rounded-xl flex items-center justify-center text-xl font-bold">
                            <i class="fa-solid fa-list-check"></i>
                        </div>
                    </div>
                </div>

                <!-- QUICK ACTIONS & BANNER -->
                <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                    <div class="lg:col-span-2 bg-white rounded-2xl shadow-sm border border-slate-200 p-6 flex flex-col justify-between">
                        <div>
                            <div class="flex items-center justify-between mb-4">
                                <h3 class="text-lg font-extrabold text-brandBlue flex items-center gap-2">
                                    <i class="fa-solid fa-users-rectangle text-amber-500"></i> Peluncuran & Komitmen Tim "The Bonding Care"
                                </h3>
                                <span class="text-xs font-bold bg-amber-100 text-amber-800 px-3 py-1 rounded-full">Home Care Terpercaya</span>
                            </div>
                            
                            <div class="relative bg-gradient-to-r from-teal-700 to-brandBlue rounded-xl p-6 text-white overflow-hidden shadow-inner mb-4">
                                <div class="relative z-10">
                                    <p class="text-xs font-bold text-amber-300 uppercase tracking-widest mb-1">LAUNCHING THE BONDING CARE</p>
                                    <h4 class="text-xl sm:text-2xl font-black">"Trust Each Other, Committed to Together"</h4>
                                    <p class="text-xs sm:text-sm text-slate-200 mt-2 max-w-xl">
                                        Memberikan pelayanan perawatan medis & pendampingan emosional terbaik langsung ke rumah Anda dengan tenaga kesehatan profesional dan penuh kasih.
                                    </p>
                                </div>
                                <i class="fa-solid fa-heart-pulse absolute -right-4 -bottom-6 text-9xl text-white/10 pointer-events-none"></i>
                            </div>

                            <p class="text-xs sm:text-sm text-slate-600 leading-relaxed">
                                Portal Manajemen ini dirancang untuk memudahkan pengaturan jadwal perawat, pemantauan kondisi vital pasien, pencatatan jurnal emosional (*Bonding Progress*), serta pengolahan laporan administrasi secara transparan dan terstruktur.
                            </p>
                        </div>

                        <div class="mt-6 pt-4 border-t border-slate-100 flex flex-wrap gap-2">
                            <button onclick="switchTab('input-bonding')" class="bg-brandBlue hover:bg-indigo-900 text-white text-xs font-bold px-4 py-2.5 rounded-xl shadow transition flex items-center gap-2">
                                <i class="fa-solid fa-plus-circle"></i> Input Catatan Bonding
                            </button>
                            <button onclick="openModal('modalPasien')" class="bg-brandTeal hover:bg-teal-900 text-white text-xs font-bold px-4 py-2.5 rounded-xl shadow transition flex items-center gap-2">
                                <i class="fa-solid fa-user-plus"></i> Tambah Pasien
                            </button>
                            <button onclick="switchTab('laporan')" class="bg-slate-800 hover:bg-slate-900 text-white text-xs font-bold px-4 py-2.5 rounded-xl shadow transition flex items-center gap-2">
                                <i class="fa-solid fa-file-pdf"></i> Lihat Laporan
                            </button>
                        </div>
                    </div>

                    <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6 flex flex-col">
                        <h3 class="text-base font-extrabold text-slate-800 mb-4 flex items-center gap-2">
                            <i class="fa-solid fa-clock-rotate-left text-brandBlue"></i> Catatan Bonding Terbaru
                        </h3>
                        <div id="dashboardRecentLogs" class="space-y-3 flex-1 overflow-y-auto max-h-80 custom-scrollbar pr-1">
                            <!-- Populated via JS -->
                        </div>
                    </div>
                </div>
            </section>

            <!-- 2. PROFIL PASIEN -->
            <section id="page-pasien" class="page-content hidden space-y-6">
                <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6">
                    <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4 mb-6">
                        <div>
                            <h2 class="text-xl font-black text-brandBlue flex items-center gap-2">
                                <i class="fa-solid fa-hospital-user text-brandTeal"></i> Profil & Data Pasien Home Care
                            </h2>
                            <p class="text-xs text-slate-500 mt-0.5">Kelola data riwayat medis dan informasi keluarga pasien</p>
                        </div>
                        <button onclick="openModal('modalPasien')" class="bg-brandBlue hover:bg-indigo-900 text-white text-xs font-bold px-4 py-2.5 rounded-xl shadow transition flex items-center gap-2">
                            <i class="fa-solid fa-plus"></i> Tambah Pasien Baru
                        </button>
                    </div>

                    <div class="mb-4">
                        <div class="relative max-w-md">
                            <span class="absolute inset-y-0 left-0 flex items-center pl-3 text-slate-400"><i class="fa-solid fa-magnifying-glass"></i></span>
                            <input type="text" id="searchPasien" oninput="renderPasienTable()" placeholder="Cari nama pasien, diagnosa, atau alamat..." class="w-full pl-9 pr-4 py-2 bg-slate-50 border border-slate-200 rounded-xl text-xs focus:outline-none focus:ring-2 focus:ring-brandBlue">
                        </div>
                    </div>

                    <div class="overflow-x-auto rounded-xl border border-slate-200">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="bg-slate-50 text-slate-600 text-xs uppercase font-extrabold border-b border-slate-200">
                                    <th class="p-3">ID Pasien</th>
                                    <th class="p-3">Nama Lengkap</th>
                                    <th class="p-3">Umur / JK</th>
                                    <th class="p-3">Diagnosa Utama</th>
                                    <th class="p-3">PJ / Kontak</th>
                                    <th class="p-3">Alamat</th>
                                    <th class="p-3 text-center">Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="tablePasienBody" class="text-xs divide-y divide-slate-100">
                                <!-- JS Populated -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- 3. TIM PERAWAT -->
            <section id="page-perawat" class="page-content hidden space-y-6">
                <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6">
                    <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4 mb-6">
                        <div>
                            <h2 class="text-xl font-black text-brandBlue flex items-center gap-2">
                                <i class="fa-solid fa-user-nurse text-brandTeal"></i> Tim Perawat & Tenaga Medis
                            </h2>
                            <p class="text-xs text-slate-500 mt-0.5">Daftar perawat profesional, status tugas, dan spesialisasi</p>
                        </div>
                        <button onclick="openModal('modalPerawat')" class="bg-brandTeal hover:bg-teal-900 text-white text-xs font-bold px-4 py-2.5 rounded-xl shadow transition flex items-center gap-2">
                            <i class="fa-solid fa-plus"></i> Tambah Perawat
                        </button>
                    </div>

                    <div id="gridPerawat" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
                        <!-- JS Populated -->
                    </div>
                </div>
            </section>

            <!-- 4. INPUT BONDING -->
            <section id="page-input-bonding" class="page-content hidden">
                <div class="max-w-3xl mx-auto bg-white rounded-2xl shadow-sm border border-slate-200 p-6 sm:p-8">
                    <div class="border-b border-slate-100 pb-4 mb-6">
                        <h2 class="text-xl font-black text-brandBlue flex items-center gap-2">
                            <i class="fa-solid fa-heart-circle-plus text-rose-500"></i> Form Input Catatan Bonding & Perkembangan Pasien
                        </h2>
                        <p class="text-xs text-slate-500 mt-1">Catat kondisi vital, perkembangan fisik, dan respon emosional pasien setiap kunjungan.</p>
                    </div>

                    <form id="formBonding" onsubmit="event.preventDefault(); saveBondingLog();" class="space-y-5 text-xs sm:text-sm">
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label class="block font-bold text-slate-700 mb-1">Pilih Pasien <span class="text-red-500">*</span></label>
                                <select id="bondPasienSelect" required class="w-full bg-slate-50 border border-slate-300 rounded-xl p-2.5 focus:ring-2 focus:ring-brandBlue focus:bg-white">
                                    <!-- Populated JS -->
                                </select>
                            </div>
                            <div>
                                <label class="block font-bold text-slate-700 mb-1">Perawat Penanggung Jawab <span class="text-red-500">*</span></label>
                                <select id="bondPerawatSelect" required class="w-full bg-slate-50 border border-slate-300 rounded-xl p-2.5 focus:ring-2 focus:ring-brandBlue focus:bg-white">
                                    <!-- Populated JS -->
                                </select>
                            </div>
                        </div>

                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label class="block font-bold text-slate-700 mb-1">Tanggal & Waktu Kunjungan <span class="text-red-500">*</span></label>
                                <input type="datetime-local" id="bondTanggal" required class="w-full bg-slate-50 border border-slate-300 rounded-xl p-2.5 focus:ring-2 focus:ring-brandBlue focus:bg-white">
                            </div>
                            <div>
                                <label class="block font-bold text-slate-700 mb-1">Status Respon Emosional Pasien</label>
                                <select id="bondEmosi" class="w-full bg-slate-50 border border-slate-300 rounded-xl p-2.5 focus:ring-2 focus:ring-brandBlue focus:bg-white">
                                    <option value="Sangat Kooperatif & Ceria">😊 Sangat Kooperatif & Ceria</option>
                                    <option value="Tenang & Nyaman">🙂 Tenang & Nyaman</option>
                                    <option value="Cemas / Sedikit Gelisah">😐 Cemas / Sedikit Gelisah</option>
                                    <option value="Butuh Pendampingan Extra">😟 Butuh Pendampingan Extra</option>
                                </select>
                            </div>
                        </div>

                        <div class="bg-slate-50 p-4 rounded-xl border border-slate-200 grid grid-cols-2 sm:grid-cols-4 gap-3">
                            <div>
                                <label class="block text-[11px] font-bold text-slate-600 mb-1">Tekanan Darah</label>
                                <input type="text" id="bondTD" placeholder="120/80 mmHg" class="w-full bg-white border border-slate-300 rounded-lg p-2 text-xs">
                            </div>
                            <div>
                                <label class="block text-[11px] font-bold text-slate-600 mb-1">Nadi (x/mnt)</label>
                                <input type="text" id="bondNadi" placeholder="80" class="w-full bg-white border border-slate-300 rounded-lg p-2 text-xs">
                            </div>
                            <div>
                                <label class="block text-[11px] font-bold text-slate-600 mb-1">Suhu (°C)</label>
                                <input type="text" id="bondSuhu" placeholder="36.5" class="w-full bg-white border border-slate-300 rounded-lg p-2 text-xs">
                            </div>
                            <div>
                                <label class="block text-[11px] font-bold text-slate-600 mb-1">Saturasi O2 (%)</label>
                                <input type="text" id="bondSPO2" placeholder="98" class="w-full bg-white border border-slate-300 rounded-lg p-2 text-xs">
                            </div>
                        </div>

                        <div>
                            <label class="block font-bold text-slate-700 mb-1">Catatan Perkembangan & Emotional Bonding <span class="text-red-500">*</span></label>
                            <textarea id="bondCatatan" rows="4" required placeholder="Tuliskan respon interaksi emosional, keluhan pasien, tindakan medis yang diberikan, dan pesan keluarga..." class="w-full bg-slate-50 border border-slate-300 rounded-xl p-3 focus:ring-2 focus:ring-brandBlue focus:bg-white"></textarea>
                        </div>

                        <button type="submit" class="w-full bg-gradient-to-r from-brandBlue to-brandTeal hover:opacity-95 text-white font-bold py-3 rounded-xl shadow-lg transition flex items-center justify-center gap-2">
                            <i class="fa-solid fa-floppy-disk"></i> Simpan Jurnal Bonding
                        </button>
                    </form>
                </div>
            </section>

            <!-- 5. LAYANAN -->
            <section id="page-layanan" class="page-content hidden space-y-6">
                <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6">
                    <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4 mb-6">
                        <div>
                            <h2 class="text-xl font-black text-brandBlue flex items-center gap-2">
                                <i class="fa-solid fa-hand-holding-medical text-brandTeal"></i> Layanan Home Care
                            </h2>
                            <p class="text-xs text-slate-500 mt-0.5">Katalog layanan perawatan medis dan pendampingan</p>
                        </div>
                        <button onclick="openModal('modalLayanan')" class="bg-brandBlue hover:bg-indigo-900 text-white text-xs font-bold px-4 py-2.5 rounded-xl shadow transition flex items-center gap-2">
                            <i class="fa-solid fa-plus"></i> Tambah Layanan
                        </button>
                    </div>

                    <div id="gridLayanan" class="grid grid-cols-1 md:grid-cols-3 gap-6">
                        <!-- Populated JS -->
                    </div>
                </div>
            </section>

            <!-- 6. TARIF MASTER -->
            <section id="page-tarif" class="page-content hidden space-y-6">
                <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6">
                    <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4 mb-6">
                        <div>
                            <h2 class="text-xl font-black text-brandBlue flex items-center gap-2">
                                <i class="fa-solid fa-tags text-amber-500"></i> Master Tarif Layanan
                            </h2>
                            <p class="text-xs text-slate-500 mt-0.5">Daftar penawaran harga paket dan tindakan perawat</p>
                        </div>
                        <button onclick="openModal('modalTarif')" class="bg-amber-600 hover:bg-amber-700 text-white text-xs font-bold px-4 py-2.5 rounded-xl shadow transition flex items-center gap-2">
                            <i class="fa-solid fa-plus"></i> Tambah Tarif
                        </button>
                    </div>

                    <div class="overflow-x-auto rounded-xl border border-slate-200">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="bg-slate-50 text-slate-600 text-xs uppercase font-extrabold border-b border-slate-200">
                                    <th class="p-3">Kode Tarif</th>
                                    <th class="p-3">Nama Paket / Layanan</th>
                                    <th class="p-3">Durasi / Satuan</th>
                                    <th class="p-3">Harga (Rp)</th>
                                    <th class="p-3 text-center">Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="tableTarifBody" class="text-xs divide-y divide-slate-100">
                                <!-- Populated JS -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- 7. LAPORAN -->
            <section id="page-laporan" class="page-content hidden space-y-6">
                <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6">
                    <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4 mb-6">
                        <div>
                            <h2 class="text-xl font-black text-brandBlue flex items-center gap-2">
                                <i class="fa-solid fa-file-invoice-dollar text-emerald-600"></i> Laporan Aktivitas & Rekapitulasi Bonding Care
                            </h2>
                            <p class="text-xs text-slate-500 mt-0.5">Rekapitulasi catatan kunjungan perawat dan riwayat tindakan medis</p>
                        </div>
                        <div class="flex items-center gap-2">
                            <button onclick="exportReportToCSV()" class="bg-emerald-700 hover:bg-emerald-800 text-white text-xs font-bold px-3 py-2 rounded-lg shadow transition flex items-center gap-1.5">
                                <i class="fa-solid fa-file-excel"></i> Export CSV/Excel
                            </button>
                            <button onclick="window.print()" class="bg-slate-800 hover:bg-slate-900 text-white text-xs font-bold px-3 py-2 rounded-lg shadow transition flex items-center gap-1.5">
                                <i class="fa-solid fa-print"></i> Cetak PDF
                            </button>
                        </div>
                    </div>

                    <div class="bg-slate-50 p-4 rounded-xl border border-slate-200 mb-6 grid grid-cols-1 sm:grid-cols-3 gap-4">
                        <div>
                            <label class="block text-xs font-bold text-slate-600 mb-1">Cari Laporan</label>
                            <input type="text" id="reportSearch" oninput="renderLaporanTable()" placeholder="Cari pasien / perawat..." class="w-full bg-white border border-slate-300 rounded-lg p-2 text-xs">
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-slate-600 mb-1">Filter Respon Emosional</label>
                            <select id="reportFilterEmosi" onchange="renderLaporanTable()" class="w-full bg-white border border-slate-300 rounded-lg p-2 text-xs">
                                <option value="">Semua Respon</option>
                                <option value="Sangat Kooperatif & Ceria">😊 Sangat Kooperatif & Ceria</option>
                                <option value="Tenang & Nyaman">🙂 Tenang & Nyaman</option>
                                <option value="Cemas / Sedikit Gelisah">😐 Cemas / Sedikit Gelisah</option>
                                <option value="Butuh Pendampingan Extra">😟 Butuh Pendampingan Extra</option>
                            </select>
                        </div>
                        <div class="flex items-end">
                            <button onclick="resetLaporanFilter()" class="w-full bg-slate-200 hover:bg-slate-300 text-slate-700 text-xs font-bold py-2 rounded-lg transition">
                                Reset Filter
                            </button>
                        </div>
                    </div>

                    <div class="overflow-x-auto rounded-xl border border-slate-200">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="bg-slate-50 text-slate-600 text-xs uppercase font-extrabold border-b border-slate-200">
                                    <th class="p-3">Waktu</th>
                                    <th class="p-3">Pasien</th>
                                    <th class="p-3">Perawat</th>
                                    <th class="p-3">Tanda Vital</th>
                                    <th class="p-3">Respon Emosi</th>
                                    <th class="p-3">Catatan Perkembangan</th>
                                    <th class="p-3 text-center">Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="tableLaporanBody" class="text-xs divide-y divide-slate-100">
                                <!-- Populated JS -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- 8. MANAJEMEN USER -->
            <section id="page-users" class="page-content hidden space-y-6">
                <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6">
                    <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4 mb-6">
                        <div>
                            <h2 class="text-xl font-black text-brandBlue flex items-center gap-2">
                                <i class="fa-solid fa-users-gear text-brandTeal"></i> Manajemen Pengguna & Hak Akses
                            </h2>
                            <p class="text-xs text-slate-500 mt-0.5">Kelola akun staf, perawat, supervisor, dan hak akses portal</p>
                        </div>
                        <button onclick="openModal('modalUser')" class="bg-brandBlue hover:bg-indigo-900 text-white text-xs font-bold px-4 py-2.5 rounded-xl shadow transition flex items-center gap-2">
                            <i class="fa-solid fa-user-plus"></i> Tambah Pengguna Baru
                        </button>
                    </div>

                    <div class="overflow-x-auto rounded-xl border border-slate-200">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="bg-slate-50 text-slate-600 text-xs uppercase font-extrabold border-b border-slate-200">
                                    <th class="p-3">ID User</th>
                                    <th class="p-3">Nama Pengguna</th>
                                    <th class="p-3">Username</th>
                                    <th class="p-3">Role / Jabatan</th>
                                    <th class="p-3">Status</th>
                                    <th class="p-3 text-center">Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="tableUserBody" class="text-xs divide-y divide-slate-100">
                                <!-- JS Populated -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- 9. DATA MASTER -->
            <section id="page-master" class="page-content hidden space-y-6">
                <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6">
                    <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4 mb-6">
                        <div>
                            <h2 class="text-xl font-black text-brandBlue flex items-center gap-2">
                                <i class="fa-solid fa-database text-brandTeal"></i> Pengaturan Data Master Sistem
                            </h2>
                            <p class="text-xs text-slate-500 mt-0.5">Kelola cakupan area layanan, kategori perawat, dan hak akses staf portal.</p>
                        </div>
                        <button onclick="openModal('modalMasterData')" class="bg-brandTeal hover:bg-teal-900 text-white text-xs font-bold px-4 py-2.5 rounded-xl shadow transition flex items-center gap-2">
                            <i class="fa-solid fa-plus"></i> Input Master Data Baru
                        </button>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div class="p-5 border border-slate-200 rounded-2xl bg-slate-50/50 space-y-3">
                            <div class="flex items-center justify-between">
                                <h4 class="font-bold text-sm text-brandBlue"><i class="fa-solid fa-map-location-dot mr-2"></i> Area Coverage Layanan</h4>
                                <span class="bg-blue-100 text-brandBlue text-[10px] font-bold px-2 py-0.5 rounded">Bekasi & Sekitarnya</span>
                            </div>
                            <ul id="listAreaCoverage" class="text-xs text-slate-600 space-y-1.5 list-disc pl-4">
                                <li>Pondok Timur Mas & Jaka Setia</li>
                                <li>Bekasi Selatan & Bekasi Barat</li>
                                <li>Pekayon, Galaxi, & Kemang Pratama</li>
                                <li>Caman & Jatibening</li>
                            </ul>
                        </div>

                        <div class="p-5 border border-slate-200 rounded-2xl bg-slate-50/50 space-y-3">
                            <div class="flex items-center justify-between">
                                <h4 class="font-bold text-sm text-brandBlue"><i class="fa-solid fa-user-shield mr-2"></i> Hak Akses Portal (User Roles)</h4>
                                <span class="bg-emerald-100 text-emerald-800 text-[10px] font-bold px-2 py-0.5 rounded">Administrator</span>
                            </div>
                            <ul id="listUserRoles" class="text-xs text-slate-600 space-y-1.5 list-disc pl-4">
                                <li><b>Super Admin:</b> Full Access (Kelola Pasien, Perawat, Tarif & Laporan)</li>
                                <li><b>Perawat/Nurse:</b> Akses Input Jurnal Bonding & Lihat Profil Pasien</li>
                                <li><b>Keuangan:</b> Akses Master Tarif & Export Laporan</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </section>

            <!-- 10. INFORMASI TENTANG BONDING CARE -->
            <section id="page-tentang" class="page-content hidden space-y-6">
                <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6 sm:p-8 space-y-8">
                    
                    <div class="flex flex-col sm:flex-row items-center gap-6 pb-6 border-b border-slate-100">
                        <div class="w-28 h-28 bg-white rounded-full flex items-center justify-center border-4 border-amber-300 shadow-xl flex-shrink-0 overflow-hidden">
                            <img src="file:///C:/Users/JAING/Desktop/Aplikasi%20The%20Bonding%20Cara/logo.jpg..jpg" alt="Logo The Bonding Care" class="w-full h-full object-cover">
                        </div>
                        <div class="text-center sm:text-left flex-1">
                            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2">
                                <div>
                                    <h2 class="text-2xl sm:text-3xl font-black text-brandBlue">The Bonding Care</h2>
                                    <p class="text-sm font-bold text-amber-600 italic mt-1">"Building trust through emotional bonding"</p>
                                    <p class="text-xs text-brandTeal font-semibold mt-1">"Trust Each Other, Committed to Together"</p>
                                </div>
                                <button onclick="openModal('modalInformasi')" class="bg-amber-600 hover:bg-amber-700 text-white text-xs font-bold px-4 py-2.5 rounded-xl shadow transition flex items-center justify-center gap-2 self-start">
                                    <i class="fa-solid fa-bullhorn"></i> Tambah Informasi Baru
                                </button>
                            </div>
                        </div>
                    </div>

                    <div>
                        <h3 class="font-extrabold text-brandBlue text-base mb-3 flex items-center gap-2">
                            <i class="fa-solid fa-newspaper text-brandTeal"></i> Pengumuman & Informasi Terbaru
                        </h3>
                        <div id="containerInformasi" class="grid grid-cols-1 md:grid-cols-2 gap-4">
                            <!-- JS Populated -->
                        </div>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div class="bg-slate-50 p-6 rounded-2xl border border-slate-200">
                            <h3 class="font-extrabold text-brandBlue text-base mb-2 flex items-center gap-2">
                                <i class="fa-solid fa-bullseye text-amber-500"></i> Filosofi Layanan
                            </h3>
                            <p class="text-xs sm:text-sm text-slate-600 leading-relaxed">
                                <b>The Bonding Care</b> berdiri atas dasar komitmen bahwa perawatan kesehatan terbaik membutuhkan keseimbangan antara kecakapan tindakan medis profesional dan sentuhan kehangatan emosional (*emotional bonding*). Kami hadir mendampingi pasien dan keluarga untuk mencapai kualitas hidup optimal di rumah sendiri.
                            </p>
                        </div>

                        <div class="bg-slate-50 p-6 rounded-2xl border border-slate-200">
                            <h3 class="font-extrabold text-brandBlue text-base mb-2 flex items-center gap-2">
                                <i class="fa-solid fa-star text-amber-500"></i> Keunggulan Utama
                            </h3>
                            <ul class="text-xs sm:text-sm text-slate-600 space-y-2 list-disc pl-4">
                                <li>Tim perawat tersertifikasi & berpengalaman medis.</li>
                                <li>Pendekatan empatik berfokus pada kenyamanan psikologis pasien.</li>
                                <li>Sistem pemantauan kesehatan terintegrasi digital.</li>
                                <li>Layanan fleksibel 24/7 sesuai kebutuhan keluarga.</li>
                            </ul>
                        </div>
                    </div>

                    <div class="bg-gradient-to-r from-brandBlue to-indigo-950 text-white p-6 rounded-2xl shadow-md">
                        <h3 class="font-extrabold text-amber-400 text-base mb-4 flex items-center gap-2">
                            <i class="fa-solid fa-building text-white"></i> Alamat Kantor & Pusat Layanan
                        </h3>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-xs sm:text-sm">
                            <div class="space-y-2">
                                <p><i class="fa-solid fa-location-dot text-amber-400 mr-2"></i> <b>Alamat Lengkap:</b></p>
                                <p class="text-slate-200 pl-6">Pondok Timur Mas Blok H3/21, Jl. Pondok Nila Mas I, Rt 008/Rw 13, Jaka Setia, Bekasi Selatan, Kode Pos 17147</p>
                            </div>
                            <div class="space-y-2">
                                <p><i class="fa-solid fa-phone text-amber-400 mr-2"></i> <b>Kontak Resmi:</b></p>
                                <p class="text-slate-200 pl-6"><i class="fa-brands fa-whatsapp text-emerald-400 mr-1"></i> WhatsApp: 0831 9329 3745</p>
                                <p class="text-slate-200 pl-6"><i class="fa-solid fa-envelope text-amber-300 mr-1"></i> Email: thebondingcare@gmail.com</p>
                            </div>
                        </div>
                    </div>

                </div>
            </section>

        </main>

        <!-- FOOTER -->
        <footer class="bg-slate-900 text-slate-400 text-xs py-4 text-center border-t border-slate-800">
            <div class="max-w-7xl mx-auto px-4 flex flex-col sm:flex-row items-center justify-between gap-2">
                <p>&copy; 2026 <b>The Bonding Care</b>. All Rights Reserved.</p>
                <p class="text-slate-500">Portal Manajemen Home Care Terpadu</p>
            </div>
        </footer>

    </div>

    <!-- MODAL POPUPS -->

    <!-- 1. MODAL TAMBAH PASIEN -->
    <div id="modalPasien" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm hidden items-center justify-center z-50 p-4 overflow-y-auto">
        <div class="bg-white rounded-2xl shadow-2xl max-w-lg w-full p-6 border-t-4 border-brandBlue">
            <div class="flex items-center justify-between pb-3 border-b mb-4">
                <h3 class="font-extrabold text-brandBlue text-base"><i class="fa-solid fa-hospital-user mr-1"></i> Tambah Data Pasien Baru</h3>
                <button onclick="closeModal('modalPasien')" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="formPasien" onsubmit="event.preventDefault(); savePasien();" class="space-y-3 text-xs">
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Nama Lengkap Pasien <span class="text-red-500">*</span></label>
                    <input type="text" id="pNama" required placeholder="Contoh: Bpk. H. Sutrisno" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block font-bold text-slate-700 mb-1">Umur (Tahun) <span class="text-red-500">*</span></label>
                        <input type="number" id="pUmur" required placeholder="65" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                    </div>
                    <div>
                        <label class="block font-bold text-slate-700 mb-1">Jenis Kelamin</label>
                        <select id="pJK" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                            <option value="Laki-Laki">Laki-Laki</option>
                            <option value="Perempuan">Perempuan</option>
                        </select>
                    </div>
                </div>
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Diagnosa Utama <span class="text-red-500">*</span></label>
                    <input type="text" id="pDiagnosa" required placeholder="Contoh: Perawatan Pasca Stroke / Lansia" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                </div>
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Penanggung Jawab / Kontak WA <span class="text-red-500">*</span></label>
                    <input type="text" id="pKontak" required placeholder="0812xxxxxx (Nama Anak/Keluarga)" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                </div>
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Alamat Domisili <span class="text-red-500">*</span></label>
                    <textarea id="pAlamat" rows="2" required placeholder="Alamat lengkap lokasi pendampingan home care..." class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5"></textarea>
                </div>
                <div class="pt-3 flex justify-end gap-2">
                    <button type="button" onclick="closeModal('modalPasien')" class="px-4 py-2 bg-slate-200 text-slate-700 font-bold rounded-lg">Batal</button>
                    <button type="submit" class="px-4 py-2 bg-brandBlue text-white font-bold rounded-lg hover:bg-indigo-900">Simpan Pasien</button>
                </div>
            </form>
        </div>
    </div>

    <!-- 2. MODAL TAMBAH PERAWAT -->
    <div id="modalPerawat" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm hidden items-center justify-center z-50 p-4 overflow-y-auto">
        <div class="bg-white rounded-2xl shadow-2xl max-w-lg w-full p-6 border-t-4 border-brandTeal">
            <div class="flex items-center justify-between pb-3 border-b mb-4">
                <h3 class="font-extrabold text-brandTeal text-base"><i class="fa-solid fa-user-nurse mr-1"></i> Tambah Perawat Baru</h3>
                <button onclick="closeModal('modalPerawat')" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="formPerawat" onsubmit="event.preventDefault(); savePerawat();" class="space-y-3 text-xs">
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Nama Lengkap & Gelar <span class="text-red-500">*</span></label>
                    <input type="text" id="nNama" required placeholder="Contoh: Ns. Ani Wijaya, S.Kep" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                </div>
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Spesialisasi / Keahlian <span class="text-red-500">*</span></label>
                    <input type="text" id="nSpesialis" required placeholder="Contoh: Perawatan Lansia & Medis General" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block font-bold text-slate-700 mb-1">Nomor Telepon / WA <span class="text-red-500">*</span></label>
                        <input type="text" id="nKontak" required placeholder="0813xxxxxxx" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                    </div>
                    <div>
                        <label class="block font-bold text-slate-700 mb-1">Status Tugas</label>
                        <select id="nStatus" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                            <option value="On-Duty">On-Duty (Tersedia)</option>
                            <option value="In-Service">In-Service (Bertugas)</option>
                            <option value="Off">Off (Cuti/Izin)</option>
                        </select>
                    </div>
                </div>
                <div class="pt-3 flex justify-end gap-2">
                    <button type="button" onclick="closeModal('modalPerawat')" class="px-4 py-2 bg-slate-200 text-slate-700 font-bold rounded-lg">Batal</button>
                    <button type="submit" class="px-4 py-2 bg-brandTeal text-white font-bold rounded-lg hover:bg-teal-900">Simpan Perawat</button>
                </div>
            </form>
        </div>
    </div>

    <!-- 3. MODAL TAMBAH LAYANAN -->
    <div id="modalLayanan" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm hidden items-center justify-center z-50 p-4 overflow-y-auto">
        <div class="bg-white rounded-2xl shadow-2xl max-w-lg w-full p-6 border-t-4 border-indigo-600">
            <div class="flex items-center justify-between pb-3 border-b mb-4">
                <h3 class="font-extrabold text-indigo-700 text-base"><i class="fa-solid fa-hand-holding-medical mr-1"></i> Tambah Layanan Baru</h3>
                <button onclick="closeModal('modalLayanan')" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="formLayanan" onsubmit="event.preventDefault(); saveLayanan();" class="space-y-3 text-xs">
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Nama Layanan <span class="text-red-500">*</span></label>
                    <input type="text" id="lNama" required placeholder="Contoh: Fisioterapi Pendampingan" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                </div>
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Deskripsi Layanan <span class="text-red-500">*</span></label>
                    <textarea id="lDeskripsi" rows="3" required placeholder="Deskripsi ringkas cakupan perawatan..." class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5"></textarea>
                </div>
                <div class="pt-3 flex justify-end gap-2">
                    <button type="button" onclick="closeModal('modalLayanan')" class="px-4 py-2 bg-slate-200 text-slate-700 font-bold rounded-lg">Batal</button>
                    <button type="submit" class="px-4 py-2 bg-indigo-600 text-white font-bold rounded-lg hover:bg-indigo-800">Simpan Layanan</button>
                </div>
            </form>
        </div>
    </div>

    <!-- 4. MODAL TAMBAH TARIF MASTER -->
    <div id="modalTarif" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm hidden items-center justify-center z-50 p-4 overflow-y-auto">
        <div class="bg-white rounded-2xl shadow-2xl max-w-lg w-full p-6 border-t-4 border-amber-500">
            <div class="flex items-center justify-between pb-3 border-b mb-4">
                <h3 class="font-extrabold text-amber-700 text-base"><i class="fa-solid fa-tags mr-1"></i> Tambah Tarif Layanan</h3>
                <button onclick="closeModal('modalTarif')" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="formTarif" onsubmit="event.preventDefault(); saveTarif();" class="space-y-3 text-xs">
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Nama Paket Layanan <span class="text-red-500">*</span></label>
                    <input type="text" id="tNama" required placeholder="Contoh: Paket Visit Perawat 2 Jam" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block font-bold text-slate-700 mb-1">Durasi / Satuan <span class="text-red-500">*</span></label>
                        <input type="text" id="tDurasi" required placeholder="Per Visit / 12 Jam" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                    </div>
                    <div>
                        <label class="block font-bold text-slate-700 mb-1">Harga Tarif (Rp) <span class="text-red-500">*</span></label>
                        <input type="number" id="tHarga" required placeholder="300000" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                    </div>
                </div>
                <div class="pt-3 flex justify-end gap-2">
                    <button type="button" onclick="closeModal('modalTarif')" class="px-4 py-2 bg-slate-200 text-slate-700 font-bold rounded-lg">Batal</button>
                    <button type="submit" class="px-4 py-2 bg-amber-600 text-white font-bold rounded-lg hover:bg-amber-800">Simpan Tarif</button>
                </div>
            </form>
        </div>
    </div>

    <!-- 5. MODAL TAMBAH USER -->
    <div id="modalUser" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm hidden items-center justify-center z-50 p-4 overflow-y-auto">
        <div class="bg-white rounded-2xl shadow-2xl max-w-lg w-full p-6 border-t-4 border-brandBlue">
            <div class="flex items-center justify-between pb-3 border-b mb-4">
                <h3 class="font-extrabold text-brandBlue text-base"><i class="fa-solid fa-user-gear mr-1"></i> Tambah Pengguna Portal Baru</h3>
                <button onclick="closeModal('modalUser')" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="formUser" onsubmit="event.preventDefault(); saveUser();" class="space-y-3 text-xs">
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Nama Lengkap Staff <span class="text-red-500">*</span></label>
                    <input type="text" id="uNama" required placeholder="Contoh: Sarah Amelia, A.Md" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block font-bold text-slate-700 mb-1">Username <span class="text-red-500">*</span></label>
                        <input type="text" id="uUsername" required placeholder="sarah_nurse" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                    </div>
                    <div>
                        <label class="block font-bold text-slate-700 mb-1">Role / Hak Akses <span class="text-red-500">*</span></label>
                        <select id="uRole" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                            <option value="Administrator">Administrator</option>
                            <option value="Perawat On-Duty">Perawat On-Duty</option>
                            <option value="Supervisor Medis">Supervisor Medis</option>
                            <option value="Keuangan & Laporan">Keuangan & Laporan</option>
                        </select>
                    </div>
                </div>
                <div class="pt-3 flex justify-end gap-2">
                    <button type="button" onclick="closeModal('modalUser')" class="px-4 py-2 bg-slate-200 text-slate-700 font-bold rounded-lg">Batal</button>
                    <button type="submit" class="px-4 py-2 bg-brandBlue text-white font-bold rounded-lg hover:bg-indigo-900">Simpan User</button>
                </div>
            </form>
        </div>
    </div>

<!-- MODAL TAMBAH INFORMASI / PENGUMUMAN -->
<div id="modalInformasi" class="fixed inset-0 z-50 hidden overflow-y-auto bg-slate-900/60 p-4 backdrop-blur-sm items-center justify-center">
    <div class="w-full max-w-lg rounded-2xl border-t-4 border-amber-500 bg-white p-6 shadow-2xl">
        
        <!-- Header Modal -->
        <div class="mb-4 flex items-center justify-between border-b pb-3">
            <h3 class="text-base font-extrabold text-amber-700">
                <i class="fa-solid fa-bullhorn mr-1.5"></i> Tambah Informasi / Pengumuman Baru
            </h3>
            <button type="button" onclick="closeModal('modalInformasi')" class="text-slate-400 hover:text-slate-600 transition-colors">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>
        </div>

        <!-- Form Input -->
        <form id="formInformasi" onsubmit="event.preventDefault(); saveInformasi();" class="space-y-3 text-xs">
            <div>
                <label for="infoJudul" class="mb-1 block font-bold text-slate-700">
                    Judul Informasi <span class="text-red-500">*</span>
                </label>
                <input type="text" id="infoJudul" required placeholder="Contoh: Perluasan Layanan Perawatan Lansia" class="w-full rounded-lg border border-slate-300 bg-slate-50 p-2.5 text-slate-800 focus:border-amber-500 focus:outline-none focus:ring-1 focus:ring-amber-500">
            </div>

            <div>
                <label for="infoKategori" class="mb-1 block font-bold text-slate-700">
                    Kategori <span class="text-red-500">*</span>
                </label>
                <select id="infoKategori" required class="w-full rounded-lg border border-slate-300 bg-slate-50 p-2.5 text-slate-800 focus:border-amber-500 focus:outline-none focus:ring-1 focus:ring-amber-500">
                    <option value="Pengumuman">Pengumuman Internal</option>
                    <option value="Layanan">Update Layanan</option>
                    <option value="Kesehatan">Tips & Edukasi Kesehatan</option>
                </select>
            </div>

            <!-- Input Upload / Link Foto -->
            <div>
                <label for="infoFoto" class="mb-1 block font-bold text-slate-700">
                    Lampiran Foto <span class="text-slate-400 font-normal">(Opsional)</span>
                </label>
                <input type="file" id="infoFoto" accept="file:///C:/Users/JAING/Desktop/Aplikasi%20The%20Bonding%20Cara/jaingggg.jpg/*" class="w-full rounded-lg border border-slate-300 bg-slate-50 p-2 text-slate-800 file:mr-3 file:rounded-md file:border-0 file:bg-amber-100 file:px-3 file:py-1 file:text-xs file:font-semibold file:text-amber-800 hover:file:bg-amber-200">
                <p class="mt-1 text-[10px] text-slate-500">Format: JPG, PNG, WebP (Maks. 2MB)</p>
            </div>

            <!-- Input Link Video -->
            <div>
                <label for="infoVideo" class="mb-1 block font-bold text-slate-700">
                    Link Video <span class="text-slate-400 font-normal">(Opsional)</span>
                </label>
                <div class="relative">
                    <span class="absolute inset-y-0 left-0 flex items-center pl-3 text-slate-400">
                        <i class="fa-solid fa-video"></i>
                    </span>
                    <input type="url" id="infoVideo" placeholder="https://www.youtube.com/watch?v=..." class="w-full rounded-lg border border-slate-300 bg-slate-50 p-2.5 pl-9 text-slate-800 focus:border-amber-500 focus:outline-none focus:ring-1 focus:ring-amber-500">
                </div>
            </div>

            <div>
                <label for="infoIsi" class="mb-1 block font-bold text-slate-700">
                    Isi Pesan / Informasi <span class="text-red-500">*</span>
                </label>
                <textarea id="infoIsi" rows="3" required placeholder="Tulis rincian informasi..." class="w-full rounded-lg border border-slate-300 bg-slate-50 p-2.5 text-slate-800 focus:border-amber-500 focus:outline-none focus:ring-1 focus:ring-amber-500"></textarea>
            </div>

            <!-- Tombol Aksi -->
            <div class="flex justify-end gap-2 pt-3">
                <button type="button" onclick="closeModal('modalInformasi')" class="rounded-lg bg-slate-200 px-4 py-2 font-bold text-slate-700 hover:bg-slate-300 transition-colors">
                    Batal
                </button>
                <button type="submit" class="rounded-lg bg-amber-600 px-4 py-2 font-bold text-white hover:bg-amber-700 transition-colors">
                    Publikasikan
                </button>
            </div>
        </form>

    </div>
</div>

    <!-- 7. MODAL INPUT MASTER DATA -->
    <div id="modalMasterData" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm hidden items-center justify-center z-50 p-4 overflow-y-auto">
        <div class="bg-white rounded-2xl shadow-2xl max-w-lg w-full p-6 border-t-4 border-brandTeal">
            <div class="flex items-center justify-between pb-3 border-b mb-4">
                <h3 class="font-extrabold text-brandTeal text-base"><i class="fa-solid fa-database mr-1"></i> Input Master Data Baru</h3>
                <button onclick="closeModal('modalMasterData')" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="formMasterData" onsubmit="event.preventDefault(); saveMasterData();" class="space-y-3 text-xs">
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Kategori Master Data <span class="text-red-500">*</span></label>
                    <select id="mKategori" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                        <option value="area">Area Coverage Layanan</option>
                        <option value="role">Hak Akses User (User Role)</option>
                    </select>
                </div>
                <div>
                    <label class="block font-bold text-slate-700 mb-1">Nilai Data Baru / Keterangan <span class="text-red-500">*</span></label>
                    <input type="text" id="mNilai" required placeholder="Contoh: Harapan Indah & Rawalumbu" class="w-full bg-slate-50 border border-slate-300 rounded-lg p-2.5">
                </div>
                <div class="pt-3 flex justify-end gap-2">
                    <button type="button" onclick="closeModal('modalMasterData')" class="px-4 py-2 bg-slate-200 text-slate-700 font-bold rounded-lg">Batal</button>
                    <button type="submit" class="px-4 py-2 bg-brandTeal text-white font-bold rounded-lg hover:bg-teal-900">Tambahkan Master</button>
                </div>
            </form>
        </div>
    </div>

    <!-- JAVASCRIPT LOGIC & STATE MANAGEMENT -->
    <script>
        const defaultPasien = [
            { id: 'BC-PAS-001', nama: 'Bpk. H. Sutrisno', umur: 68, jk: 'Laki-Laki', diagnosa: 'Stroke & Rehab Medik', kontak: '0812-8877-6655 (Anak)', alamat: 'Jaka Setia, Bekasi Selatan' },
            { id: 'BC-PAS-002', nama: 'Ibu Hj. Maryam', umur: 72, jk: 'Perempuan', diagnosa: 'Pendampingan Lansia / Demensia', kontak: '0813-1122-3344 (Suami)', alamat: 'Pondok Timur Mas, Bekasi' }
        ];

        const defaultPerawat = [
            { id: 'NRS-001', nama: 'Ns. Ani Wijaya, S.Kep', spesialis: 'Perawat Medis Senior & Lansia', kontak: '0812-3456-7890', status: 'On-Duty' },
            { id: 'NRS-002', nama: 'Ns. Budi Santoso, Amd.Kep', spesialis: 'Pendampingan Stroke & Fisioterapi', kontak: '0813-9876-5432', status: 'In-Service' }
        ];

        const defaultLayanan = [
            { id: 'LAY-001', nama: 'Pendampingan Lansia (Elderly Care)', deskripsi: 'Perawatan harian, bantuan aktivitas mandiri, serta interaksi emosional hangat untuk lansia.' },
            { id: 'LAY-002', nama: 'Perawatan Pasca Operasi / Medis', deskripsi: 'Perawatan luka, manajemen infus/obat, serta fisioterapi pendampingan pasca-rawat inap.' },
            { id: 'LAY-003', nama: 'Emotional Bonding Support', deskripsi: 'Terapi psikologis ringan, teman bicara, dan stimulasi memori untuk menjaga kesehatan mental pasien.' }
        ];

        const defaultTarif = [
            { kode: 'TRF-001', nama: 'Kunjungan Perawat Harian (Visit)', durasi: 'Per Visit (2 Jam)', harga: 250000 },
            { kode: 'TRF-002', nama: 'Pendampingan Lansia Standar (Shift)', durasi: '12 Jam / Hari', harga: 450000 },
            { kode: 'TRF-003', nama: 'Paket Intensive Home Care (Full Stay)', durasi: '24 Jam / Hari', harga: 750000 }
        ];

        const defaultBondingLogs = [
            { id: 'BND-101', waktu: '2026-10-03 09:00', pasienId: 'BC-PAS-001', pasienNama: 'Bpk. H. Sutrisno', perawatNama: 'Ns. Ani Wijaya, S.Kep', emosi: 'Sangat Kooperatif & Ceria', td: '130/80', nadi: '78', suhu: '36.6', spo2: '98', catatan: 'Pasien terlihat gembira saat latihan pergerakan tangan. Komunikasi berjalan sangat harmonis.' },
            { id: 'BND-102', waktu: '2026-10-02 14:30', pasienId: 'BC-PAS-002', pasienNama: 'Ibu Hj. Maryam', perawatNama: 'Ns. Budi Santoso, Amd.Kep', emosi: 'Tenang & Nyaman', td: '120/75', nadi: '82', suhu: '36.4', spo2: '99', catatan: 'Pasien telah minum obat sore tepat waktu. Didampingi saat minum teh hangat.' }
        ];

        const defaultUsers = [
            { id: 'USR-001', nama: 'Administrator Sistem', username: 'admin', role: 'Administrator', status: 'Aktif' },
            { id: 'USR-002', nama: 'Ns. Ani Wijaya, S.Kep', username: 'ani_nurse', role: 'Perawat On-Duty', status: 'Aktif' },
            { id: 'USR-003', nama: 'Dr. Hendra Saputra', username: 'hendra_supervisor', role: 'Supervisor Medis', status: 'Aktif' }
        ];

        const defaultInformasi = [
            { id: 'INF-001', judul: 'Standar Operasional Pendampingan Emotional Bonding', kategori: 'Pengumuman', tanggal: '2026-10-01', isi: 'Seluruh perawat diwajibkan mencatat perkembangan respon emosional pasien setiap kali selesai melakukan kunjungan.' },
            { id: 'INF-002', judul: 'Layanan Baru: Perawatan Pasca Rawat Inap & Fisioterapi', kategori: 'Layanan', tanggal: '2026-09-28', isi: 'The Bonding Care kini menyediakan modul fisioterapi geriatri terpadu untuk pasien lansia.' }
        ];

        const defaultAreaCoverage = [
            'Pondok Timur Mas & Jaka Setia',
            'Bekasi Selatan & Bekasi Barat',
            'Pekayon, Galaxi, & Kemang Pratama',
            'Caman & Jatibening'
        ];

        const defaultUserRoles = [
            '<b>Super Admin:</b> Full Access (Kelola Pasien, Perawat, Tarif & Laporan)',
            '<b>Perawat/Nurse:</b> Akses Input Jurnal Bonding & Lihat Profil Pasien',
            '<b>Keuangan:</b> Akses Master Tarif & Export Laporan'
        ];

        let pasienList = JSON.parse(localStorage.getItem('bc_pasien')) || defaultPasien;
        let perawatList = JSON.parse(localStorage.getItem('bc_perawat')) || defaultPerawat;
        let layananList = JSON.parse(localStorage.getItem('bc_layanan')) || defaultLayanan;
        let tarifList = JSON.parse(localStorage.getItem('bc_tarif')) || defaultTarif;
        let bondingLogs = JSON.parse(localStorage.getItem('bc_bonding')) || defaultBondingLogs;
        let userList = JSON.parse(localStorage.getItem('bc_users')) || defaultUsers;
        let informasiList = JSON.parse(localStorage.getItem('bc_informasi')) || defaultInformasi;
        let areaCoverageList = JSON.parse(localStorage.getItem('bc_area_coverage')) || defaultAreaCoverage;
        let userRoleList = JSON.parse(localStorage.getItem('bc_user_roles')) || defaultUserRoles;

        function saveAllState() {
            localStorage.setItem('bc_pasien', JSON.stringify(pasienList));
            localStorage.setItem('bc_perawat', JSON.stringify(perawatList));
            localStorage.setItem('bc_layanan', JSON.stringify(layananList));
            localStorage.setItem('bc_tarif', JSON.stringify(tarifList));
            localStorage.setItem('bc_bonding', JSON.stringify(bondingLogs));
            localStorage.setItem('bc_users', JSON.stringify(userList));
            localStorage.setItem('bc_informasi', JSON.stringify(informasiList));
            localStorage.setItem('bc_area_coverage', JSON.stringify(areaCoverageList));
            localStorage.setItem('bc_user_roles', JSON.stringify(userRoleList));
            updateDashboardStats();
        }

        function handleLogin() {
            const u = document.getElementById('username').value.trim();
            const p = document.getElementById('password').value.trim();
            const err = document.getElementById('loginError');

            if (u === 'admin' && p === 'admin123') {
                sessionStorage.setItem('bc_authenticated', 'true');
                document.getElementById('loginModal').classList.add('hidden');
                document.getElementById('appContainer').classList.remove('hidden');
                document.getElementById('appContainer').classList.add('flex');
                initApp();
            } else {
                err.classList.remove('hidden');
            }
        }

        function handleLogout() {
            sessionStorage.removeItem('bc_authenticated');
            document.getElementById('appContainer').classList.add('hidden');
            document.getElementById('loginModal').classList.remove('hidden');
        }

        function checkSession() {
            if (sessionStorage.getItem('bc_authenticated') === 'true') {
                document.getElementById('loginModal').classList.add('hidden');
                document.getElementById('appContainer').classList.remove('hidden');
                document.getElementById('appContainer').classList.add('flex');
                initApp();
            }
        }

        function switchTab(tabName) {
            const pages = document.querySelectorAll('.page-content');
            pages.forEach(p => p.classList.add('hidden'));

            const targetPage = document.getElementById('page-' + tabName);
            if (targetPage) targetPage.classList.remove('hidden');

            const navBtns = document.querySelectorAll('.nav-btn');
            navBtns.forEach(btn => {
                btn.classList.remove('bg-brandBlue', 'text-white');
                btn.classList.add('hover:bg-slate-100', 'text-slate-600');
            });

            const activeBtn = document.getElementById('btn-' + tabName);
            if (activeBtn) {
                activeBtn.classList.remove('hover:bg-slate-100', 'text-slate-600');
                activeBtn.classList.add('bg-brandBlue', 'text-white');
            }
        }

        function openModal(modalId) {
            document.getElementById(modalId).classList.remove('hidden');
            document.getElementById(modalId).classList.add('flex');
        }

        function closeModal(modalId) {
            document.getElementById(modalId).classList.add('hidden');
            document.getElementById(modalId).classList.remove('flex');
        }

        function initApp() {
            updateDashboardStats();
            renderPasienTable();
            renderPerawatGrid();
            renderLayananGrid();
            renderTarifTable();
            renderLaporanTable();
            renderUserTable();
            renderInformasiCards();
            renderMasterDataLists();
            populateFormSelects();
            setInitialDateTime();
        }

        function setInitialDateTime() {
            const now = new Date();
            now.setMinutes(now.getMinutes() - now.getTimezoneOffset());
            document.getElementById('bondTanggal').value = now.toISOString().slice(0, 16);
        }

        function updateDashboardStats() {
            document.getElementById('stat-pasien').innerText = pasienList.length;
            document.getElementById('stat-perawat').innerText = perawatList.length;
            document.getElementById('stat-bonding').innerText = bondingLogs.length;
            document.getElementById('stat-layanan').innerText = layananList.length;

            const recentContainer = document.getElementById('dashboardRecentLogs');
            if (bondingLogs.length === 0) {
                recentContainer.innerHTML = `<p class="text-xs text-slate-400 italic">Belum ada catatan bonding.</p>`;
                return;
            }

            recentContainer.innerHTML = bondingLogs.slice(0, 5).map(log => `
                <div class="p-3 bg-slate-50 rounded-xl border border-slate-100 space-y-1">
                    <div class="flex items-center justify-between">
                        <span class="font-bold text-xs text-brandBlue">${escapeHtml(log.pasienNama)}</span>
                        <span class="text-[10px] text-slate-400">${escapeHtml(log.waktu)}</span>
                    </div>
                    <p class="text-xs text-slate-600 line-clamp-2">"${escapeHtml(log.catatan)}"</p>
                    <div class="flex items-center justify-between pt-1">
                        <span class="text-[10px] text-brandTeal font-semibold"><i class="fa-solid fa-user-nurse mr-1"></i>${escapeHtml(log.perawatNama)}</span>
                        <span class="text-[10px] bg-amber-100 text-amber-800 px-2 py-0.5 rounded-full font-bold">${escapeHtml(log.emosi)}</span>
                    </div>
                </div>
            `).join('');
        }

        function populateFormSelects() {
            const pSelect = document.getElementById('bondPasienSelect');
            pSelect.innerHTML = pasienList.map(p => `<option value="${p.id}">${p.id} - ${p.nama}</option>`).join('');

            const nSelect = document.getElementById('bondPerawatSelect');
            nSelect.innerHTML = perawatList.map(n => `<option value="${n.nama}">${n.nama}</option>`).join('');
        }

        function renderPasienTable() {
            const q = document.getElementById('searchPasien').value.toLowerCase();
            const tbody = document.getElementById('tablePasienBody');
            
            const filtered = pasienList.filter(p => 
                p.nama.toLowerCase().includes(q) || 
                p.diagnosa.toLowerCase().includes(q) || 
                p.alamat.toLowerCase().includes(q)
            );

            if (filtered.length === 0) {
                tbody.innerHTML = `<tr><td colspan="7" class="p-4 text-center text-slate-400 italic">Tidak ada data pasien ditemukan.</td></tr>`;
                return;
            }

            tbody.innerHTML = filtered.map(p => `
                <tr class="hover:bg-slate-50 transition">
                    <td class="p-3 font-bold text-brandBlue">${p.id}</td>
                    <td class="p-3 font-semibold text-slate-800">${escapeHtml(p.nama)}</td>
                    <td class="p-3">${p.umur} Thn / ${p.jk}</td>
                    <td class="p-3"><span class="bg-blue-50 text-brandBlue px-2 py-0.5 rounded font-medium">${escapeHtml(p.diagnosa)}</span></td>
                    <td class="p-3 text-slate-600">${escapeHtml(p.kontak)}</td>
                    <td class="p-3 text-slate-500 max-w-xs truncate">${escapeHtml(p.alamat)}</td>
                    <td class="p-3 text-center">
                        <button onclick="deletePasien('${p.id}')" class="text-rose-600 hover:text-rose-800 font-bold"><i class="fa-solid fa-trash-can"></i></button>
                    </td>
                </tr>
            `).join('');
        }

        function savePasien() {
            const newId = 'BC-PAS-' + String(pasienList.length + 1).padStart(3, '0');
            const newP = {
                id: newId,
                nama: document.getElementById('pNama').value.trim(),
                umur: document.getElementById('pUmur').value,
                jk: document.getElementById('pJK').value,
                diagnosa: document.getElementById('pDiagnosa').value.trim(),
                kontak: document.getElementById('pKontak').value.trim(),
                alamat: document.getElementById('pAlamat').value.trim()
            };

            pasienList.push(newP);
            saveAllState();
            renderPasienTable();
            populateFormSelects();
            closeModal('modalPasien');
            document.getElementById('formPasien').reset();
        }

        function deletePasien(id) {
            if (confirm('Apakah Anda yakin ingin menghapus data pasien ini?')) {
                pasienList = pasienList.filter(p => p.id !== id);
                saveAllState();
                renderPasienTable();
                populateFormSelects();
            }
        }

        function renderPerawatGrid() {
            const grid = document.getElementById('gridPerawat');
            if (perawatList.length === 0) {
                grid.innerHTML = `<p class="text-xs text-slate-400 italic">Belum ada perawat terdaftar.</p>`;
                return;
            }

            grid.innerHTML = perawatList.map(n => `
                <div class="border border-slate-200 rounded-2xl p-5 bg-white shadow-sm flex flex-col justify-between hover:shadow-md transition">
                    <div>
                        <div class="flex items-center justify-between mb-3">
                            <span class="text-xs font-bold bg-slate-100 text-slate-600 px-2.5 py-0.5 rounded-full">${n.id}</span>
                            <span class="text-[10px] font-bold px-2 py-0.5 rounded-full ${n.status === 'On-Duty' ? 'bg-emerald-100 text-emerald-800' : n.status === 'In-Service' ? 'bg-blue-100 text-blue-800' : 'bg-slate-100 text-slate-600'}">
                                ${n.status}
                            </span>
                        </div>
                        <h4 class="font-bold text-slate-800 text-base mb-1">${escapeHtml(n.nama)}</h4>
                        <p class="text-xs text-brandTeal font-semibold mb-2"><i class="fa-solid fa-stethoscope mr-1"></i> ${escapeHtml(n.spesialis)}</p>
                        <p class="text-xs text-slate-500 mb-4"><i class="fa-brands fa-whatsapp text-emerald-600 mr-1"></i> ${escapeHtml(n.kontak)}</p>
                    </div>
                    <div class="pt-3 border-t border-slate-100 flex justify-end">
                        <button onclick="deletePerawat('${n.id}')" class="text-xs text-rose-600 hover:text-rose-800 font-bold flex items-center gap-1">
                            <i class="fa-solid fa-trash-can"></i> Hapus
                        </button>
                    </div>
                </div>
            `).join('');
        }

        function savePerawat() {
            const newId = 'NRS-' + String(perawatList.length + 1).padStart(3, '0');
            const newN = {
                id: newId,
                nama: document.getElementById('nNama').value.trim(),
                spesialis: document.getElementById('nSpesialis').value.trim(),
                kontak: document.getElementById('nKontak').value.trim(),
                status: document.getElementById('nStatus').value
            };

            perawatList.push(newN);
            saveAllState();
            renderPerawatGrid();
            populateFormSelects();
            closeModal('modalPerawat');
            document.getElementById('formPerawat').reset();
        }

        function deletePerawat(id) {
            if (confirm('Apakah Anda yakin menghapus data perawat ini?')) {
                perawatList = perawatList.filter(n => n.id !== id);
                saveAllState();
                renderPerawatGrid();
                populateFormSelects();
            }
        }

        function saveBondingLog() {
            const pasId = document.getElementById('bondPasienSelect').value;
            const pasObj = pasienList.find(p => p.id === pasId);
            
            const newLog = {
                id: 'BND-' + Date.now().toString().slice(-4),
                waktu: document.getElementById('bondTanggal').value.replace('T', ' '),
                pasienId: pasId,
                pasienNama: pasObj ? pasObj.nama : 'Pasien',
                perawatNama: document.getElementById('bondPerawatSelect').value,
                emosi: document.getElementById('bondEmosi').value,
                td: document.getElementById('bondTD').value || '-',
                nadi: document.getElementById('bondNadi').value || '-',
                suhu: document.getElementById('bondSuhu').value || '-',
                spo2: document.getElementById('bondSPO2').value || '-',
                catatan: document.getElementById('bondCatatan').value.trim()
            };

            bondingLogs.unshift(newLog);
            saveAllState();
            renderLaporanTable();
            document.getElementById('formBonding').reset();
            setInitialDateTime();
            alert('Catatan Jurnal Bonding berhasil disimpan!');
            switchTab('laporan');
        }

        function renderLayananGrid() {
            const grid = document.getElementById('gridLayanan');
            grid.innerHTML = layananList.map(l => `
                <div class="border border-slate-200 rounded-2xl p-5 bg-white shadow-sm flex flex-col justify-between">
                    <div>
                        <div class="text-brandBlue text-3xl mb-3"><i class="fa-solid fa-hand-holding-medical"></i></div>
                        <h3 class="font-extrabold text-slate-800 text-base mb-2">${escapeHtml(l.nama)}</h3>
                        <p class="text-xs text-slate-600 leading-relaxed mb-4">${escapeHtml(l.deskripsi)}</p>
                    </div>
                    <div class="pt-3 border-t border-slate-100 flex justify-end">
                        <button onclick="deleteLayanan('${l.id}')" class="text-xs text-rose-600 hover:text-rose-800 font-bold"><i class="fa-solid fa-trash-can"></i> Hapus</button>
                    </div>
                </div>
            `).join('');
        }

        function saveLayanan() {
            const newL = {
                id: 'LAY-' + String(layananList.length + 1).padStart(3, '0'),
                nama: document.getElementById('lNama').value.trim(),
                deskripsi: document.getElementById('lDeskripsi').value.trim()
            };
            layananList.push(newL);
            saveAllState();
            renderLayananGrid();
            closeModal('modalLayanan');
            document.getElementById('formLayanan').reset();
        }

        function deleteLayanan(id) {
            if (confirm('Hapus layanan ini?')) {
                layananList = layananList.filter(l => l.id !== id);
                saveAllState();
                renderLayananGrid();
            }
        }

        function renderTarifTable() {
            const tbody = document.getElementById('tableTarifBody');
            tbody.innerHTML = tarifList.map(t => `
                <tr class="hover:bg-slate-50 transition">
                    <td class="p-3 font-bold text-slate-700">${t.kode}</td>
                    <td class="p-3 font-semibold text-slate-800">${escapeHtml(t.nama)}</td>
                    <td class="p-3 text-slate-600">${escapeHtml(t.durasi)}</td>
                    <td class="p-3 font-extrabold text-emerald-700">Rp ${Number(t.harga).toLocaleString('id-ID')}</td>
                    <td class="p-3 text-center">
                        <button onclick="deleteTarif('${t.kode}')" class="text-rose-600 hover:text-rose-800 font-bold"><i class="fa-solid fa-trash-can"></i></button>
                    </td>
                </tr>
            `).join('');
        }

        function saveTarif() {
            const newT = {
                kode: 'TRF-' + String(tarifList.length + 1).padStart(3, '0'),
                nama: document.getElementById('tNama').value.trim(),
                durasi: document.getElementById('tDurasi').value.trim(),
                harga: parseInt(document.getElementById('tHarga').value) || 0
            };
            tarifList.push(newT);
            saveAllState();
            renderTarifTable();
            closeModal('modalTarif');
            document.getElementById('formTarif').reset();
        }

        function deleteTarif(kode) {
            if (confirm('Hapus tarif ini?')) {
                tarifList = tarifList.filter(t => t.kode !== kode);
                saveAllState();
                renderTarifTable();
            }
        }

        function renderUserTable() {
            const tbody = document.getElementById('tableUserBody');
            if (userList.length === 0) {
                tbody.innerHTML = `<tr><td colspan="6" class="p-4 text-center text-slate-400 italic">Belum ada user registered.</td></tr>`;
                return;
            }

            tbody.innerHTML = userList.map(u => `
                <tr class="hover:bg-slate-50 transition">
                    <td class="p-3 font-bold text-brandBlue">${u.id}</td>
                    <td class="p-3 font-semibold text-slate-800">${escapeHtml(u.nama)}</td>
                    <td class="p-3 font-mono text-slate-600">${escapeHtml(u.username)}</td>
                    <td class="p-3"><span class="bg-indigo-50 text-indigo-700 px-2 py-0.5 rounded font-bold">${escapeHtml(u.role)}</span></td>
                    <td class="p-3"><span class="bg-emerald-100 text-emerald-800 text-[10px] font-bold px-2 py-0.5 rounded-full">${escapeHtml(u.status)}</span></td>
                    <td class="p-3 text-center">
                        <button onclick="deleteUser('${u.id}')" class="text-rose-600 hover:text-rose-800 font-bold"><i class="fa-solid fa-trash-can"></i></button>
                    </td>
                </tr>
            `).join('');
        }

        function saveUser() {
            const newU = {
                id: 'USR-' + String(userList.length + 1).padStart(3, '0'),
                nama: document.getElementById('uNama').value.trim(),
                username: document.getElementById('uUsername').value.trim(),
                role: document.getElementById('uRole').value,
                status: 'Aktif'
            };
            userList.push(newU);
            saveAllState();
            renderUserTable();
            closeModal('modalUser');
            document.getElementById('formUser').reset();
        }

        function deleteUser(id) {
            if (confirm('Hapus pengguna ini?')) {
                userList = userList.filter(u => u.id !== id);
                saveAllState();
                renderUserTable();
            }
        }

        function renderInformasiCards() {
            const container = document.getElementById('containerInformasi');
            if (informasiList.length === 0) {
                container.innerHTML = `<p class="text-xs text-slate-400 italic">Belum ada pengumuman terbaru.</p>`;
                return;
            }

            container.innerHTML = informasiList.map(info => `
                <div class="bg-slate-50 p-5 rounded-2xl border border-slate-200 flex flex-col justify-between">
                    <div>
                        <div class="flex items-center justify-between mb-2">
                            <span class="text-[10px] font-bold bg-amber-100 text-amber-800 px-2.5 py-0.5 rounded-full">${escapeHtml(info.kategori)}</span>
                            <span class="text-[10px] text-slate-400">${escapeHtml(info.tanggal)}</span>
                        </div>
                        <h4 class="font-extrabold text-slate-800 text-sm mb-2">${escapeHtml(info.judul)}</h4>
                        <p class="text-xs text-slate-600 leading-relaxed mb-4">${escapeHtml(info.isi)}</p>
                    </div>
                    <div class="pt-2 border-t border-slate-200 flex justify-end">
                        <button onclick="deleteInformasi('${info.id}')" class="text-xs text-rose-600 hover:text-rose-800 font-bold"><i class="fa-solid fa-trash-can"></i> Hapus</button>
                    </div>
                </div>
            `).join('');
        }

        function saveInformasi() {
            const today = new Date().toISOString().slice(0, 10);
            const newInf = {
                id: 'INF-' + String(informasiList.length + 1).padStart(3, '0'),
                judul: document.getElementById('infoJudul').value.trim(),
                kategori: document.getElementById('infoKategori').value,
                tanggal: today,
                isi: document.getElementById('infoIsi').value.trim()
            };
            informasiList.unshift(newInf);
            saveAllState();
            renderInformasiCards();
            closeModal('modalInformasi');
            document.getElementById('formInformasi').reset();
        }

        function deleteInformasi(id) {
            if (confirm('Hapus informasi ini?')) {
                informasiList = informasiList.filter(i => i.id !== id);
                saveAllState();
                renderInformasiCards();
            }
        }

        function renderMasterDataLists() {
            const areaUl = document.getElementById('listAreaCoverage');
            areaUl.innerHTML = areaCoverageList.map(a => `<li>${escapeHtml(a)}</li>`).join('');

            const roleUl = document.getElementById('listUserRoles');
            roleUl.innerHTML = userRoleList.map(r => `<li>${r}</li>`).join('');
        }

        function saveMasterData() {
            const kat = document.getElementById('mKategori').value;
            const val = document.getElementById('mNilai').value.trim();

            if (kat === 'area') {
                areaCoverageList.push(val);
            } else if (kat === 'role') {
                userRoleList.push(`<b>${escapeHtml(val)}:</b> Custom Role`);
            }

            saveAllState();
            renderMasterDataLists();
            closeModal('modalMasterData');
            document.getElementById('formMasterData').reset();
            alert('Master Data berhasil ditambahkan!');
        }

        function renderLaporanTable() {
            const q = document.getElementById('reportSearch').value.toLowerCase();
            const filterEmosi = document.getElementById('reportFilterEmosi').value;
            const tbody = document.getElementById('tableLaporanBody');

            const filtered = bondingLogs.filter(log => {
                const matchQ = log.pasienNama.toLowerCase().includes(q) || log.perawatNama.toLowerCase().includes(q) || log.catatan.toLowerCase().includes(q);
                const matchEmosi = filterEmosi === '' || log.emosi === filterEmosi;
                return matchQ && matchEmosi;
            });

            if (filtered.length === 0) {
                tbody.innerHTML = `<tr><td colspan="7" class="p-4 text-center text-slate-400 italic">Tidak ada catatan laporan ditemukan.</td></tr>`;
                return;
            }

            tbody.innerHTML = filtered.map(log => `
                <tr class="hover:bg-slate-50 transition">
                    <td class="p-3 font-semibold text-slate-600">${escapeHtml(log.waktu)}</td>
                    <td class="p-3 font-bold text-brandBlue">${escapeHtml(log.pasienNama)}</td>
                    <td class="p-3 font-medium text-slate-700">${escapeHtml(log.perawatNama)}</td>
                    <td class="p-3 text-[11px] text-slate-600">
                        TD: ${log.td} | HR: ${log.nadi} | T: ${log.suhu}°C | SpO2: ${log.spo2}%
                    </td>
                    <td class="p-3"><span class="bg-amber-100 text-amber-800 text-[10px] font-bold px-2 py-0.5 rounded-full">${escapeHtml(log.emosi)}</span></td>
                    <td class="p-3 text-slate-600 max-w-xs">${escapeHtml(log.catatan)}</td>
                    <td class="p-3 text-center">
                        <button onclick="deleteBondingLog('${log.id}')" class="text-rose-600 hover:text-rose-800 font-bold"><i class="fa-solid fa-trash-can"></i></button>
                    </td>
                </tr>
            `).join('');
        }

        function resetLaporanFilter() {
            document.getElementById('reportSearch').value = '';
            document.getElementById('reportFilterEmosi').value = '';
            renderLaporanTable();
        }

        function deleteBondingLog(id) {
            if (confirm('Hapus catatan laporan ini?')) {
                bondingLogs = bondingLogs.filter(b => b.id !== id);
                saveAllState();
                renderLaporanTable();
            }
        }

        function exportReportToCSV() {
            if (bondingLogs.length === 0) {
                alert('Tidak ada data laporan untuk di-export.');
                return;
            }

            let csvContent = "data:text/csv;charset=utf-8,ID,Waktu,Pasien,Perawat,Respon Emosi,TD,Nadi,Suhu,SPO2,Catatan\n";
            bondingLogs.forEach(l => {
                const row = [
                    l.id,
                    `"${l.waktu}"`,
                    `"${l.pasienNama}"`,
                    `"${l.perawatNama}"`,
                    `"${l.emosi}"`,
                    `"${l.td}"`,
                    `"${l.nadi}"`,
                    `"${l.suhu}"`,
                    `"${l.spo2}"`,
                    `"${l.catatan.replace(/"/g, '""')}"`
                ].join(",");
                csvContent += row + "\n";
            });

            const encodedUri = encodeURI(csvContent);
            const link = document.createElement("a");
            link.setAttribute("href", encodedUri);
            link.setAttribute("download", `Laporan_BondingCare_${new Date().toISOString().slice(0, 10)}.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }

        function escapeHtml(str) {
            if (!str) return '';
            return str.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;").replace(/"/g, "&quot;").replace(/'/g, "&#039;");
        }

        window.onload = function() {
            checkSession();
        };
    </script>
</body>
</html>
