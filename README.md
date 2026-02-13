<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Untuk Raissya Maulidina</title>
    <style>
        :root {
            --pink-light: #fce4ec;
            --pink-main: #f48fb1;
            --pink-dark: #ad1457;
            --gold: #ffb703;
            --white: #ffffff;
            --envelope-bg: #ffb1c1; 
        }

        * { box-sizing: border-box; }

        body {
            font-family: 'Courier New', Courier, monospace;
            background-color: #fef0f3;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
        }

        /* --- PAGE 0: WELCOME --- */
        #page0 {
            background: white;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
            max-width: 350px;
        }

        .welcome-text {
            font-size: 1.2rem;
            color: var(--pink-dark);
            margin-bottom: 25px;
            font-weight: bold;
            line-height: 1.5;
        }

        /* --- EFEK HUJAN HATI --- */
        .falling-heart {
            position: fixed;
            top: -20px;
            font-size: 20px;
            user-select: none;
            pointer-events: none;
            z-index: 9999;
            animation: fall linear forwards;
        }

        @keyframes fall {
            to { transform: translateY(110vh) rotate(360deg); }
        }

        .page {
            display: none;
            width: 100%;
            text-align: center;
            animation: fadeIn 0.5s ease-in-out forwards;
        }

        .active { display: flex; flex-direction: column; align-items: center; }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        /* --- PAGE 1: CLAW MACHINE --- */
        .machine-frame {
            width: 300px; height: 380px; background: white;
            border: 10px solid var(--pink-main); border-radius: 20px 20px 0 0;
            position: relative; overflow: hidden;
        }

        .claw-system {
            position: absolute; top: 0; left: 125px; width: 50px;
            z-index: 10; transition: left 0.2s ease-out;
            display: flex; flex-direction: column; align-items: center;
        }

        .claw-cable { width: 4px; height: 30px; background: #555; transition: height 0.8s ease-in-out; }
        .claw-head { width: 40px; height: 15px; background: #888; border-radius: 5px; position: relative; }
        .claw-arm { position: absolute; width: 6px; height: 22px; background: #999; top: 10px; border-radius: 4px; }
        .arm-left { left: 5px; transform: rotate(25deg); }
        .arm-right { right: 5px; transform: rotate(-25deg); }

        .prize-pool { position: absolute; bottom: 0; width: 100%; height: 120px; }
        .heart { position: absolute; font-size: 26px; transition: bottom 0.8s ease-in-out; }

        .panel {
            width: 320px; background: var(--pink-main); padding: 15px 0;
            border-radius: 0 0 20px 20px; box-shadow: 0 8px 0 #db5a7a;
            display: flex; flex-direction: column; align-items: center; gap: 10px;
        }

        .joypad { display: flex; gap: 15px; }
        .btn-circle { width: 55px; height: 55px; border-radius: 50%; border: none; background: white; cursor: pointer; font-size: 20px; box-shadow: 0 4px #ddd; }
        .btn-circle:active { transform: translateY(2px); box-shadow: 0 2px #ddd; }
        .btn-action { width: 140px; height: 45px; border-radius: 20px; border: none; background: var(--gold); color: white; font-weight: bold; cursor: pointer; box-shadow: 0 4px #e6a600; font-family: sans-serif;}

        /* --- PAGE 2: ENVELOPE --- */
        .envelope-wrapper {
            position: relative; width: 320px; height: 220px;
            background-color: var(--envelope-bg); margin-top: 50px;
            border-radius: 5px; cursor: pointer; box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .flap {
            position: absolute; top: 0; left: 0; width: 0; height: 0;
            border-left: 160px solid transparent; border-right: 160px solid transparent;
            border-top: 120px solid #f896aa; transform-origin: top;
            transition: transform 0.6s ease; z-index: 3;
        }

        .pocket { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: var(--envelope-bg); z-index: 2; overflow: hidden; }

        .heart-seal {
            position: absolute; top: 45%; left: 50%; transform: translate(-50%, -50%);
            font-size: 40px; color: #ff4d6d; z-index: 4; transition: opacity 0.3s;
        }

        .letter-preview {
            position: absolute; bottom: 20px; left: 20px; width: 280px; height: 180px;
            background: #fdfdfd; border-radius: 3px; z-index: 1; transition: transform 1.5s ease-in-out;
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            padding: 20px; border: 1px solid #eee;
        }

        .opened .flap { transform: rotateX(180deg); z-index: 0; }
        .opened .letter-preview { transform: translateY(-130px); z-index: 5; }
        .opened .heart-seal { opacity: 0; }

        /* --- PAGE 3: SURAT UTAMA --- */
        .final-scroll-page {
            background: #fff; width: 90%; max-width: 400px;
            padding: 40px 30px; border-radius: 10px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.1);
            max-height: 85vh; overflow-y: auto; border: 1px solid #fce4ec;
            position: relative;
        }

        .long-text { text-align: center; line-height: 1.8; font-size: 15px; color: #5d4037; }
        
        .btn-claim {
            display: inline-block; margin-top: 25px; padding: 15px 30px;
            background-color: #ff4d6d; color: white; text-decoration: none;
            border-radius: 5px; font-weight: bold; font-family: sans-serif;
            box-shadow: 0 4px #ad1457;
        }

        /* --- STYLES UNTUK FOTO --- */
        .photo-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 20px 0;
            flex-wrap: wrap;
        }

        .photo-frame {
            background: white;
            padding: 8px 8px 20px 8px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            border: 1px solid #eee;
            transform: rotate(calc(var(--r) * 1deg));
        }

        .photo-frame img {
            width: 120px;
            height: 150px;
            object-fit: cover;
            display: block;
        }

    </style>
</head>
<body>

    <div id="page0" class="page active">
        <div class="welcome-text">
            Kamu siap untuk kejutan nya<br>
            <span style="font-size: 1.5rem; color: #ff4d6d;">Raissya Maulidina</span><br>
            yang paling cantik? ✨
        </div>
        <button class="btn-action" onclick="goToPage(1)" style="width: 200px;">SIAP! ❤️</button>
    </div>

    <div id="page1" class="page">
        <h2 style="color: var(--pink-dark); font-family: sans-serif;">Ambil Kejutanmu! ❤️</h2>
        <div class="machine-frame">
            <div class="claw-system" id="claw-sys">
                <div class="claw-cable" id="claw-cable"></div>
                <div class="claw-head"><div class="claw-arm arm-left"></div><div class="claw-arm arm-right"></div></div>
            </div>
            <div class="prize-pool" id="pool"></div>
        </div>
        <div class="panel">
            <div class="joypad">
                <button class="btn-circle" onclick="moveClaw(-30)">◀️</button>
                <button class="btn-circle" onclick="moveClaw(30)">▶️</button>
            </div>
            <button class="btn-action" onclick="dropClaw()">AMBIL!</button>
        </div>
    </div>

    <div id="page2" class="page">
        <div class="envelope-wrapper" id="envelope" onclick="openAnimation()">
            <div class="flap"></div>
            <div class="pocket">
                <div class="signature-line" style="position: absolute; bottom: 20px; left: 20px; font-size: 12px;">
                    Dari: Arka<br>Untuk: Raissya M.
                </div>
            </div>
            <div class="heart-seal">❤️</div>
            <div class="letter-preview">
                <p>ada surat untuk muu</p>
                <p>maaf yaa hadia nya cuman bisa ini ajaa</p>
            </div>
        </div>
    </div>

    <div id="page3" class="page">
        <div class="final-scroll-page">
            <h2 style="color: var(--pink-dark);">untuk manusia paling cantik ❤️</h2>
            
            <div class="photo-container">
                <div class="photo-frame" style="--r: -3">
                    <img src="cantik.jpg" alt="Foto 1">
                </div>
                <div class="photo-frame" style="--r: 3">
                    <img src="cantik2.jpg" alt="Foto 2">
                </div>
            </div>
            <div class="long-text">
                <p>Halo <b>Raissya Maulidina</b>,</p>
                <p>Selamat ya! Akhirnya kamu berhasil menangkap surat ini.</p>
                <p>Terima kasih sudah menjadi alasan aku tersenyum setiap hari. Bersamamu, hal-hal yang biasa saja berubah jadi terasa luar biasa.</p>
                <p>Aku sangat bersyukur punya kamu yang selalu sabar dan pengertian. Tetaplah jadi Raissya yang ceria.</p>
                <p style="font-size: 20px; color: #ff4d6d; font-weight: bold; margin-top: 20px;">I Love You So Much! ❤️</p>
            </div>
            <a href="https://www.tiktok.com/@ar_nexo" class="btn-claim" target="_blank">🎁 KLAIM HADIAHMU</a>
            <br>
            <button class="btn-reload" style="background:none; border:none; color:#bbb; margin-top:20px; cursor:pointer;" onclick="location.reload()">Main Lagi</button>
        </div>
    </div>

    <script>
        let pos = 125;
        let isBusy = false;

        function goToPage(num) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            document.getElementById('page' + num).classList.add('active');
            
            if(num === 1) {
                initHearts(); // Inisialisasi hati saat masuk ke game
            }
            if(num === 3) {
                startHeartRain();
            }
        }

        function initHearts() {
            const pool = document.getElementById('pool');
            pool.innerHTML = ''; // Clear pool first
            for(let i=0; i<15; i++) {
                const h = document.createElement('span');
                h.className = 'heart';
                h.innerHTML = (i === 7) ? '❤️' : '🤍';
                if(i === 7) h.id = 'jackpot';
                h.style.left = Math.random() * 260 + 'px';
                h.style.bottom = Math.random() * 60 + 'px';
                pool.appendChild(h);
            }
        }

        function moveClaw(val) {
            if(isBusy) return;
            pos += val;
            if(pos < 10) pos = 10; if(pos > 250) pos = 250;
            document.getElementById('claw-sys').style.left = pos + 'px';
        }

        function dropClaw() {
            if(isBusy) return;
            isBusy = true;
            const cable = document.getElementById('claw-cable');
            cable.style.height = "280px";
            setTimeout(() => {
                const clawX = pos + 20;
                const target = document.getElementById('jackpot');
                const targetX = target.offsetLeft + 13;
                if(Math.abs(clawX - targetX) < 22) {
                    target.style.transition = "bottom 0.8s ease-in-out";
                    target.style.bottom = "330px";
                    cable.style.height = "30px";
                    setTimeout(() => goToPage(2), 1000);
                } else {
                    cable.style.height = "30px";
                    setTimeout(() => isBusy = false, 800);
                }
            }, 800);
        }

        function openAnimation() {
            const env = document.getElementById('envelope');
            env.classList.add('opened');
            setTimeout(() => {
                goToPage(3);
            }, 3000);
        }

        function startHeartRain() {
            const symbols = ['❤️', '💖', '💕', '💗', '🌸'];
            setInterval(() => {
                const heart = document.createElement('div');
                heart.className = 'falling-heart';
                heart.innerHTML = symbols[Math.floor(Math.random() * symbols.length)];
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.animationDuration = (Math.random() * 3 + 2) + 's'; 
                heart.style.opacity = Math.random();
                heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
                
                document.body.appendChild(heart);
                setTimeout(() => { heart.remove(); }, 5000);
            }, 300);
        }
    </script>
</body>
</html>
