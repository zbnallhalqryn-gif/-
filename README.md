<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>رسالة هامة ✨</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;900&display=swap');
        
        body {
            font-family: 'Cairo', sans-serif;
            background-color: #050505;
            margin: 0;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
        }

        /* خلفية جزيئات متحركة */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            z-index: 0;
        }

        .main-card {
            z-index: 10;
            background: rgba(15, 15, 15, 0.8);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 50px;
            padding: 4rem 2rem;
            box-shadow: 0 0 60px rgba(0, 0, 0, 0.8), 0 0 30px rgba(255, 0, 221, 0.15);
            max-width: 90%;
            width: 550px;
            text-align: center;
            transition: all 0.5s ease;
        }

        .neon-text {
            color: #fff;
            text-shadow: 
                0 0 7px #fff,
                0 0 10px #fff,
                0 0 21px #fff,
                0 0 42px #ff00de,
                0 0 82px #ff00de,
                0 0 92px #ff00de;
            animation: pulsate 1.5s infinite alternate;
        }

        @keyframes pulsate {
            100% {
                text-shadow:
                0 0 4px #fff,
                0 0 11px #fff,
                0 0 19px #fff,
                0 0 40px #ff00de,
                0 0 80px #ff00de,
                0 0 90px #ff00de;
            }
            0% {
                text-shadow:
                0 0 2px #fff,
                0 0 4px #fff,
                0 0 6px #fff,
                0 0 10px #ff00de,
                0 0 45px #ff00de,
                0 0 55px #ff00de;
            }
        }

        .reveal-text {
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 0.8s ease forwards;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .gradient-line {
            height: 2px;
            width: 150px;
            background: linear-gradient(90deg, transparent, #ff00de, transparent);
            margin: 2rem auto;
        }
    </style>
</head>
<body>

    <canvas id="bg-canvas"></canvas>

    <div class="main-card reveal-text">
        
        <h1 class="neon-text text-4xl md:text-5xl font-black mb-6 leading-tight">
            كلوو زق انضحك عليكم يا اغبياء
        </h1>

        <div class="gradient-line"></div>

        <div class="space-y-6">
            <p class="text-white text-3xl md:text-4xl font-bold tracking-wide">
                فكررووو زيين وركزوو 😂
            </p>
            
            <p class="text-gray-500 text-lg font-medium opacity-60 tracking-[0.2em] uppercase mt-4">
                H a h a h a h a h a
            </p>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('bg-canvas');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function init() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            particles = [];
            for (let i = 0; i < 120; i++) {
                particles.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 1.5 + 0.5,
                    speedX: (Math.random() - 0.5) * 0.8,
                    speedY: (Math.random() - 0.5) * 0.8,
                    color: Math.random() > 0.5 ? '#ff00de' : '#4deeea'
                });
            }
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => {
                p.x += p.speedX;
                p.y += p.speedY;

                if (p.x < 0 || p.x > canvas.width) p.speedX *= -1;
                if (p.y < 0 || p.y > canvas.height) p.speedY *= -1;

                ctx.beginPath();
                ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                ctx.shadowBlur = 5;
                ctx.shadowColor = p.color;
                ctx.fillStyle = p.color;
                ctx.globalAlpha = 0.4;
                ctx.fill();
            });
            requestAnimationFrame(animate);
        }

        window.addEventListener('resize', init);
        init();
        animate();
    </script>
</body>
</html>

