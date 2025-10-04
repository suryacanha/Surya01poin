<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dasbor Media Sosial - Aktif</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: { primary: "#1D9BF0", secondary: "#FF5858" },
          fontFamily: { sans: ["Inter", "sans-serif"] }
        }
      }
    }
  </script>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
    .card { box-shadow: 0 4px 6px -1px rgba(0,0,0,.1),0 2px 4px -2px rgba(0,0,0,.06); }
  </style>
</head>
<body class="bg-gray-50 min-h-screen font-sans p-4 sm:p-8">

<div class="max-w-4xl mx-auto">
  <header class="text-center mb-8">
    <h1 class="text-3xl font-extrabold">Dasbor <span class="text-primary">Media Sosial</span></h1>
    <p class="mt-2 text-gray-500">Versi nyata berjalan di GitHub Pages (simulasi aman).</p>
  </header>

  <!-- Form -->
  <section class="card bg-white p-6 rounded-xl mb-8">
    <h2 class="text-xl font-semibold mb-4">Buat Permintaan</h2>
    <form id="submission-form">
      <label class="block mb-2">Pilih Platform</label>
      <select id="platform" class="w-full p-2 border rounded mb-3">
        <option value="tiktok">TikTok</option>
        <option value="instagram">Instagram</option>
        <option value="youtube">YouTube</option>
      </select>

      <label class="block mb-2">Jenis Layanan</label>
      <select id="service-type" class="w-full p-2 border rounded mb-3">
        <option value="followers">Pengikut</option>
        <option value="views">Tayangan</option>
        <option value="likes">Suka</option>
      </select>

      <label class="block mb-2">Tautan Profil/Konten</label>
      <input type="url" id="link" required placeholder="https://tiktok.com/@username"
             class="w-full p-2 border rounded mb-3">

      <label class="block mb-2">Jumlah</label>
      <input type="number" id="quantity" min="10" max="5000" value="1000"
             class="w-full p-2 border rounded mb-3">

      <button type="submit"
              class="w-full bg-primary text-white py-2 rounded font-bold hover:bg-blue-600">
        Proses
      </button>
    </form>
  </section>

  <!-- Status -->
  <section class="card bg-white p-6 rounded-xl">
    <h2 class="text-xl font-semibold mb-4">Status</h2>
    <div id="notification-box" class="hidden p-3 mb-4 rounded text-white"></div>
    <div id="last-request" class="bg-gray-100 p-3 rounded mb-4">
      <p class="font-bold">Permintaan Terakhir:</p>
      <p><b>Platform:</b> <span id="detail-platform">-</span></p>
      <p><b>Layanan:</b> <span id="detail-service">-</span></p>
      <p><b>Jumlah:</b> <span id="detail-quantity">-</span></p>
      <p><b>Tautan:</b> <span id="detail-link">-</span></p>
    </div>

    <div id="progress-container" class="hidden">
      <div class="w-full bg-gray-200 rounded-full h-2.5">
        <div id="progress-bar" class="bg-primary h-2.5 rounded-full" style="width:0%"></div>
      </div>
      <p id="progress-text" class="text-xs mt-1 text-primary">0% Selesai</p>
    </div>
  </section>

  <!-- Riwayat -->
  <section class="card bg-white p-6 rounded-xl mt-6">
    <h2 class="text-xl font-semibold mb-4">Riwayat Simulasi</h2>
    <ul id="history-list" class="text-sm text-gray-700 space-y-2"></ul>
  </section>
</div>

<script>
const form = document.getElementById("submission-form");
const notificationBox = document.getElementById("notification-box");
const progressContainer = document.getElementById("progress-container");
const progressBar = document.getElementById("progress-bar");
const progressText = document.getElementById("progress-text");
const historyList = document.getElementById("history-list");

// Load riwayat dari localStorage
function loadHistory() {
  const history = JSON.parse(localStorage.getItem("simHistory") || "[]");
  historyList.innerHTML = "";
  history.forEach(req => {
    const li = document.createElement("li");
    li.textContent = `[${req.platform}] ${req.service} - ${req.quantity} → ${req.link}`;
    historyList.appendChild(li);
  });
}
loadHistory();

function showNotification(msg, type="success") {
  notificationBox.textContent = msg;
  notificationBox.classList.remove("hidden","bg-green-500","bg-red-500");
  notificationBox.classList.add(type==="success" ? "bg-green-500":"bg-red-500");
  setTimeout(()=>notificationBox.classList.add("hidden"),4000);
}

function startSimulation(quantity, onFinish) {
  progressContainer.classList.remove("hidden");
  let progress=0;
  const intv=setInterval(()=>{
    progress+=10;
    if(progress>=100){
      progress=100;
      clearInterval(intv);
      onFinish();
    }
    progressBar.style.width=progress+"%";
    progressText.textContent=progress+"% Selesai";
  },200);
}

form.addEventListener("submit", e=>{
  e.preventDefault();
  const platform=document.getElementById("platform").value;
  const service=document.getElementById("service-type").value;
  const link=document.getElementById("link").value;
  const quantity=document.getElementById("quantity").value;

  document.getElementById("detail-platform").textContent=platform;
  document.getElementById("detail-service").textContent=service;
  document.getElementById("detail-quantity").textContent=quantity;
  document.getElementById("detail-link").textContent=link;

  startSimulation(quantity,()=>{
    showNotification("Simulasi selesai ✔️","success");
    progressContainer.classList.add("hidden");

    // Simpan ke localStorage
    const history=JSON.parse(localStorage.getItem("simHistory")||"[]");
    history.unshift({platform,service,link,quantity});
    localStorage.setItem("simHistory",JSON.stringify(history));
    loadHistory();
  });
});
</script>
</body>
</html>
