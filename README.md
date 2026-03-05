# e.izin.bk
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>E-Izin SMAN 2 - Sistem Perizinan Keluar</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"/>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap');
        
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background: #f0f4f8;
            color: #1e293b;
        }

        .glass-morphism {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .gradient-bg {
            background: linear-gradient(135deg, #1e3a8a 0%, #3b82f6 100%);
        }

        .custom-shadow {
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
        }
    </style>
</head>
<body class="min-h-screen flex items-center justify-center p-4">

    <!-- Kontainer Utama -->
    <div id="app-container" class="w-full max-w-md animate__animated animate__fadeIn">
        
        <!-- HEADER SEKOLAH -->
        <div class="bg-white rounded-t-3xl p-6 text-center border-b border-gray-100 shadow-sm relative overflow-hidden">
            <div class="absolute top-0 right-0 p-4 opacity-10">
                <i data-lucide="school" class="w-20 h-20 text-blue-900"></i>
            </div>
            <div class="flex justify-center items-center gap-4 relative z-10">
                <img src="https://upload.wikimedia.org/wikipedia/commons/b/b2/Coat_of_arms_of_East_Java.svg" alt="Logo Jatim" class="h-14 drop-shadow-sm">
                <div class="h-12 w-[2px] bg-blue-100"></div>
                <div class="text-left">
                    <h1 class="text-2xl font-extrabold text-blue-900 leading-tight">SMAN 2</h1>
                    <p class="text-[10px] font-bold text-blue-500 uppercase tracking-[0.2em]">E-Izin Perizinan Digital</p>
                </div>
            </div>
        </div>

        <!-- AREA KONTEN UTAMA -->
        <div class="bg-white rounded-b-3xl p-8 custom-shadow min-h-[400px]">
            
            <!-- SECTION 1: LOGIN -->
            <div id="login-section" class="block">
                <h2 class="text-xl font-bold mb-1 text-gray-800">Selamat Datang</h2>
                <p class="text-sm text-gray-500 mb-8">Silahkan login dengan akun Anda</p>
                
                <div class="space-y-4">
                    <div class="relative">
                        <i data-lucide="user" class="absolute left-3 top-3 w-5 h-5 text-gray-400"></i>
                        <input type="text" id="username" placeholder="Username" class="w-full pl-10 pr-4 py-3 bg-gray-50 border border-gray-100 rounded-2xl focus:ring-2 focus:ring-blue-500 focus:bg-white outline-none transition-all">
                    </div>
                    <div class="relative">
                        <i data-lucide="lock" class="absolute left-3 top-3 w-5 h-5 text-gray-400"></i>
                        <input type="password" id="password" placeholder="Password" class="w-full pl-10 pr-4 py-3 bg-gray-50 border border-gray-100 rounded-2xl focus:ring-2 focus:ring-blue-500 focus:bg-white outline-none transition-all">
                    </div>
                    <button onclick="authAction()" class="w-full gradient-bg text-white font-bold py-4 rounded-2xl shadow-lg hover:opacity-90 transition transform active:scale-95 flex justify-center items-center gap-2 mt-4">
                        Masuk <i data-lucide="chevron-right" class="w-5 h-5"></i>
                    </button>
                    <p id="login-error" class="text-red-500 text-xs text-center mt-2 hidden">Username atau Password salah!</p>
                </div>
            </div>

            <!-- SECTION 2: DASHBOARD MURID -->
            <div id="student-section" class="hidden animate__animated animate__fadeIn">
                <div class="flex justify-between items-center mb-6">
                    <div>
                        <p class="text-xs text-gray-400">Halo Murid,</p>
                        <h2 id="display-student-name" class="text-lg font-bold text-gray-800">Nama Murid</h2>
                    </div>
                    <button onclick="logout()" class="p-2 text-red-400 hover:bg-red-50 rounded-full transition">
                        <i data-lucide="log-out" class="w-5 h-5"></i>
                    </button>
                </div>

                <!-- Formulir Pengajuan -->
                <div id="request-form-container">
                    <div class="bg-blue-50 p-4 rounded-2xl mb-6">
                        <p class="text-xs text-blue-700 font-semibold mb-2 flex items-center gap-1">
                            <i data-lucide="info" class="w-3 h-3"></i> Ketentuan Izin
                        </p>
                        <p class="text-[11px] text-blue-600 leading-relaxed">Pastikan alasan keluar jelas dan sudah mendapatkan izin guru mata pelajaran.</p>
                    </div>

                    <div class="space-y-4">
                        <div class="grid grid-cols-2 gap-3">
                            <input type="text" id="m-kelas" placeholder="Kelas" class="w-full p-3 bg-gray-50 rounded-xl border-none outline-none focus:ring-2 focus:ring-blue-500">
                            <input type="number" id="m-absen" placeholder="No. Absen" class="w-full p-3 bg-gray-50 rounded-xl border-none outline-none focus:ring-2 focus:ring-blue-500">
                        </div>
                        <div class="relative">
                            <label class="text-[10px] font-bold text-gray-400 uppercase ml-2">Estimasi Jam Keluar</label>
                            <input type="time" id="m-jam" class="w-full p-3 bg-gray-50 rounded-xl border-none outline-none focus:ring-2 focus:ring-blue-500">
                        </div>
                        <textarea id="m-alasan" placeholder="Alasan Keluar..." rows="3" class="w-full p-3 bg-gray-50 rounded-xl border-none outline-none focus:ring-2 focus:ring-blue-500"></textarea>
                        
                        <button onclick="submitPermit()" class="w-full bg-blue-600 text-white font-bold py-4 rounded-2xl shadow-md hover:bg-blue-700 transition">
                            Ajukan Izin Sekarang
                        </button>
                    </div>
                </div>

                <!-- Status Perizinan -->
                <div id="status-container" class="hidden py-4">
                    <div id="status-card" class="rounded-2xl p-6 text-center border-2 border-dashed border-gray-200">
                        <div id="status-icon" class="mb-4 flex justify-center text-yellow-500">
                            <i data-lucide="clock" class="w-12 h-12"></i>
                        </div>
                        <h3 id="status-title" class="text-lg font-bold mb-2">Menunggu Persetujuan</h3>
                        <p id="status-desc" class="text-sm text-gray-500 mb-6">Guru BK sedang memeriksa permintaan izin Anda. Mohon tunggu sejenak.</p>
                        
                        <div id="finish-action" class="hidden">
                            <div class="bg-green-50 p-4 rounded-xl mb-6 flex flex-col items-center gap-2">
                                <p class="text-xs text-green-700 font-bold">SILAHKAN KELUAR SEKOLAH</p>
                                <p class="text-[10px] text-green-600">Klik tombol di bawah jika Anda sudah kembali ke sekolah.</p>
                            </div>
                            <button onclick="completePermit()" class="w-full bg-gray-900 text-white font-bold py-4 rounded-2xl">
                                Selesai (Sudah Kembali)
                            </button>
                        </div>

                        <div id="denied-action" class="hidden">
                            <button onclick="resetForm()" class="w-full bg-red-100 text-red-600 font-bold py-4 rounded-2xl">
                                Buat Pengajuan Baru
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- SECTION 3: DASHBOARD ADMIN -->
            <div id="admin-section" class="hidden animate__animated animate__fadeIn">
                <div class="flex justify-between items-center mb-6">
                    <div>
                        <p class="text-xs text-gray-400">Panel Guru BK,</p>
                        <h2 id="display-admin-name" class="text-lg font-bold text-gray-800">Admin</h2>
                    </div>
                    <button onclick="logout()" class="p-2 text-red-400 hover:bg-red-50 rounded-full transition">
                        <i data-lucide="log-out" class="w-5 h-5"></i>
                    </button>
                </div>

                <!-- Tabs -->
                <div class="flex gap-2 mb-6">
                    <button onclick="switchAdminTab('pending')" id="tab-pending" class="flex-1 py-2 bg-blue-600 text-white rounded-xl text-xs font-bold">Pengajuan</button>
                    <button onclick="switchAdminTab('history')" id="tab-history" class="flex-1 py-2 bg-gray-100 text-gray-500 rounded-xl text-xs font-bold">Riwayat Log</button>
                </div>

                <div id="pending-list" class="space-y-4 max-h-[400px] overflow-y-auto pr-2">
                    <!-- Item List Pengajuan -->
                </div>

                <div id="history-list" class="hidden space-y-4 max-h-[400px] overflow-y-auto pr-2">
                    <!-- Item List Riwayat -->
                </div>
            </div>

        </div>

        <!-- FOOTER -->
        <p class="text-center text-white/60 text-[10px] mt-6 font-medium">© 2024 SMAN 2 - Smart School System</p>
    </div>

    <!-- MODAL NOTIFIKASI -->
    <div id="notification-modal" class="fixed inset-0 bg-black/50 hidden z-50 flex items-center justify-center p-6">
        <div class="bg-white rounded-3xl p-8 max-w-sm w-full text-center">
            <div id="modal-icon" class="flex justify-center mb-4"></div>
            <h3 id="modal-title" class="text-xl font-bold mb-2">Info</h3>
            <p id="modal-message" class="text-gray-500 text-sm mb-6"></p>
            <button onclick="closeModal()" class="w-full bg-blue-600 text-white py-3 rounded-xl font-bold">Mengerti</button>
        </div>
    </div>

    <script>
        // DATA MASTER (Sesuai Permintaan)
        const MASTER_ADMIN = [
            { user: "Guru BK 1", pass: "Admin123" },
            { user: "Guru BK 2", pass: "Admin123" }
        ];

        const MASTER_MURID = [
            { user: "Diemas Adji Prabowo", pass: "Diemas123" },
            { user: "Muhammad Nardi", pass: "Nardi123" },
            { user: "Nafaro", pass: "Nafa123" },
            { user: "Nindya Machdi", pass: "Nindya123" },
            { user: "Rabbani Paundra", pass: "Rabbani123" },
            { user: "Rizqi Aditya", pass: "Rizqi123" }
        ];

        // STATE MANAGEMENT
        let currentUser = null;
        let role = '';
        let permits = JSON.parse(localStorage.getItem('sman2_permits')) || [];

        // INITIALIZE ICONS
        lucide.createIcons();

        // 1. AUTHENTICATION
        function authAction() {
            const userIn = document.getElementById('username').value;
            const passIn = document.getElementById('password').value;
            const err = document.getElementById('login-error');

            const adminMatch = MASTER_ADMIN.find(a => a.user === userIn && a.pass === passIn);
            const muridMatch = MASTER_MURID.find(m => m.user === userIn && m.pass === passIn);

            if (adminMatch) {
                currentUser = adminMatch;
                role = 'admin';
                loginSuccess('admin-section', adminMatch.user);
            } else if (muridMatch) {
                currentUser = muridMatch;
                role = 'murid';
                loginSuccess('student-section', muridMatch.user);
                checkActivePermit();
            } else {
                err.classList.remove('hidden');
            }
        }

        function loginSuccess(sectionId, name) {
            document.getElementById('login-section').classList.add('hidden');
            document.getElementById(sectionId).classList.remove('hidden');
            if(role === 'admin') {
                document.getElementById('display-admin-name').innerText = name;
                renderAdminPending();
            } else {
                document.getElementById('display-student-name').innerText = name;
            }
            lucide.createIcons();
        }

        function logout() {
            location.reload();
        }

        // 2. MURID LOGIC
        function submitPermit() {
            const kelas = document.getElementById('m-kelas').value;
            const absen = document.getElementById('m-absen').value;
            const jam = document.getElementById('m-jam').value;
            const alasan = document.getElementById('m-alasan').value;

            if(!kelas || !absen || !jam || !alasan) {
                alertModal("Mohon lengkapi semua data perizinan.");
                return;
            }

            const newPermit = {
                id: Date.now(),
                nama: currentUser.user,
                kelas,
                absen,
                jamKeluar: jam,
                alasan,
                status: 'pending', // pending, approved, denied, finished
                waktuPengajuan: new Date().toLocaleString('id-ID'),
                waktuSelesai: null
            };

            permits.push(newPermit);
            saveData();
            checkActivePermit();
            alertModal("Berhasil!", "Permintaan izin Anda telah terkirim ke Guru BK.", "success");
        }

        function checkActivePermit() {
            const myActive = permits.find(p => p.nama === currentUser.user && p.status !== 'finished');
            
            if (myActive) {
                document.getElementById('request-form-container').classList.add('hidden');
                document.getElementById('status-container').classList.remove('hidden');
                updateStatusUI(myActive);
            } else {
                document.getElementById('request-form-container').classList.remove('hidden');
                document.getElementById('status-container').classList.add('hidden');
            }
        }

        function updateStatusUI(permit) {
            const card = document.getElementById('status-card');
            const icon = document.getElementById('status-icon');
            const title = document.getElementById('status-title');
            const desc = document.getElementById('status-desc');
            const actionFinish = document.getElementById('finish-action');
            const actionDenied = document.getElementById('denied-action');

            actionFinish.classList.add('hidden');
            actionDenied.classList.add('hidden');

            if (permit.status === 'pending') {
                icon.innerHTML = '<i data-lucide="clock" class="w-12 h-12"></i>';
                icon.className = "mb-4 flex justify-center text-yellow-500";
                title.innerText = "Menunggu Persetujuan";
                desc.innerText = "Guru BK sedang memeriksa permintaan izin Anda.";
            } else if (permit.status === 'approved') {
                icon.innerHTML = '<i data-lucide="check-circle" class="w-12 h-12"></i>';
                icon.className = "mb-4 flex justify-center text-green-500";
                title.innerText = "Izin Diberikan!";
                desc.innerText = "Anda diperbolehkan keluar sekolah. Jaga keselamatan diri.";
                actionFinish.classList.remove('hidden');
            } else if (permit.status === 'denied') {
                icon.innerHTML = '<i data-lucide="x-circle" class="w-12 h-12"></i>';
                icon.className = "mb-4 flex justify-center text-red-500";
                title.innerText = "Izin Ditolak";
                desc.innerText = "Maaf, permintaan izin Anda ditolak oleh Admin.";
                actionDenied.classList.remove('hidden');
            }
            lucide.createIcons();
        }

        function completePermit() {
            const idx = permits.findIndex(p => p.nama === currentUser.user && p.status === 'approved');
            if (idx !== -1) {
                permits[idx].status = 'finished';
                permits[idx].waktuSelesai = new Date().toLocaleString('id-ID');
                saveData();
                alertModal("Kembali!", "Status Anda telah diperbarui menjadi SUDAH KEMBALI di sistem.", "success");
                checkActivePermit();
            }
        }

        function resetForm() {
            const idx = permits.findIndex(p => p.nama === currentUser.user && p.status === 'denied');
            if (idx !== -1) {
                // Hapus yang ditolak dari riwayat aktif agar bisa buat baru (bisa juga di-arsip)
                permits[idx].status = 'finished'; // tandai saja agar tidak muncul di dashboard murid
                saveData();
                checkActivePermit();
            }
        }

        // 3. ADMIN LOGIC
        function switchAdminTab(tab) {
            const btnP = document.getElementById('tab-pending');
            const btnH = document.getElementById('tab-history');
            const listP = document.getElementById('pending-list');
            const listH = document.getElementById('history-list');

            if (tab === 'pending') {
                btnP.classList.replace('bg-gray-100', 'bg-blue-600');
                btnP.classList.replace('text-gray-500', 'text-white');
                btnH.classList.replace('bg-blue-600', 'bg-gray-100');
                btnH.classList.replace('text-white', 'text-gray-500');
                listP.classList.remove('hidden');
                listH.classList.add('hidden');
                renderAdminPending();
            } else {
                btnH.classList.replace('bg-gray-100', 'bg-blue-600');
                btnH.classList.replace('text-gray-500', 'text-white');
                btnP.classList.replace('bg-blue-600', 'bg-gray-100');
                btnP.classList.replace('text-white', 'text-gray-500');
                listH.classList.remove('hidden');
                listP.classList.add('hidden');
                renderAdminHistory();
            }
        }

        function renderAdminPending() {
            const list = document.getElementById('pending-list');
            const data = permits.filter(p => p.status === 'pending' || p.status === 'approved');
            
            if (data.length === 0) {
                list.innerHTML = `<div class="text-center py-10"><i data-lucide="inbox" class="w-10 h-10 mx-auto text-gray-200 mb-2"></i><p class="text-gray-400 text-xs">Belum ada pengajuan baru</p></div>`;
                lucide.createIcons();
                return;
            }

            list.innerHTML = data.map(p => `
                <div class="bg-gray-50 p-4 rounded-2xl border border-gray-100 animate__animated animate__fadeInUp">
                    <div class="flex justify-between items-start mb-2">
                        <div>
                            <h4 class="font-bold text-sm text-blue-900">${p.nama}</h4>
                            <p class="text-[10px] text-gray-400">${p.kelas} | Absen: ${p.absen}</p>
                        </div>
                        <span class="text-[10px] px-2 py-1 ${p.status === 'pending' ? 'bg-yellow-100 text-yellow-600' : 'bg-green-100 text-green-600'} rounded-full font-bold">
                            ${p.status.toUpperCase()}
                        </span>
                    </div>
                    <div class="bg-white p-2 rounded-lg mb-3">
                        <p class="text-[10px] text-gray-500 font-semibold mb-1">ALASAN KELUAR:</p>
                        <p class="text-xs text-gray-700">${p.alasan}</p>
                    </div>
                    ${p.status === 'pending' ? `
                        <div class="grid grid-cols-2 gap-2">
                            <button onclick="updatePermitStatus(${p.id}, 'denied')" class="py-2 bg-red-50 text-red-600 text-[10px] font-bold rounded-lg border border-red-100">TOLAK</button>
                            <button onclick="updatePermitStatus(${p.id}, 'approved')" class="py-2 bg-blue-600 text-white text-[10px] font-bold rounded-lg shadow-sm">IZINKAN</button>
                        </div>
                    ` : `
                        <p class="text-[9px] text-gray-400 italic text-center">Menunggu murid mengklik 'Selesai' untuk konfirmasi kembali.</p>
                    `}
                </div>
            `).join('');
            lucide.createIcons();
        }

        function renderAdminHistory() {
            const list = document.getElementById('history-list');
            const data = permits.filter(p => p.status === 'finished' || p.status === 'denied');

            if (data.length === 0) {
                list.innerHTML = `<div class="text-center py-10"><p class="text-gray-400 text-xs">Belum ada data riwayat</p></div>`;
                return;
            }

            list.innerHTML = data.map(p => `
                <div class="bg-white p-4 rounded-2xl border-l-4 ${p.status === 'finished' ? 'border-green-500' : 'border-red-500'} shadow-sm">
                    <div class="flex justify-between items-center mb-1">
                        <h4 class="font-bold text-sm">${p.nama}</h4>
                        <span class="text-[8px] text-gray-400 font-medium">${p.waktuPengajuan}</span>
                    </div>
                    <div class="grid grid-cols-2 gap-4 mt-2">
                        <div>
                            <p class="text-[8px] text-gray-400 font-bold uppercase">Jam Keluar</p>
                            <p class="text-[10px] font-medium text-gray-700">${p.jamKeluar}</p>
                        </div>
                        <div>
                            <p class="text-[8px] text-gray-400 font-bold uppercase">Jam Kembali</p>
                            <p class="text-[10px] font-medium text-gray-700">${p.waktuSelesai || '-'}</p>
                        </div>
                    </div>
                    <div class="mt-2 text-[10px] text-gray-500 italic truncate italic">"${p.alasan}"</div>
                </div>
            `).join('');
        }

        function updatePermitStatus(id, newStatus) {
            const idx = permits.findIndex(p => p.id === id);
            if (idx !== -1) {
                permits[idx].status = newStatus;
                saveData();
                renderAdminPending();
                if(newStatus === 'approved') {
                    alertModal("Berhasil!", "Izin telah diberikan.", "success");
                } else {
                    alertModal("Ditolak!", "Izin telah dibatalkan.", "info");
                }
            }
        }

        // UTILITIES
        function saveData() {
            localStorage.setItem('sman2_permits', JSON.stringify(permits));
        }

        function alertModal(title, msg = "", type = "info") {
            const modal = document.getElementById('notification-modal');
            const mTitle = document.getElementById('modal-title');
            const mMsg = document.getElementById('modal-message');
            const mIcon = document.getElementById('modal-icon');

            mTitle.innerText = title;
            mMsg.innerText = msg;
            
            if (type === 'success') {
                mIcon.innerHTML = '<div class="w-16 h-16 bg-green-100 text-green-500 rounded-full flex items-center justify-center"><i data-lucide="check-circle" class="w-10 h-10"></i></div>';
            } else {
                mIcon.innerHTML = '<div class="w-16 h-16 bg-blue-100 text-blue-500 rounded-full flex items-center justify-center"><i data-lucide="bell" class="w-10 h-10"></i></div>';
            }

            modal.classList.remove('hidden');
            lucide.createIcons();
        }

        function closeModal() {
            document.getElementById('notification-modal').classList.add('hidden');
        }
    </script>
</body>
</html>
