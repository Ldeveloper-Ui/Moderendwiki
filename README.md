# Moderendwiki
ModerendWiki Adalah Web yang, terinspirasi dari web wikipedia dan di buat untuk informasi digital

index.html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Modern Wiki</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --neon: #00e5ff;
            --muted: #80deea;
            --bg1: #021019;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            margin: 0;
            background: radial-gradient(circle at top, var(--bg1), #000);
            font-family: 'Roboto', sans-serif;
            color: #e0f7fa;
            overflow-x: hidden;
        }

        header {
            background: rgba(0, 255, 255, 0.05);
            backdrop-filter: blur(6px);
            border-bottom: 1px solid rgba(0, 255, 255, 0.2);
            padding: 12px 20px;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 10;
        }

        header p {
            margin: 0;
            font-size: 0.9em;
            color: var(--muted);
        }

        header h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.8em;
            color: var(--neon);
            text-shadow: 0 0 10px var(--neon);
            margin: 6px 0 10px;
        }

        nav {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 8px;
        }

        nav a {
            color: var(--muted);
            text-decoration: none;
            padding: 7px 14px;
            border: 1px solid rgba(0, 255, 255, 0.12);
            border-radius: 8px;
            transition: .25s;
        }

        nav a:hover,
        nav a.active {
            background: rgba(0, 255, 255, 0.12);
            color: #fff;
        }

        main {
            max-width: 900px;
            margin: auto;
            padding: 20px;
        }

        article {
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(0, 255, 255, 0.08);
            border-radius: 12px;
            padding: 18px;
            margin-bottom: 18px;
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.03);
            animation: fadeIn .7s ease;
        }

        article h2 {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.5em;
            color: #00bcd4;
            margin-bottom: 10px;
        }

        article p,
        article ul {
            line-height: 1.6;
            color: #b2ebf2;
        }
        
        .contact-table {
            display: grid;
            grid-template-columns: auto 1fr;
            gap: 10px 20px;
            margin-top: 20px;
            background: rgba(0, 255, 255, 0.05);
            border: 1px solid rgba(0, 255, 255, 0.1);
            border-radius: 8px;
            padding: 15px;
        }
        .contact-table strong {
            color: var(--neon);
            white-space: nowrap;
        }
        .contact-table span {
            color: #b2ebf2;
            word-break: break-all;
        }

        footer {
            text-align: center;
            padding: 14px;
            border-top: 1px solid rgba(0, 255, 255, 0.08);
            font-size: 0.9em;
            color: var(--muted);
            margin-top: 30px;
        }

        canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(18px)
            }

            to {
                opacity: 1;
                transform: translateY(0)
            }
        }

        /* Top price widget */
        #cryptoTop {
            margin-top: 8px;
            color: var(--neon);
            font-weight: 600;
        }

        /* CHATBOT / INFO PANEL STYLES */
        #ai-assistant {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 320px;
            max-width: calc(100% - 40px);
            background: rgba(0, 0, 0, 0.8);
            border: 1px solid rgba(0, 255, 255, 0.2);
            border-radius: 12px;
            overflow: hidden;
            font-size: 14px;
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.7);
            z-index: 9999;
            user-select: none;
            cursor: default;
            display: flex;
            flex-direction: column;
            backdrop-filter: blur(12px);
        }

        #ai-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 10px 14px;
            background: rgba(0, 255, 255, 0.1);
            cursor: grab;
            color: var(--neon);
            font-weight: 700;
            font-family: 'Orbitron', sans-serif;
            font-size: 1.1em;
            user-select: none;
        }

        #ai-header:active {
            cursor: grabbing;
        }

        #ai-body {
            display: flex;
            flex-direction: column;
            height: 360px;
            background: rgba(0, 0, 0, 0.6);
            color: var(--muted);
        }

        #ai-messages {
            flex: 1;
            padding: 10px 14px;
            overflow-y: auto;
            font-size: 14px;
            line-height: 1.4;
        }

        .msg {
            margin: 6px 0;
            padding: 8px 12px;
            border-radius: 8px;
            max-width: 85%;
            word-break: break-word;
        }

        .msg.user {
            background: rgba(0, 229, 255, 0.15);
            align-self: flex-end;
            color: #fff;
        }

        .msg.ai {
            background: rgba(255, 255, 255, 0.1);
            align-self: flex-start;
            border: 1px solid rgba(0, 255, 255, 0.12);
            color: #e0f7fa;
        }

        #ai-controls {
            display: flex;
            border-top: 1px solid rgba(0, 255, 255, 0.12);
            background: rgba(0, 255, 255, 0.05);
        }

        #ai-input {
            flex: 1;
            padding: 12px 14px;
            border: none;
            background: transparent;
            color: #fff;
            outline: none;
            font-size: 14px;
            font-family: 'Roboto', sans-serif;
        }

        #ai-send {
            background: var(--neon);
            border: none;
            color: #000;
            padding: 0 18px;
            cursor: pointer;
            font-weight: 700;
            font-size: 14px;
            transition: background-color 0.3s;
        }

        #ai-send:hover {
            background: #00bcd4;
        }

        #ai-body.hidden {
            display: none;
        }

        @media (max-width: 420px) {
            #ai-assistant {
                right: 10px;
                left: 10px;
                width: auto;
            }

            #ai-body {
                height: 300px;
            }
        }
    </style>
</head>
<body>

    <canvas id="stars"></canvas>

    <header>
        <p>Pembuat: Vlsk2045 | Email: Vlskthegame@gmail.com</p>
        <h1>✨ Modern Wiki ✨</h1>
        <div id="cryptoTop">
            ⏳ Memuat harga Bitcoin...
        </div>
        <nav>
            <a href="#beranda" class="active">Beranda</a>
            <a href="#">Teknologi</a>
            <a href="#">Sejarah</a>
            <a href="#">Informasi</a>
            <a href="#kontak">Kontak</a>
        </nav>
    </header>

    <main>
        <article id="beranda">
            <h2>Apa Itu Modern Wiki?</h2>
            <p>Modern Wiki adalah platform pengetahuan yang dirancang untuk era digital masa depan. Dengan tampilan neon yang elegan, navigasi cepat, dan animasi interaktif, website ini membawa pengalaman membaca layaknya menjelajah galaksi informasi.</p>
            <h3>Kelebihan Dibanding Wiki Biasa</h3>
            <ul>
                <li>🚀 Desain modern yang memanjakan mata.</li>
                <li>⚡ Performa cepat dan ringan di semua perangkat.</li>
                <li>🌌 Efek animasi bintang untuk nuansa futuristik.</li>
                <li>🤖 Cocok untuk integrasi AI di masa depan.</li>
            </ul>
        </article>

        <article>
            <h2>Informasi Finansial & Aset Digital</h2>
            <p>Dapatkan informasi terkini seputar dunia finansial, mulai dari saham perusahaan teknologi hingga perkembangan terbaru di dunia aset kripto. Data di bawah ini diperbarui secara real-time untuk referensi Anda.</p>
            <div id="latest-crypto">
                <p>Memuat harga Bitcoin...</p>
            </div>
            <h3>Informasi Saham (Contoh)</h3>
            <p><strong>Saham Perusahaan Teknologi:</strong> Sektor ini terus berinovasi. Perusahaan seperti Google (GOOGL), Apple (AAPL), dan Microsoft (MSFT) tetap menjadi pilar utama di pasar saham global.</p>
            <p><strong>Investasi Jangka Panjang:</strong> Memilih saham dengan fundamental kuat seringkali menjadi strategi yang lebih aman dibandingkan trading jangka pendek yang spekulatif.</p>
            <p><strong>Pentingnya Diversifikasi:</strong> Jangan menaruh semua aset Anda di satu tempat. Diversifikasi antara saham, obligasi, dan aset digital seperti Bitcoin dapat membantu mengurangi risiko.</p>
            <p><strong>Catatan:</strong> Informasi di sini bukan merupakan nasihat finansial. Selalu lakukan riset Anda sendiri (DYOR).</p>
        </article>
        
        <article id="kontak">
            <h2>Hubungi Kami</h2>
            <p>Untuk pertanyaan, dukungan, atau informasi lebih lanjut, silakan hubungi kami melalui kontak di bawah ini.</p>
            <div class="contact-table">
                <strong>Nomor Telepon:</strong>
                <span>838 2173 0195</span>
                <strong>Email:</strong>
                <span>AnakEmas2045@gmail.com</span>
            </div>
        </article>
    </main>

    <footer>
        <p>&copy; 2025 Modern Wiki. Dibuat dengan ❤️ untuk masa depan.</p>
    </footer>

    <aside id="ai-assistant">
        <div id="ai-header" tabindex="0" role="button" aria-pressed="true">
            <span>🤖 Asisten AI</span>
            <span id="ai-toggle-state">Tutup</span>
        </div>
        <div id="ai-body">
            <div id="ai-messages">
                <div class="msg ai">Halo! Saya asisten AI. Anda bisa bertanya tentang teknologi, kripto, atau topik umum lainnya.</div>
            </div>
            <div id="ai-controls">
                <input id="ai-input" type="text" placeholder="Ketik pesan..." autocomplete="off">
                <button id="ai-send">Kirim</button>
            </div>
        </div>
    </aside>

    <script>
        /* ===== STARRY BACKGROUND ===== */
        const canvas = document.getElementById('stars'),
            ctx = canvas.getContext('2d');
        let stars = [];

        function resizeCanvas() {
            canvas.width = innerWidth;
            canvas.height = innerHeight;
        }
        addEventListener('resize', resizeCanvas);
        resizeCanvas();

        function initStars() {
            stars = [];
            for (let i = 0; i < 160; i++) {
                stars.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    r: Math.random() * 1.6 + 0.2,
                    s: Math.random() * 0.35 + 0.02
                });
            }
        }

        function drawStars() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = '#0ff';
            stars.forEach(s => {
                ctx.beginPath();
                ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
                ctx.fill();
            })
        }

        function updateStars() {
            stars.forEach(s => {
                s.y += s.s;
                if (s.y > canvas.height) {
                    s.y = 0;
                    s.x = Math.random() * canvas.width;
                }
            });
        }

        function animate() {
            drawStars();
            updateStars();
            requestAnimationFrame(animate);
        }
        initStars();
        animate();

        /* ===== BTC PRICE (CoinGecko) - update tiap 60 detik ===== */
        const topElem = document.getElementById('cryptoTop');
        const latestCrypto = document.getElementById('latest-crypto');

        async function fetchBtc() {
            try {
                const res = await fetch('https://api.coingecko.com/api/v3/simple/price?ids=bitcoin&vs_currencies=usd,idr&include_24hr_change=true');
                if (!res.ok) throw new Error('Fetch failed');
                const data = await res.json();
                const usd = data.bitcoin.usd;
                const idr = data.bitcoin.idr;
                const change = data.bitcoin.usd_24h_change ?? 0;
                const sign = change >= 0 ? '▲' : '▼';
                const color = change >= 0 ? '#00e5ff' : '#ff4d4d'; // Warna untuk naik/turun

                topElem.innerHTML = `💰 Bitcoin: $${usd.toLocaleString()} USD <span style="color:${color};">(${sign}${Math.abs(change).toFixed(2)}% 24h)</span>`;

                if (latestCrypto) { // Cek jika elemen ada
                    latestCrypto.innerHTML = `
                    <p>Harga Bitcoin saat ini: <strong>$${usd.toLocaleString()}</strong> (~Rp ${idr.toLocaleString()})</p>
                    <ul>
                        <li>Perubahan 24 jam: <strong style="color:${color}">${change.toFixed(2)}%</strong>.</li>
                        <li>Sumber: CoinGecko (update otomatis tiap 1 menit).</li>
                    </ul>
                `;
                }
            } catch (e) {
                topElem.textContent = '⚠️ Gagal memuat harga Bitcoin';
                if (latestCrypto) latestCrypto.innerHTML = '<p>Gagal memuat harga Bitcoin.</p>';
                console.error(e);
            }
        }
        fetchBtc();
        setInterval(fetchBtc, 60000);

        /* ===== CHATBOT UI & DRAG FUNCTIONALITY ===== */
        const assistant = document.getElementById('ai-assistant');
        const header = document.getElementById('ai-header');
        const body = document.getElementById('ai-body');
        const messages = document.getElementById('ai-messages');
        const input = document.getElementById('ai-input');
        const sendBtn = document.getElementById('ai-send');
        const toggleState = document.getElementById('ai-toggle-state');
        let isDragging = false;
        let dragOffsetX = 0;
        let dragOffsetY = 0;

        function togglePanel() {
            const isHidden = body.classList.toggle('hidden');
            toggleState.textContent = isHidden ? 'Buka' : 'Tutup';
            header.setAttribute('aria-pressed', !isHidden);
            if (!isHidden) input.focus();
        }

        header.addEventListener('click', (e) => {
            // Hanya toggle jika klik terjadi langsung di header, bukan saat selesai drag
            if (e.target.closest('#ai-header')) {
                const rect = header.getBoundingClientRect();
                const clickX = e.clientX - rect.left;
                const clickY = e.clientY - rect.top;
                if (!isDragging || (Math.abs(clickX - dragOffsetX) < 5 && Math.abs(clickY - dragOffsetY) < 5)) {
                    togglePanel();
                }
            }
        });

        header.addEventListener('keydown', e => {
            if (e.key === 'Enter' || e.key === ' ') {
                e.preventDefault();
                togglePanel();
            }
        });

        header.addEventListener('mousedown', e => {
            isDragging = true;
            dragOffsetX = e.clientX - assistant.getBoundingClientRect().left;
            dragOffsetY = e.clientY - assistant.getBoundingClientRect().top;
            header.style.cursor = 'grabbing';
            document.body.style.userSelect = 'none'; // Cegah seleksi teks saat drag
            e.preventDefault();
        });

        window.addEventListener('mouseup', () => {
            if (isDragging) {
                isDragging = false;
                header.style.cursor = 'grab';
                document.body.style.userSelect = '';
            }
        });

        window.addEventListener('mousemove', e => {
            if (isDragging) {
                let x = e.clientX - dragOffsetX;
                let y = e.clientY - dragOffsetY;
                const padding = 10;
                const maxX = window.innerWidth - assistant.offsetWidth - padding;
                const maxY = window.innerHeight - assistant.offsetHeight - padding;
                x = Math.min(Math.max(x, padding), maxX);
                y = Math.min(Math.max(y, padding), maxY);
                assistant.style.left = x + 'px';
                assistant.style.top = y + 'px';
                assistant.style.right = 'auto';
                assistant.style.bottom = 'auto';
            }
        });

        /* ===== CHATBOT MESSAGE HANDLING ===== */
        function addMsg(text, who = 'ai') {
            const el = document.createElement('div');
            el.className = 'msg ' + (who === 'user' ? 'user' : 'ai');
            el.innerText = text;
            messages.appendChild(el);
            messages.scrollTop = messages.scrollHeight;
        }

        async function sendMessage() {
            const txt = input.value.trim();
            if (!txt) return;

            addMsg(txt, 'user');
            input.value = '';
            input.focus();

            const loadingEl = document.createElement('div');
            loadingEl.className = 'msg ai';
            loadingEl.innerText = '...';
            messages.appendChild(loadingEl);
            messages.scrollTop = messages.scrollHeight;

            try {
                // --- DEMO STATIS (bisa Anda gunakan sekarang) ---
                let reply = "Maaf, saya belum terhubung ke server untuk memproses permintaan itu.";
                if (txt.toLowerCase().includes('bitcoin')) {
                    reply = "Bitcoin adalah aset kripto terdesentralisasi pertama. Harganya sangat fluktuatif. Anda bisa melihat harga terbarunya di bagian atas halaman ini.";
                } else if (txt.toLowerCase().includes('saham')) {
                    reply = "Saham adalah bukti kepemilikan nilai suatu perusahaan. Berinvestasi di saham bisa memberikan keuntungan, namun juga memiliki risiko.";
                } else if (txt.toLowerCase().includes('halo') || txt.toLowerCase().includes('hai')) {
                    reply = "Halo juga! Ada yang bisa saya bantu terkait teknologi atau finansial?";
                }

                setTimeout(() => {
                    loadingEl.innerText = reply;
                }, 1000); // Simulasi waktu loading
            } catch (err) {
                loadingEl.innerText = '⚠️ Gagal menghubungi server.';
                console.error(err);
            }
        }

        sendBtn.addEventListener('click', sendMessage);
        input.addEventListener('keypress', (e) => {
            if (e.key === 'Enter' && !e.shiftKey) { // Kirim dengan Enter
                e.preventDefault();
                sendMessage();
            }
        });

        /* === Init: panel terbuka === */
        if (!body.classList.contains('hidden')) {
            toggleState.textContent = 'Tutup';
            header.setAttribute('aria-pressed', 'true');
            // Optional: Fokus input saat halaman selesai dimuat
            window.addEventListener('load', () => {
                input.focus();
            });
        }
    </script>
</body>
</html>