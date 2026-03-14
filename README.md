<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Shonniiiiiii</title>
    <style>
        body, html {
            margin: 0;
            padding: 0;
            height: 100%;
            width: 100%;
            font-family: 'Segoe UI', Arial, sans-serif;
            overflow: hidden;
            transition: background-color 0.8s;
        }

        /* --- INTERACTIVE ROSE BORDER DECORATIONS --- */
        .rose-decor {
            position: fixed;
            font-size: 80px;
            z-index: 100;
            cursor: pointer; /* Hints that it's interactive */
            transition: transform 0.6s ease-in-out, filter 0.6s;
            pointer-events: auto; /* Required for hover to work */
            display: inline-block; /* Helps with clean animation */
        }

        /* Hover Effect: Spin and Scale Up */
        .rose-decor:hover {
            transform: scale(1.3) rotate(360deg);
            filter: drop-shadow(0 0 10px rgba(255, 77, 109, 0.6));
        }

        /* Corner Positions */
        .top-left { top: 10px; left: 10px; }
        .top-right { top: 10px; right: 10px; }
        .bottom-left { bottom: 10px; left: 10px; }
        .bottom-right { bottom: 10px; right: 10px; }

        /* --- PAGE 1 (PINK) --- */
        #page1 {
            background-color: #fff0f3;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            width: 100%;
            position: absolute;
            z-index: 10;
            transition: opacity 0.8s ease;
            border: 15px solid #ffccd5; /* Soft pink border */
            box-sizing: border-box;
        }

        .container-pink {
            background: white;
            padding: 2.5rem;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(255, 77, 109, 0.2);
            max-width: 400px;
            text-align: center;
            color: #ff4d6d;
        }

        .heart-beat {
            font-size: 60px;
            animation: beat 1.2s infinite;
            display: inline-block;
        }

        @keyframes beat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.15); }
        }

        .btn-next {
            background: #ff4d6d;
            color: white;
            border: none;
            padding: 15px 35px;
            border-radius: 50px;
            font-size: 1.2rem;
            cursor: pointer;
            margin-top: 20px;
            box-shadow: 0 4px 15px rgba(255, 77, 109, 0.4);
            transition: background 0.3s, transform 0.2s;
        }
        .btn-next:hover {
            background: #c9184a;
            transform: scale(1.05);
        }

        /* --- PAGE 2 (GLITTER) --- */
        #page2 {
            background-color: #0a0a0a;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            width: 100%;
            position: absolute;
            opacity: 0;
            visibility: hidden;
            z-index: 5;
            transition: opacity 1s ease;
            border: 15px solid #4a0404; /* Dark wine border */
            box-sizing: border-box;
        }

        .container-dark {
            background: rgba(255, 255, 255, 0.08);
            padding: 40px;
            border-radius: 30px;
            backdrop-filter: blur(15px);
            text-align: center;
            max-width: 500px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            position: relative;
            z-index: 10;
        }

        /* GLITTER TEXT */
        .glitter-text {
            font-size: 2rem;
            font-weight: bold;
            line-height: 1.5;
            background: linear-gradient(to right, #f1c40f 20%, #fff 40%, #f1c40f 60%, #fff 80%);
            background-size: 200% auto;
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: shine 2.5s linear infinite;
        }

        @keyframes shine { to { background-position: 200% center; } }

        /* SPARKLE EFFECT */
        .sparkle {
            position: absolute;
            color: white;
            pointer-events: none;
            animation: fall 4s linear infinite;
            z-index: 8;
        }

        @keyframes fall {
            from { transform: translateY(-10vh) rotate(0deg); opacity: 1; }
            to { transform: translateY(110vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="rose-decor top-left">🌹</div>
    <div class="rose-decor top-right">🌹</div>
    <div class="rose-decor bottom-left">🌹</div>
    <div class="rose-decor bottom-right">🌹</div>

    <div id="page1">
        <div class="container-pink">
            <div class="heart-beat">❤️</div>
            <h1 style="margin: 10px 0;">I'm Sorry!</h1>
            <p style="color: #555; font-size: 1.1rem;">To my dearest Shonniiiiiii,</p>
            <p style="color: #666;">I know I hurt you. Please give me one chance to explain...</p>
            <button class="btn-next" onclick="goToNextPage()">Next →</button>
        </div>
    </div>

    <div id="page2">
        <div class="container-dark">
            <div class="glitter-text">
                m kabhi sad nhi karu ga apko please insta par wapis aa jao baby koi bhi excuse nhi duga sari baate mnaanu ga baby pka promise
            </div>
            <p style="color: white; font-size: 30px; margin-top: 20px;">🥺🙏🌹</p>
        </div>
    </div>

    <script>
        function goToNextPage() {
            // Smooth transition
            document.getElementById('page1').style.opacity = '0';
            setTimeout(() => {
                document.getElementById('page1').style.visibility = 'hidden';
                document.getElementById('page2').style.visibility = 'visible';
                document.getElementById('page2').style.opacity = '1';
                
                // Change border roses to dark, velvet red for page 2
                // (Matches the dark theme automatically)
                const roses = document.querySelectorAll('.rose-decor');
                roses.forEach(r => r.style.filter = "brightness(0.6) sepia(1) hue-rotate(-50deg)");
            }, 800);

            // Start sparkle rain
            setInterval(createSparkle, 400);
        }

        function createSparkle() {
            const sparkle = document.createElement('div');
            sparkle.innerHTML = '✨';
            sparkle.className = 'sparkle';
            sparkle.style.left = Math.random() * 100 + 'vw';
            sparkle.style.animationDuration = (Math.random() * 2 + 2) + 's';
            document.body.appendChild(sparkle);
            setTimeout(() => sparkle.remove(), 4000);
        }
    </script>

</body>
</html>
