<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cả Một Vườn Thương - 20/10</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Caveat:wght@600;700&family=Dancing+Script:wght@600;700&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <style>
        * {
            box-sizing: border-box;
            user-select: none;
            -webkit-user-select: none;
        }

        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow: hidden;
            background: linear-gradient(180deg, #bfe0ff 0%, #d8ecff 30%, #fde2e4 70%, #fff1f2 100%);
            margin: 0;
            padding: 0;
            width: 100vw;
            height: 100vh;
        }

        .font-handwriting {
            font-family: 'Dancing Script', cursive;
        }

        .font-caveat {
            font-family: 'Caveat', cursive;
        }

        #flowerCanvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 10;
            cursor: pointer;
        }

        /* Glassmorphism Card Style */
        .glass-card {
            background: rgba(255, 255, 255, 0.94);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            border: 1px solid rgba(244, 114, 182, 0.35);
            box-shadow: 0 25px 50px -12px rgba(225, 29, 72, 0.22), 0 0 30px rgba(255, 255, 255, 0.9) inset;
        }

        /* Custom Scrollbar */
        .custom-scrollbar::-webkit-scrollbar {
            width: 5px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: rgba(244, 114, 182, 0.05);
            border-radius: 10px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: rgba(244, 114, 182, 0.4);
            border-radius: 10px;
        }

        @keyframes floatCloud {
            0% { transform: translateX(-4%); }
            50% { transform: translateX(4%); }
            100% { transform: translateX(-4%); }
        }
        .animate-cloud {
            animation: floatCloud 22s ease-in-out infinite;
        }
    </style>
</head>
<body class="h-screen w-screen relative overflow-hidden">

    <div class="absolute inset-0 z-0 pointer-events-none opacity-40 animate-cloud">
        <div class="absolute top-10 left-8 w-52 h-20 bg-white rounded-full blur-xl"></div>
        <div class="absolute top-16 right-12 w-72 h-24 bg-white rounded-full blur-xl"></div>
        <div class="absolute top-6 left-1/3 w-64 h-16 bg-white rounded-full blur-lg"></div>
    </div>

    <!-- Canvas for Flowers and Particles -->
    <canvas id="flowerCanvas"></canvas>

    <div id="textOverlay" class="absolute top-8 left-0 right-0 z-20 text-center pointer-events-none px-4 transition-all duration-700">
        <h1 id="mainTitle" class="text-3xl sm:text-5xl font-bold text-slate-800 font-handwriting drop-shadow-sm mb-2">
            Từ một bông hoa nhỏ...
        </h1>
        <p id="subTitle" class="text-xs sm:text-sm text-rose-600 font-semibold bg-white/80 inline-block px-6 py-2 rounded-full backdrop-blur-md border border-rose-200/80 shadow-md">
            Chạm vào bông hoa, cả một vườn thương.
        </p>
    </div>

    <div id="cardModal" class="fixed inset-0 z-40 flex items-center justify-center p-4 opacity-0 pointer-events-none transition-all duration-700 ease-out transform scale-95">
        <div class="glass-card rounded-3xl p-6 sm:p-8 max-w-lg w-full max-h-[88vh] flex flex-col relative border border-rose-200 shadow-2xl">
            
            <!-- Close Button -->
            <button onclick="closeCard()" class="absolute top-4 right-4 text-slate-400 hover:text-rose-600 p-2 rounded-full hover:bg-rose-50 transition-colors duration-200">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                </svg>
            </button>

            <!-- Card Header Icon -->
            <div class="text-center mb-2">
                <p class="text-xs font-bold uppercase tracking-widest text-rose-500">Xin chào Thương nhé ,</p>
            </div>

            <!-- Scrollable Content -->
            <div class="overflow-y-auto custom-scrollbar pr-2 space-y-4 text-slate-700 text-sm sm:text-base leading-relaxed">
                <h2 class="text-2xl sm:text-3xl font-bold text-center text-rose-600 font-handwriting py-1">
                    Mong những điều đẹp đẽ luôn nở bên bạn.
                </h2>

                <p class="text-slate-600 text-justify italic border-l-4 border-rose-400 pl-3 py-1.5 bg-rose-50/60 rounded-r-lg">
                    Một bông hoa có thể làm nên một ngày thêm đẹp.<br>
                    Còn bạn, làm thế giới này dịu dàng hơn.
                </p>

                <p class="text-justify">
                    Nhân ngày <strong class="text-rose-600 font-semibold">20/10, chúc bạn luôn được yêu thương, trân trọng</strong> và có thật nhiều niềm vui. Mong bạn luôn bình yên trong tâm hồn, tự tin và rạng rỡ tỏa sáng theo cách riêng của mình.
                </p>

                <p class="text-justify">
                    Hôm nay và cả những ngày sau, hãy cứ như những bông hoa xinh đẹp nhất nhé.
                </p>

                <div class="pt-4 text-right">
                    <p class="font-bold text-rose-600 text-lg">Gửi bạn thật nhiều thương yêu ♡</p>
                    <p class="text-xs text-slate-400 font-caveat text-lg mt-0.5">~ ngàn vườn hoa ~</p>
                </div>
            </div>

            <!-- Modal Action -->
            <div class="mt-5 pt-3 border-t border-rose-100 flex justify-center">
                <button onclick="closeCard()" class="px-8 py-2.5 bg-gradient-to-r from-rose-500 via-pink-500 to-rose-400 text-white font-semibold text-sm rounded-full shadow-lg hover:shadow-rose-300/60 transition-all transform active:scale-95">
                    Ngắm nhìn vườn hoa ❀
                </button>
            </div>
        </div>
    </div>

    <div id="controlBar" class="fixed bottom-6 left-0 right-0 z-30 flex flex-wrap justify-center items-center gap-2 sm:gap-3 px-4 opacity-0 transform translate-y-8 pointer-events-none transition-all duration-700">
        <!-- Re-open Letter -->
        <button onclick="openCard()" class="px-5 py-2.5 bg-white/90 hover:bg-white text-slate-700 font-semibold text-xs sm:text-sm rounded-full shadow-md hover:shadow-xl backdrop-blur-md border border-rose-200 transition-all flex items-center gap-2 transform hover:-translate-y-0.5 active:scale-95">
            <span>Đọc lại thiệp</span>
        </button>

        <!-- Re-bloom Garden -->
        <button onclick="bloomAgain()" class="px-5 py-2.5 bg-gradient-to-r from-rose-500 to-pink-500 hover:from-rose-600 hover:to-pink-600 text-white font-semibold text-xs sm:text-sm rounded-full shadow-lg hover:shadow-rose-300/50 transition-all flex items-center gap-2 transform hover:-translate-y-0.5 active:scale-95">
            <span>Cho hoa nở lại</span>
        </button>

        <!-- Toggle Sound -->
        <button id="audioBtn" onclick="toggleAudio()" class="px-5 py-2.5 bg-white/90 hover:bg-white text-slate-700 font-semibold text-xs sm:text-sm rounded-full shadow-md hover:shadow-xl backdrop-blur-md border border-rose-200 transition-all flex items-center gap-2 transform hover:-translate-y-0.5 active:scale-95">
            <span id="audioIcon">🎵</span>
            <span id="audioText">Bật nhạc</span>
        </button>
    </div>

    <script>
        class SoftAudioSynth {
            constructor() {
                this.ctx = null;
                this.isPlaying = false;
                this.timer = null;
                this.step = 0;
                this.notes = [
                    523.25, 659.25, 783.99, 1046.50, // C5, E5, G5, C6
                    587.33, 698.46, 880.00, 1174.66, // D5, F5, A5, D6
                    659.25, 783.99, 987.77, 1318.51, // E5, G5, B5, E6
                    698.46, 880.00, 1046.50, 1396.91 // F5, A5, C6, F6
                ];
            }

            init() {
                if (!this.ctx) {
                    const AudioCtx = window.AudioContext || window.webkitAudioContext;
                    this.ctx = new AudioCtx();
                }
            }

            playTone(freq, duration = 2.8) {
                if (!this.ctx || this.ctx.state === 'suspended') return;

                const osc = this.ctx.createOscillator();
                const gain = this.ctx.createGain();

                osc.type = 'sine';
                osc.frequency.setValueAtTime(freq, this.ctx.currentTime);

                gain.gain.setValueAtTime(0.0001, this.ctx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.09, this.ctx.currentTime + 0.08);
                gain.gain.exponentialRampToValueAtTime(0.0001, this.ctx.currentTime + duration);

                osc.connect(gain);
                gain.connect(this.ctx.destination);

                osc.start();
                osc.stop(this.ctx.currentTime + duration);
            }

            start() {
                this.init();
                if (this.ctx.state === 'suspended') {
                    this.ctx.resume();
                }
                this.isPlaying = true;
                this.step = 0;

                const playLoop = () => {
                    if (!this.isPlaying) return;

                    const noteFreq = this.notes[this.step % this.notes.length];
                    this.playTone(noteFreq, 3.0);

                    if (this.step % 3 === 0) {
                        this.playTone(noteFreq * 0.5, 3.5); // Warm bass note
                    }

                    this.step++;
                    this.timer = setTimeout(playLoop, 460 + Math.random() * 140);
                };

                playLoop();
            }

            stop() {
                this.isPlaying = false;
                if (this.timer) clearTimeout(this.timer);
            }

            toggle() {
                if (this.isPlaying) {
                    this.stop();
                    return false;
                } else {
                    this.start();
                    return true;
                }
            }
        }

        const audioSynth = new SoftAudioSynth();

        function toggleAudio() {
            const isNowPlaying = audioSynth.toggle();
            const icon = document.getElementById('audioIcon');
            const text = document.getElementById('audioText');
            if (isNowPlaying) {
                icon.innerText = '🎶';
                text.innerText = 'Tắt nhạc';
            } else {
                icon.innerText = '🎵';
                text.innerText = 'Bật nhạc';
            }
        }

        const canvas = document.getElementById('flowerCanvas');
        const ctx = canvas.getContext('2d');

        let width = canvas.width = window.innerWidth;
        let height = canvas.height = window.innerHeight;

        window.addEventListener('resize', () => {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
            if (state === 'bloomed') {
                generateGarden();
            } else {
                initSingleCenterRose();
            }
        });

        let state = 'initial'; // 'initial' | 'blooming' | 'bloomed'

        // Ambient Falling Petals & Sparkles
        class Particle {
            constructor(type) {
                this.type = type; // 'petal' | 'sparkle'
                this.reset();
            }

            reset() {
                this.x = Math.random() * width;
                this.y = -20 - Math.random() * 100;
                this.size = this.type === 'petal' ? 8 + Math.random() * 10 : 2 + Math.random() * 4;
                this.speedY = 0.6 + Math.random() * 1.2;
                this.speedX = (Math.random() - 0.5) * 0.8;
                this.rotation = Math.random() * Math.PI * 2;
                this.rotSpeed = (Math.random() - 0.5) * 0.03;
                this.opacity = 0.3 + Math.random() * 0.6;
                this.color = ['#f472b6', '#fb7185', '#fda4af', '#fef08a', '#c084fc'][Math.floor(Math.random() * 5)];
            }

            update() {
                this.y += this.speedY;
                this.x += Math.sin(this.y * 0.02) * 0.6 + this.speedX;
                this.rotation += this.rotSpeed;

                if (this.y > height + 20) {
                    this.reset();
                }
            }

            draw() {
                ctx.save();
                ctx.translate(this.x, this.y);
                ctx.rotate(this.rotation);
                ctx.globalAlpha = this.opacity;

                if (this.type === 'petal') {
                    ctx.fillStyle = this.color;
                    ctx.beginPath();
                    ctx.moveTo(0, 0);
                    ctx.bezierCurveTo(this.size, -this.size, this.size * 1.5, this.size, 0, this.size * 1.5);
                    ctx.bezierCurveTo(-this.size * 1.5, this.size, -this.size, -this.size, 0, 0);
                    ctx.fill();
                } else {
                    ctx.fillStyle = '#fff';
                    ctx.shadowColor = this.color;
                    ctx.shadowBlur = 8;
                    ctx.beginPath();
                    ctx.arc(0, 0, this.size, 0, Math.PI * 2);
                    ctx.fill();
                }

                ctx.restore();
            }
        }

        const particles = Array.from({ length: 35 }, (_, i) => new Particle(i % 3 === 0 ? 'sparkle' : 'petal'));

        const ORGANIC_PALETTES = [
            // Deep Velvet Rose (Red/Magenta)
            { dark: '#881337', mid: '#e11d48', light: '#fda4af', highlight: '#fff1f2' },
            // Soft Blush Pink Rose
            { dark: '#9d174d', mid: '#f43f5e', light: '#fbcfe8', highlight: '#ffffff' },
            // Coral / Peach Sunset Rose
            { dark: '#9a3412', mid: '#f97316', light: '#ffedd5', highlight: '#fff7ed' },
            // Creamy Canary Yellow Rose
            { dark: '#854d0e', mid: '#eab308', light: '#fef08a', highlight: '#fefce8' },
            // Royal Purple / Lavender Rose
            { dark: '#581c87', mid: '#a855f7', light: '#e9d5ff', highlight: '#faf5ff' },
            // Powder Sky Blue Rose
            { dark: '#1e3a8a', mid: '#3b82f6', light: '#bfdbfe', highlight: '#eff6ff' },
            // Gentle Mint Sage Rose
            { dark: '#14532d', mid: '#22c55e', light: '#bbf7d0', highlight: '#f0fdf4' }
        ];

        class LushRoseStem {
            constructor(x, targetY, radius, palette, isBud = false, delay = 0) {
                this.x = Number.isFinite(x) ? x : width / 2;
                this.startY = height + 40;
                this.currentY = this.startY;
                this.targetY = Number.isFinite(targetY) ? targetY : height * 0.5;
                this.radius = Number.isFinite(radius) ? radius : 36;
                this.palette = palette || ORGANIC_PALETTES[0];
                this.isBud = isBud;
                this.delay = delay;

                this.growthProgress = 0;
                this.bloomProgress = 0;

                this.sway = 0;
                this.swayOffset = Math.random() * Math.PI * 2;
                this.swaySpeed = 0.01 + Math.random() * 0.008;

                this.stemCurve = (Math.random() - 0.5) * 40;
                this.leafSide = Math.random() > 0.5 ? 1 : -1;
                this.petalSeed = Math.random() * 10;
            }

            update(time) {
                if (this.delay > 0) {
                    this.delay -= 16;
                    return;
                }

                // Growth Phase
                if (this.growthProgress < 1) {
                    this.growthProgress += 0.018;
                    if (this.growthProgress > 1) this.growthProgress = 1;
                    const hDiff = this.startY - this.targetY;
                    this.currentY = this.startY - hDiff * easeOutCubic(this.growthProgress);
                } 
                // Bloom Phase
                else if (this.bloomProgress < 1) {
                    this.bloomProgress += 0.022;
                    if (this.bloomProgress > 1) this.bloomProgress = 1;
                }

                const swayAmp = 7 * (1 - (this.targetY / height));
                this.sway = Math.sin((time || 0) * this.swaySpeed + this.swayOffset) * swayAmp;
            }

            draw() {
                if (this.delay > 0) return;

                const topX = this.x + (this.sway || 0);
                const topY = this.currentY;

                ctx.save();

                // 1. Draw Organic Stem with natural gradient & curvature
                const ctrlX = this.x + this.stemCurve + (this.sway || 0) * 0.5;
                const ctrlY = (this.startY + topY) / 2;

                ctx.beginPath();
                ctx.moveTo(this.x, this.startY);
                ctx.quadraticCurveTo(ctrlX, ctrlY, topX, topY);

                const stemGrad = ctx.createLinearGradient(this.x, this.startY, topX, topY);
                stemGrad.addColorStop(0, '#14532d');
                stemGrad.addColorStop(0.5, '#15803d');
                stemGrad.addColorStop(1, '#22c55e');

                ctx.strokeStyle = stemGrad;
                ctx.lineWidth = Math.max(3.5, this.radius * 0.14);
                ctx.lineCap = 'round';
                ctx.stroke();

                // Stem thorns
                if (this.radius > 28) {
                    this.drawThorn(this.x + (ctrlX - this.x) * 0.4, (this.startY + ctrlY) / 2, -1);
                    this.drawThorn(this.x + (ctrlX - this.x) * 0.7, (ctrlY + topY) / 2, 1);
                }

                // 2. Draw Leaves with veins
                if (this.growthProgress > 0.25) {
                    const lProg = Math.min(1, (this.growthProgress - 0.25) / 0.75);
                    this.drawOrganicLeaf(this.x + (ctrlX - this.x) * 0.3, this.startY - (this.startY - ctrlY) * 0.6, lProg, this.leafSide);
                    if (this.radius > 24) {
                        this.drawOrganicLeaf(ctrlX, ctrlY, lProg, -this.leafSide);
                    }
                }

                // 3. Draw Organic Flower Head
                if (this.growthProgress > 0.45) {
                    const bProg = Math.min(1, (this.growthProgress - 0.45) / 0.55) * this.bloomProgress;
                    if (this.isBud) {
                        this.drawOrganicBud(topX, topY, this.radius * 0.75, bProg);
                    } else {
                        this.drawLushRoseHead(topX, topY, this.radius, bProg);
                    }
                }

                ctx.restore();
            }

            drawThorn(x, y, side) {
                ctx.save();
                ctx.fillStyle = '#14532d';
                ctx.beginPath();
                ctx.moveTo(x, y);
                ctx.quadraticCurveTo(x + side * 8, y - 2, x + side * 10, y + 6);
                ctx.quadraticCurveTo(x + side * 3, y + 4, x, y);
                ctx.fill();
                ctx.restore();
            }

            drawOrganicLeaf(x, y, progress, side) {
                ctx.save();
                ctx.translate(x, y);
                ctx.scale(progress, progress);
                ctx.rotate(side * 0.55);

                const leafLen = 42;
                const leafW = 18;

                // Leaf shape
                const leafGrad = ctx.createLinearGradient(0, 0, side * leafW, -leafLen);
                leafGrad.addColorStop(0, '#14532d');
                leafGrad.addColorStop(0.6, '#15803d');
                leafGrad.addColorStop(1, '#4ade80');

                ctx.fillStyle = leafGrad;
                ctx.beginPath();
                ctx.moveTo(0, 0);
                ctx.bezierCurveTo(side * leafW * 1.5, -leafLen * 0.3, side * leafW * 1.2, -leafLen * 0.8, 0, -leafLen);
                ctx.bezierCurveTo(-side * leafW * 0.4, -leafLen * 0.7, -side * leafW * 0.2, -leafLen * 0.3, 0, 0);
                ctx.fill();

                // Center leaf vein
                ctx.strokeStyle = 'rgba(255, 255, 255, 0.4)';
                ctx.lineWidth = 1.2;
                ctx.beginPath();
                ctx.moveTo(0, 0);
                ctx.quadraticCurveTo(side * 3, -leafLen * 0.5, 0, -leafLen);
                ctx.stroke();

                ctx.restore();
            }

            drawOrganicBud(x, y, radius, progress) {
                const r = radius * progress;
                if (r <= 2) return;

                ctx.save();
                ctx.translate(x, y);

                // Green Sepal base
                ctx.fillStyle = '#15803d';
                ctx.beginPath();
                ctx.arc(0, r * 0.2, r * 0.5, 0, Math.PI);
                ctx.fill();

                // Petal core
                const budGrad = ctx.createLinearGradient(0, -r, 0, r * 0.5);
                budGrad.addColorStop(0, this.palette.light);
                budGrad.addColorStop(0.6, this.palette.mid);
                budGrad.addColorStop(1, this.palette.dark);

                ctx.fillStyle = budGrad;
                ctx.beginPath();
                ctx.moveTo(-r * 0.6, 0);
                ctx.bezierCurveTo(-r * 0.6, -r * 1.3, r * 0.6, -r * 1.3, r * 0.6, 0);
                ctx.closePath();
                ctx.fill();

                ctx.restore();
            }

            drawLushRoseHead(x, y, radius, progress) {
                const r = radius * progress;
                if (r <= 3) return;

                ctx.save();
                ctx.translate(x, y);

                // Sepals under rose
                ctx.fillStyle = '#15803d';
                for (let i = 0; i < 5; i++) {
                    const ang = (i / 5) * Math.PI * 2;
                    ctx.save();
                    ctx.rotate(ang);
                    ctx.beginPath();
                    ctx.moveTo(0, 0);
                    ctx.quadraticCurveTo(r * 0.3, -r * 0.2, r * 0.1, -r * 1.05);
                    ctx.quadraticCurveTo(-r * 0.2, -r * 0.2, 0, 0);
                    ctx.fill();
                    ctx.restore();
                }

                // Layer 1: Outer Large Soft Petals (5-6 Petals)
                const outerPetalCount = 6;
                for (let i = 0; i < outerPetalCount; i++) {
                    const angle = (i / outerPetalCount) * Math.PI * 2 + this.petalSeed;
                    this.drawSinglePetal(angle, r * 0.95, r * 0.7, this.palette.mid, this.palette.light, this.palette.highlight);
                }

                // Layer 2: Middle Overlapping Petals (6 Petals rotated offset)
                const midPetalCount = 6;
                for (let i = 0; i < midPetalCount; i++) {
                    const angle = (i / midPetalCount) * Math.PI * 2 + 0.5 + this.petalSeed;
                    this.drawSinglePetal(angle, r * 0.72, r * 0.55, this.palette.dark, this.palette.mid, this.palette.light);
                }

                // Layer 3: Inner Petal Cup (5 Petals)
                const innerPetalCount = 5;
                for (let i = 0; i < innerPetalCount; i++) {
                    const angle = (i / innerPetalCount) * Math.PI * 2 + 1.1 + this.petalSeed;
                    this.drawSinglePetal(angle, r * 0.48, r * 0.38, this.palette.dark, this.palette.mid, this.palette.mid);
                }

                // Layer 4: Tight Spiraling Heart Center
                const centerGrad = ctx.createRadialGradient(0, 0, r * 0.02, 0, 0, r * 0.28);
                centerGrad.addColorStop(0, this.palette.dark);
                centerGrad.addColorStop(0.7, this.palette.mid);
                centerGrad.addColorStop(1, this.palette.light);

                ctx.fillStyle = centerGrad;
                ctx.beginPath();
                ctx.arc(0, 0, r * 0.26, 0, Math.PI * 2);
                ctx.fill();

                // Inner core swirl fold
                ctx.strokeStyle = 'rgba(255, 255, 255, 0.7)';
                ctx.lineWidth = Math.max(1, r * 0.04);
                ctx.beginPath();
                let a = 0;
                let rad = r * 0.04;
                ctx.moveTo(0, 0);
                while (a < Math.PI * 3.5) {
                    a += 0.3;
                    rad = (a / (Math.PI * 3.5)) * (r * 0.22);
                    const sx = Math.cos(a + this.petalSeed) * rad;
                    const sy = Math.sin(a + this.petalSeed) * rad;
                    ctx.lineTo(sx, sy);
                }
                ctx.stroke();

                // Dewdrop Effect on 1 in 3 roses
                if (this.radius > 32 && Math.floor(this.petalSeed) % 2 === 0) {
                    ctx.fillStyle = 'rgba(255, 255, 255, 0.8)';
                    ctx.beginPath();
                    ctx.arc(-r * 0.35, -r * 0.2, 2.5, 0, Math.PI * 2);
                    ctx.fill();
                    ctx.fillStyle = 'rgba(255, 255, 255, 0.4)';
                    ctx.beginPath();
                    ctx.arc(-r * 0.33, -r * 0.18, 1, 0, Math.PI * 2);
                    ctx.fill();
                }

                ctx.restore();
            }

            drawSinglePetal(angle, distance, size, colDark, colMid, colLight) {
                ctx.save();
                ctx.rotate(angle);
                ctx.translate(0, -distance * 0.5);

                // Soft petal drop shadow for depth
                ctx.shadowColor = 'rgba(0, 0, 0, 0.12)';
                ctx.shadowBlur = 6;
                ctx.shadowOffsetY = 3;

                // Organic Petal Gradient
                const petalGrad = ctx.createRadialGradient(0, size * 0.3, size * 0.1, 0, -size * 0.2, size * 0.9);
                petalGrad.addColorStop(0, colDark);
                petalGrad.addColorStop(0.5, colMid);
                petalGrad.addColorStop(0.9, colLight);
                petalGrad.addColorStop(1, colLight);

                ctx.fillStyle = petalGrad;

                // Heart-like organic petal curve
                ctx.beginPath();
                ctx.moveTo(0, size * 0.4);
                ctx.bezierCurveTo(-size * 0.85, size * 0.2, -size * 0.9, -size * 0.7, 0, -size);
                ctx.bezierCurveTo(size * 0.9, -size * 0.7, size * 0.85, size * 0.2, 0, size * 0.4);
                ctx.closePath();
                ctx.fill();

                // Delicate Petal Highlight Edge Line
                ctx.shadowColor = 'transparent';
                ctx.strokeStyle = 'rgba(255, 255, 255, 0.35)';
                ctx.lineWidth = 1;
                ctx.beginPath();
                ctx.bezierCurveTo(-size * 0.7, -size * 0.5, 0, -size * 0.95, size * 0.7, -size * 0.5);
                ctx.stroke();

                ctx.restore();
            }
        }

        function easeOutCubic(t) {
            return 1 - Math.pow(1 - t, 3);
        }

        let flowers = [];

        function initSingleCenterRose() {
            flowers = [];
            const centerX = width / 2;
            const targetY = height * 0.52;

            const singleRose = new LushRoseStem(centerX, targetY, 52, ORGANIC_PALETTES[1], false, 0);
            singleRose.growthProgress = 1;
            singleRose.currentY = targetY;
            singleRose.bloomProgress = 1;

            flowers.push(singleRose);
        }

        function generateGarden() {
            flowers = [];

            // Dense garden layout matching video clip
            const flowerCount = Math.floor(width / 22) + 16;

            for (let i = 0; i < flowerCount; i++) {
                const xPercent = (i + 0.5) / flowerCount + (Math.random() - 0.5) * 0.035;
                const x = xPercent * width;

                // Layer depth (0 = foreground, 1 = background)
                const depth = Math.random();
                const targetY = height * (0.36 + depth * 0.5);

                const radius = (1.15 - depth * 0.42) * 36;
                const palette = ORGANIC_PALETTES[Math.floor(Math.random() * ORGANIC_PALETTES.length)];

                const isBud = Math.random() < 0.2; // ~20% buds
                const delay = Math.random() * 1200; // Staggered blooming

                const stem = new LushRoseStem(x, targetY, radius, palette, isBud, delay);
                flowers.push(stem);
            }

            // Sort background flowers to render first
            flowers.sort((a, b) => a.targetY - b.targetY);
        }

        function plantRoseAt(x, y) {
            const palette = ORGANIC_PALETTES[Math.floor(Math.random() * ORGANIC_PALETTES.length)];
            const radius = 28 + Math.random() * 18;
            const newStem = new LushRoseStem(x, y, radius, palette, false, 0);
            flowers.push(newStem);
            flowers.sort((a, b) => a.targetY - b.targetY);
        }

        // Initialize single flower state
        initSingleCenterRose();

        function animate(time = 0) {
            ctx.clearRect(0, 0, width, height);

            // Ambient background particles & floating petals
            particles.forEach(p => {
                p.update();
                p.draw();
            });

            // Soft Glow around initial single rose
            if (state === 'initial' && flowers.length > 0) {
                const f = flowers[0];
                const glowGrad = ctx.createRadialGradient(f.x, f.currentY, 10, f.x, f.currentY, 200);
                glowGrad.addColorStop(0, 'rgba(251, 113, 133, 0.3)');
                glowGrad.addColorStop(1, 'rgba(251, 113, 133, 0)');
                ctx.fillStyle = glowGrad;
                ctx.beginPath();
                ctx.arc(f.x, f.currentY, 200, 0, Math.PI * 2);
                ctx.fill();
            }

            // Draw Flowers
            flowers.forEach(f => {
                f.update(time * 0.002);
                f.draw();
            });

            requestAnimationFrame(animate);
        }

        animate();

        canvas.addEventListener('click', (e) => {
            if (state === 'initial') {
                startGardenBloom();
            } else {
                plantRoseAt(e.clientX, e.clientY);
            }
        });

        canvas.addEventListener('touchstart', (e) => {
            if (e.touches.length > 0) {
                const touch = e.touches[0];
                if (state === 'initial') {
                    startGardenBloom();
                } else {
                    plantRoseAt(touch.clientX, touch.clientY);
                }
            }
        }, { passive: true });

        function startGardenBloom() {
            if (state !== 'initial') return;
            state = 'blooming';

            if (!audioSynth.isPlaying) {
                toggleAudio();
            }

            const mainTitle = document.getElementById('mainTitle');
            const subTitle = document.getElementById('subTitle');

            mainTitle.style.opacity = '0';
            subTitle.style.opacity = '0';

            setTimeout(() => {
                mainTitle.innerText = "Từ một bông hoa, cả một vườn thương.";
                subTitle.innerText = "Chạm vào bất cứ đâu để trồng thêm những bông hoa xinh đẹp ✨";
                mainTitle.style.opacity = '1';
                subTitle.style.opacity = '1';
            }, 400);

            generateGarden();

            const controlBar = document.getElementById('controlBar');
            controlBar.classList.remove('opacity-0', 'translate-y-8', 'pointer-events-none');

            setTimeout(() => {
                state = 'bloomed';
                openCard();
            }, 1600);
        }

        function openCard() {
            const modal = document.getElementById('cardModal');
            modal.classList.remove('opacity-0', 'pointer-events-none', 'scale-95');
            modal.classList.add('scale-100');
        }

        function closeCard() {
            const modal = document.getElementById('cardModal');
            modal.classList.add('opacity-0', 'pointer-events-none', 'scale-95');
            modal.classList.remove('scale-100');
        }

        function bloomAgain() {
            closeCard();
            state = 'blooming';
            generateGarden();

            setTimeout(() => {
                state = 'bloomed';
                openCard();
            }, 1800);
        }
    </script>
</body>
</html>
