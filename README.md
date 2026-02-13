<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Special for Raissya Maulidina</title>
    <style>
        :root {
            --pink-light: #fce4ec;
            --pink-main: #f48fb1;
            --pink-dark: #ad1457;
            --gold: #ffb703;
            --white: #ffffff;
            --envelope-bg: #ffb1c1; 
        }

        /* Mencegah scroll dan zoom tidak sengaja di HP */
        * { 
            box-sizing: border-box; 
            -webkit-tap-highlight-color: transparent; 
            touch-action: manipulation;
        }

        body {
            font-family: 'Courier New', Courier, monospace;
            background-color: #fef0f3;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            height: -webkit-fill-available; /* Supaya pas di layar HP (Safari/Chrome) */
            overflow: hidden;
        }

        /* --- PAGE 0: WELCOME --- */
        #page0 {
            background: white;
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
            max-width: 85%;
            width: 320px;
            text-align: center;
        }

        .welcome-text {
            font-size: 1.1rem;
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
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .active { display: flex; }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        /* --- PAGE 1: CLAW MACHINE (OPTIMAL HP) --- */
        .machine-frame {
            width: 280px; height: 320px; background: white;
            border: 8px solid var(--pink-main); border-radius: 20px 20px 0 0;
            position: relative; overflow: hidden;
        }

        .claw-system {
            position: absolute; top: 0; left: 115px; width: 50px;
            z-index: 10; transition: left 0.2s ease-out;
            display: flex; flex-direction: column; align-items: center;
        }

        .claw-cable { width: 4px; height: 30px; background: #555; transition: height 0.8s ease-in-out; }
        .claw-head { width: 40px; height: 15px; background: #888; border-radius: 5px; position: relative; }
        .claw-arm { position: absolute; width: 6px; height: 22px; background: #999; top: 10px; border-radius: 4px; }
        .arm-left { left: 5px; transform: rotate(25deg); }
        .arm-right { right: 5px; transform: rotate(-25deg); }

        .prize-pool { position: absolute; bottom: 0; width: 100%; height: 80px; }
        .heart { position: absolute; font-size: 26px; transition: bottom 0.8s ease-in-out; }

        .panel {
            width: 280px; background: var(--pink-main); padding: 20px 0;
            border-radius: 0 0 20px 20px; box-shadow: 0 6px 0 #db5a7a;
            display: flex; flex-direction: column; align-items: center; gap: 15px;
        }

        .joypad { display: flex; gap: 30px; }
        .btn-circle { width: 65px; height: 65px; border-radius: 50%; border: none; background: white; cursor: pointer; font-size: 28px; box-shadow: 0 4px #ddd; display: flex; align-items: center; justify-content: center; }
        .btn-circle:active { transform: translateY(2px); box-shadow: 0 2px #ddd; }
        
        .btn-action { 
            width: 180px; height: 55px; border-radius: 30px; border: none; 
            background: var(--gold); color: white; font-weight: bold; 
            cursor: pointer; box-shadow: 0 4px #e6a600; font-family: sans-serif;
            font-size: 1.1rem;
        }

        /* --- PAGE 2: ENVELOPE --- */
        .envelope-wrapper {
            position: relative; width: 280px; height: 180px;
            background-color: var(--envelope-bg); margin-top: 50px;
            border-radius: 5px; cursor: pointer;
        }

        .flap {
            position: absolute; top: 0; left: 0; width: 0; height: 0;
            border-left: 140px solid transparent; border-right: 140px solid transparent;
            border-top: 100px solid #f896aa; transform-origin: top;
            transition: transform 0.6s ease; z-index: 3;
        }

        .pocket { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: var(--envelope-bg); z-index: 2; overflow: hidden; border-radius: 5px;}

        .heart-seal {
            position: absolute; top: 45%; left: 50%; transform: translate(-50%, -50%);
            font-size: 40px; color: #ff4d6d; z-index: 4; transition: opacity 0.3s;
        }

        .letter-preview {
            position: absolute; bottom: 10px; left: 10px; width: 260px; height: 150px;
            background: #fdfdfd; border-radius: 3px; z-index: 1; transition: transform 1.5s ease-in-out;
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            padding: 15px; border: 1px solid #eee; font-size: 14px;
        }

        .opened .flap { transform: rotateX(180deg); z-index: 0; }
        .opened .letter-preview { transform: translateY(-120px); z-index: 5; }
        .opened .heart-seal { opacity: 0; }

        /* --- PAGE 3: FINAL --- */
        .final-scroll-page {
            background: #fff; width: 90%; max-width: 360px;
            padding: 25px 20px; border-radius: 15px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.1);
            max-height: 85vh; overflow-y: auto;
        }

        .long-text { text-align: center; line-height: 1.6; font-size: 14px; color: #5d4037; }
        
        .photo-container { display: flex; justify-content: center; gap: 10px; margin: 15px 0; }
        .photo-frame { background: white; padding: 5px 5px 15px 5px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); border: 1px solid #eee; transform: rotate(calc(var(--r) * 1deg)); }
        .photo-frame img { width: 90px; height: 110px; object-fit: cover; display: block; }

        .btn-claim {
            display: inline-block; margin-top: 15px; padding: 12px 20px;
            background-color: #ff4d6d; color: white; text-decoration: none;
            border-radius: 25px; font-weight: bold; font-family: sans-serif;
        }
    </style>
</head>
<body>

    <div id="page0" class="page active">
        <div class="welcome-text">
            Siap untuk kejutan nya<br>
            <span style="font-size: 1.3rem; color: #ff4d6d;">Raissya Maulidina</span><br>
            yang paling cantik? ✨
        </div>
        <button class="btn-action" onclick="goToPage(1)">SIAP! ❤️</button>
    </div>

    <div id="page1" class="page">
        <h2 style="color: var(--pink-dark); font-size: 1.1rem; margin-bottom: 5px;">Tangkap Hati Merah! ❤️</h2>
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
                <div style="position: absolute; bottom: 10px; left: 10px; font-size: 10px; color: #ad1457;">Dari: Arka</div>
            </div>
            <div class="heart-seal">❤️</div>
            <div class="letter-preview">
                <p>Ada surat untukmu...</p>
                <p style="font-size: 12px; color: #888;">(Tap untuk buka ✨)</p>
            </div>
        </div>
    </div>

    <div id="page3" class="page">
        <div class="final-scroll-page">
            <h2 style="color: var(--pink-dark); font-size: 1.2rem;">Untuk Raissya ❤️</h2>
            <div class="photo-container">
                <div class="photo-frame" style="--r: -3"><img src="<a href="https://ibb.co.com/tTzX5mNp">"https://i.ibb.co.com/tTzX5mNp/cantik.jpg"  border="0"></a>" alt="Foto 1"></div>
                <div class="photo-frame" style="--r: 3"><img src="<a href="https://ibb.co.com/VYffGBkD">"https://i.ibb.co.com/VYffGBkD/cantik2.jpg"  border="0"></a>" alt="Foto 2"></div>
            </div>
            <div class="long-text">
                <p>Halo <b>Raissya Maulidina</b>,</p>
                <p>Selamat ya! Akhirnya kamu berhasil menangkap surat ini.</p>
                <p>Terima kasih sudah menjadi alasan aku tersenyum setiap hari. Bersamamu, semuanya jadi terasa luar biasa.</p>
                <p>Tetaplah jadi Raissya yang ceria dan sabar ya.</p>
                <p style="font-size: 18px; color: #ff4d6d; font-weight: bold;">I Love You! ❤️</p>
            </div>
            <a href="https://www.tiktok.com/@ar_nexo" class="btn-claim" target="_blank">🎁 KLAIM HADIAH</a>
            <br>
            <button style="background:none; border:none; color:#bbb; margin-top:15px;" onclick="location.reload()">Main Lagi</button>
        </div>
    </div>

    <script>
        let pos = 115;
        let isBusy = false;

        function goToPage(num) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            document.getElementById('page' + num).classList.add('active');
            if(num === 1) initHearts();
            if(num === 3) startHeartRain();
        }

        function initHearts() {
            const pool = document.getElementById('pool');
            pool.innerHTML = ''; 
            for(let i=0; i<10; i++) {
                const h = document.createElement('span');
                h.className = 'heart';
                if(i === 5) {
                    h.innerHTML = '❤️'; h.id = 'jackpot'; h.style.left = '125px'; 
                } else {
                    h.innerHTML = '😩'; h.style.left = Math.random() * 230 + 'px';
                }
                h.style.bottom = Math.random() * 30 + 'px';
                pool.appendChild(h);
            }
        }

        function moveClaw(val) {
            if(isBusy) return;
            pos += val;
            if(pos < 5) pos = 5; if(pos > 225) pos = 225;
            document.getElementById('claw-sys').style.left = pos + 'px';
        }

        function dropClaw() {
            if(isBusy) return;
            isBusy = true;
            const cable = document.getElementById('claw-cable');
            const target = document.getElementById('jackpot');
            cable.style.height = "210px";
            
            setTimeout(() => {
                const clawX = pos + 25;
                const targetX = target.offsetLeft + 15;
                if(Math.abs(clawX - targetX) < 30) {
                    target.style.zIndex = "11";
                    target.style.bottom = "280px";
                    cable.style.height = "30px";
                    setTimeout(() => goToPage(2), 1000);
                } else {
                    cable.style.height = "30px";
                    setTimeout(() => { isBusy = false; alert("Meleset! Coba lagi ya ❤️"); }, 800);
                }
            }, 800);
        }

        function openAnimation() {
            document.getElementById('envelope').classList.add('opened');
            setTimeout(() => goToPage(3), 2500);
        }

        function startHeartRain() {
            setInterval(() => {
                const h = document.createElement('div');
                h.className = 'falling-heart';
                h.innerHTML = '❤️';
                h.style.left = Math.random() * 100 + 'vw';
                h.style.animationDuration = (Math.random() * 3 + 2) + 's'; 
                document.body.appendChild(h);
                setTimeout(() => h.remove(), 5000);
            }, 400);
        }
    </script>
</body>
</html>
