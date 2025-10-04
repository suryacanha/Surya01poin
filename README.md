# Surya01poin
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dasbor Media Sosial - Mockup</title>
    <!-- Memuat Tailwind CSS untuk styling responsif dan modern -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Konfigurasi Tailwind untuk font Inter dan warna kustom -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'primary': '#1D9BF0', // Warna biru Twitter/X untuk kesan profesional
                        'secondary': '#FF5858', // Merah cerah
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                }
            }
        }
    </script>
    <style>
        /* Mengatur font Inter */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        
        /* Custom scrollbar untuk tampilan yang lebih baik */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #f1f1f1; border-radius: 10px; }
        ::-webkit-scrollbar-thumb { background: #888; border-radius: 10px; }
        ::-webkit-scrollbar-thumb:hover { background: #555; }

        /* Styling untuk tampilan mobile */
        .card {
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.06);
            transition: transform 0.3s ease-in-out;
        }
        .card:hover {
            transform: translateY(-2px);
        }
    </style>
</head>
<body class="bg-gray-50 min-h-screen font-sans p-4 sm:p-8">

    <!-- Kontainer Utama -->
    <div class="max-w-4xl mx-auto">
        <header class="text-center mb-8 sm:mb-12">
            <h1 class="text-3xl sm:text-4xl font-extrabold text-gray-800">
                Dasbor Simulasi <span class="text-primary">Media Sosial</span>
            </h1>
            <p class="mt-2 text-gray-500 max-w-xl mx-auto">
                Antarmuka pengguna (UI/UX) untuk mendemonstrasikan ide pengelolaan multi-platform.
            </p>
            
            <!-- Peringatan Kritis -->
            <div id="safety-alert" class="mt-6 p-4 bg-yellow-100 border-l-4 border-secondary text-secondary-900 rounded-lg max-w-md mx-auto">
                <p class="font-bold">Penting:</p>
                <p class="text-sm">Kode ini adalah **mockup** dan **tidak memiliki fungsionalitas nyata** untuk menambah atau memanipulasi data di TikTok, Instagram, atau YouTube. Ini sesuai dengan kebijakan keamanan dan layanan platform.</p>
            </div>
            <!-- Akhir Peringatan Kritis -->

        </header>

        <!-- Form Permintaan -->
        <section id="input-form" class="card bg-white p-6 sm:p-8 rounded-xl mb-8">
            <h2 class="text-2xl font-semibold text-gray-700 mb-6">Buat Permintaan Simulasi</h2>
            
            <form id="submission-form">
                
                <!-- Pilihan Platform -->
                <div class="mb-4">
                    <label for="platform" class="block text-sm font-medium text-gray-600 mb-1">Pilih Platform</label>
                    <select id="platform" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-primary focus:border-primary transition duration-150">
                        <option value="tiktok">TikTok</option>
                        <option value="instagram">Instagram</option>
                        <option value="youtube">YouTube</option>
                    </select>
                </div>

                <!-- Pilihan Jenis Layanan -->
                <div class="mb-4">
                    <label for="service-type" class="block text-sm font-medium text-gray-600 mb-1">Jenis Layanan (Simulasi)</label>
                    <select id="service-type" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-primary focus:border-primary transition duration-150">
                        <option value="followers">Pengikut / Subscriber</option>
                        <option value="views">Tayangan (Views)</option>
                        <option value="likes">Suka (Likes)</option>
                        <option value="comments">Komentar</option>
                    </select>
                </div>
                
                <!-- Input Tautan / Link -->
                <div class="mb-4">
                    <label for="link" class="block text-sm font-medium text-gray-600 mb-1">Tautan Profil/Konten Target</label>
                    <input type="url" id="link" required placeholder="Contoh: https://tiktok.com/@username"
                           class="w-full p-3 border border-gray-300 rounded-lg focus:ring-primary focus:border-primary transition duration-150">
                </div>
                
                <!-- Input Jumlah -->
                <div class="mb-6">
                    <label for="quantity" class="block text-sm font-medium text-gray-600 mb-1">Jumlah (Simulasi)</label>
                    <input type="number" id="quantity" required min="10" max="5000" value="1000"
                           class="w-full p-3 border border-gray-300 rounded-lg focus:ring-primary focus:border-primary transition duration-150">
                    <p class="text-xs text-gray-500 mt-1">Hanya angka simulasi antara 10 hingga 5000.</p>
                </div>
                
                <!-- Tombol Proses -->
                <button type="submit" id="process-button" 
                        class="w-full bg-primary text-white py-3 rounded-xl font-bold hover:bg-blue-600 transition duration-300 shadow-md hover:shadow-lg focus:outline-none focus:ring-4 focus:ring-primary focus:ring-opacity-50">
                    Proses Permintaan Simulasi
                </button>
            </form>
        </section>
        
        <!-- Area Status / Hasil Simulasi -->
        <section id="status-area" class="card bg-white p-6 sm:p-8 rounded-xl">
            <h2 class="text-2xl font-semibold text-gray-700 mb-6">Status Simulasi</h2>
            
            <!-- Area Notifikasi -->
            <div id="notification-box" class="hidden p-4 rounded-lg text-white font-medium mb-4" role="alert"></div>

            <!-- Detail Permintaan Terakhir -->
            <div id="last-request" class="bg-gray-100 p-4 rounded-lg">
                <p class="text-sm font-semibold text-gray-700 mb-2">Permintaan Terakhir:</p>
                <ul class="text-sm text-gray-600 space-y-1" id="request-details">
                    <li><span class="font-medium">Platform:</span> <span id="detail-platform">N/A</span></li>
                    <li><span class="font-medium">Layanan:</span> <span id="detail-service">N/A</span></li>
                    <li><span class="font-medium">Jumlah:</span> <span id="detail-quantity">N/A</span></li>
                    <li><span class="font-medium">Tautan:</span> <span id="detail-link" class="break-all">N/A</span></li>
                </ul>
            </div>

            <!-- Indikator Kemajuan Simulasi -->
            <div id="progress-container" class="mt-6 hidden">
                <p class="text-sm font-medium text-gray-700 mb-2">Kemajuan Proses Simulasi:</p>
                <div class="w-full bg-gray-200 rounded-full h-2.5">
                    <div id="progress-bar" class="bg-primary h-2.5 rounded-full" style="width: 0%"></div>
                </div>
                <p id="progress-text" class="text-right text-xs mt-1 text-primary">0% Selesai</p>
            </div>
            
        </section>

    </div>

    <script>
        // Variabel global untuk elemen DOM
        const form = document.getElementById('submission-form');
        const notificationBox = document.getElementById('notification-box');
        const progressContainer = document.getElementById('progress-container');
        const progressBar = document.getElementById('progress-bar');
        const progressText = document.getElementById('progress-text');
        const processButton = document.getElementById('process-button');
        
        // Fungsi untuk menampilkan notifikasi simulasi
        function showNotification(message, type = 'success') {
            notificationBox.textContent = message;
            notificationBox.classList.remove('hidden', 'bg-red-500', 'bg-green-500');

            if (type === 'success') {
                notificationBox.classList.add('bg-green-500');
            } else if (type === 'error') {
                notificationBox.classList.add('bg-red-500');
            }
            
            // Sembunyikan notifikasi setelah 5 detik
            setTimeout(() => {
                notificationBox.classList.add('hidden');
            }, 5000);
        }

        // Fungsi untuk memulai animasi progress bar (simulasi)
        function startSimulation(quantity) {
            progressContainer.classList.remove('hidden');
            progressBar.style.width = '0%';
            progressText.textContent = '0% Selesai';
            processButton.disabled = true;
            processButton.textContent = 'Memproses...';

            let progress = 0;
            const intervalDuration = 50; // Update setiap 50ms
            const totalDuration = 3000; // Total durasi simulasi 3 detik
            const steps = totalDuration / intervalDuration;
            const progressIncrement = 100 / steps;

            const progressInterval = setInterval(() => {
                progress += progressIncrement;
                
                if (progress >= 100) {
                    progress = 100;
                    clearInterval(progressInterval);
                    
                    // Simulasi Selesai
                    showNotification(`Simulasi sukses! ${quantity.toLocaleString()} metrik telah "ditambahkan". (Mockup)`, 'success');
                    processButton.disabled = false;
                    processButton.textContent = 'Proses Permintaan Simulasi';
                    progressContainer.classList.add('hidden');
                }
                
                // Update UI
                const displayProgress = Math.min(progress, 100).toFixed(0);
                progressBar.style.width = `${displayProgress}%`;
                progressText.textContent = `${displayProgress}% Selesai`;

            }, intervalDuration);
        }

        // Event listener untuk pengiriman form
        form.addEventListener('submit', function(event) {
            event.preventDefault(); // Mencegah form dikirim secara default

            // Ambil nilai dari input form
            const platform = document.getElementById('platform').value;
            const serviceType = document.getElementById('service-type').value;
            const link = document.getElementById('link').value;
            const quantity = parseInt(document.getElementById('quantity').value, 10);
            
            // Simpan detail permintaan ke area status
            document.getElementById('detail-platform').textContent = platform.toUpperCase();
            
            let serviceLabel = serviceType;
            if (serviceType === 'followers') {
                // Label disesuaikan dengan platform untuk subscriber/pengikut
                serviceLabel = platform === 'youtube' ? 'Subscriber' : 'Pengikut';
            } else if (serviceType === 'views') {
                serviceLabel = 'Tayangan (Views)';
            } else if (serviceType === 'likes') {
                serviceLabel = 'Suka (Likes)';
            } else if (serviceType === 'comments') {
                serviceLabel = 'Komentar';
            }

            document.getElementById('detail-service').textContent = serviceLabel;
            document.getElementById('detail-quantity').textContent = quantity.toLocaleString();
            document.getElementById('detail-link').textContent = link;

            // Memulai proses simulasi
            startSimulation(quantity);
        });

        // Event listener untuk memperbarui placeholder tautan berdasarkan platform
        document.getElementById('platform').addEventListener('change', function() {
            const platform = this.value;
            const linkInput = document.getElementById('link');
            
            let placeholder = '';
            if (platform === 'tiktok') {
                placeholder = 'Contoh: https://tiktok.com/@username';
            } else if (platform === 'instagram') {
                placeholder = 'Contoh: https://instagram.com/username';
            } else if (platform === 'youtube') {
                placeholder = 'Contoh: https://youtube.com/channel/id_channel_anda';
            }
            linkInput.placeholder = placeholder;
        });

        // Setel placeholder awal saat halaman dimuat
        document.getElementById('platform').dispatchEvent(new Event('change'));
    </script>

</body>
</html>

