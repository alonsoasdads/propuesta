[index.html.txt](https://github.com/user-attachments/files/23111734/index.html.txt)
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Propuesta para Tino 💫</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.2/dist/confetti.browser.min.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Luckiest+Guy&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            min-height: 100vh;
            background: #000;
            color: white;
            font-family: 'Luckiest Guy', cursive;
            overflow: hidden;
            position: relative;
        }
        
        /* Fondo synthwave turquesa */
        .synthwave-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                45deg,
                #005f73 0%,
                #0a9396 25%,
                #48cae4 50%,
                #90e0ef 75%,
                #caf0f8 100%
            );
            z-index: -4;
        }
        
        /* Sol turquesa */
        .synth-sun {
            position: absolute;
            top: 5%;
            right: 10%;
            width: 200px;
            height: 200px;
            background: radial-gradient(circle, #caf0f8 0%, #90e0ef 30%, #48cae4 60%, transparent 80%);
            border-radius: 50%;
            filter: blur(15px) brightness(1.5);
            opacity: 0.8;
            animation: pulse 3s ease-in-out infinite;
            box-shadow: 0 0 100px #90e0ef;
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 0.8; }
            50% { transform: scale(1.2); opacity: 1; }
        }
        
        /* ÁRBOLES GIGANTES */
        .trees {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
        
        .tree {
            position: absolute;
            bottom: 0;
        }
        
        .tree-trunk {
            width: 30px;
            height: 70vh;
            background: linear-gradient(to top, #5d4037, #795548);
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }
        
        .tree-top {
            position: absolute;
            bottom: 70vh;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 0;
            border-left: 120px solid transparent;
            border-right: 120px solid transparent;
            border-bottom: 200px solid #48cae4;
            filter: blur(3px);
            box-shadow: 0 0 40px #48cae4;
            z-index: 2;
        }
        
        .tree-1 { left: 5%; }
        .tree-2 { left: 15%; transform: scale(1.1); }
        .tree-3 { left: 25%; transform: scale(0.9); }
        .tree-4 { left: 35%; transform: scale(1.2); }
        .tree-5 { left: 45%; transform: scale(1.0); }
        .tree-6 { left: 55%; transform: scale(1.3); }
        .tree-7 { left: 65%; transform: scale(0.8); }
        .tree-8 { left: 75%; transform: scale(1.1); }
        .tree-9 { left: 85%; transform: scale(0.9); }
        .tree-10 { left: 95%; transform: scale(1.2); }
        
        .container {
            position: relative;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
            z-index: 10;
        }
        
        .content {
            background: rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            border: none;
            border-radius: 15px;
            padding: 40px 30px;
            text-align: center;
            max-width: 600px;
            width: 100%;
            box-shadow: none;
        }
        
        .screen {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            animation: slideIn 0.7s ease-out;
        }
        
        @keyframes slideIn {
            0% { 
                opacity: 0; 
                transform: translateY(40px) scale(0.94); 
            }
            100% { 
                opacity: 1; 
                transform: translateY(0) scale(1); 
            }
        }
        
        .hidden {
            display: none !important;
        }
        
        .metal-text {
            font-family: 'Luckiest Guy', cursive;
            font-size: 2.5rem;
            background: linear-gradient(180deg, #fff 0%, #caf0f8 15%, #90e0ef 40%, #ffffff 50%, #caf0f8 60%, #48cae4 100%);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 
                0 1px 0 rgba(255,255,255,0.85),
                0 2px 0 rgba(255,255,255,0.6),
                0 6px 12px rgba(0,0,0,0.6),
                0 10px 30px rgba(0,0,0,0.55);
            margin-bottom: 30px;
            position: relative;
            display: inline-block;
        }
        
        .metal-text.big {
            font-size: 4rem;
        }
        
        .metal-text.medium {
            font-size: 2.8rem;
        }
        
        .metal-text.small {
            font-size: 1rem;
        }

        .message-box {
            background: rgba(0, 0, 0, 0.4);
            border: 1px solid rgba(144, 224, 239, 0.3);
            border-radius: 15px;
            padding: 20px;
            margin-top: 20px;
            max-width: 500px;
            max-height: 300px;
            overflow-y: auto;
            text-align: left;
            backdrop-filter: blur(5px);
        }

        .message-text {
            font-family: 'Arial', sans-serif;
            font-size: 1rem;
            line-height: 1.6;
            color: rgba(255, 255, 255, 0.9);
        }
        
        .buttons {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            justify-content: center;
            margin-top: 20px;
        }
        
        .btn {
            padding: 15px 25px;
            border: none;
            border-radius: 50px;
            font-family: 'Luckiest Guy', cursive;
            font-size: 1.2rem;
            cursor: pointer;
            transition: all 0.3s ease;
            min-width: 120px;
        }
        
        .btn-primary {
            background: linear-gradient(180deg, #caf0f8 0%, #90e0ef 50%, #48cae4 100%);
            color: #005f73;
            box-shadow: 
                0 10px 30px rgba(0,0,0,0.45),
                0 0 30px rgba(144, 224, 239, 0.7);
            font-weight: bold;
        }
        
        .btn-ghost {
            background: rgba(144, 224, 239, 0.1);
            border: 2px solid rgba(144, 224, 239, 0.5);
            color: #90e0ef;
            box-shadow: 0 0 20px rgba(144, 224, 239, 0.3);
        }
        
        .btn:active {
            transform: translateY(2px);
        }
        
        .music-controls {
            position: absolute;
            top: 20px;
            right: 20px;
            z-index: 100;
        }
        
        .music-btn {
            background: rgba(144, 224, 239, 0.2);
            border: 1px solid rgba(144, 224, 239, 0.5);
            color: #90e0ef;
            padding: 8px 15px;
            border-radius: 20px;
            cursor: pointer;
            font-family: 'Arial', sans-serif;
            font-size: 0.8rem;
            box-shadow: 0 0 10px rgba(144, 224, 239, 0.3);
        }

        #confetti-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 100;
        }

        .error-message {
            display: none;
            background: rgba(255, 0, 0, 0.8);
            color: white;
            padding: 10px;
            border-radius: 5px;
            margin: 10px 0;
        }
    </style>
</head>
<body>
    <canvas id="confetti-canvas"></canvas>
    
    <audio id="bg-music" loop>
        <source src="cancion_propuesta.mp3" type="audio/mp3">
        <source src="cancion_propuesta.mp3" type="audio/mpeg">
        Tu navegador no soporta el elemento de audio.
    </audio>
    
    <div class="synthwave-bg"></div>
    
    <div class="trees">
        <div class="tree tree-1">
            <div class="tree-trunk"></div>
            <div class="tree-top"></div>
        </div>
        <div class="tree tree-2">
            <div class="tree-trunk"></div>
            <div class="tree-top"></div>
        </div>
        <div class="tree tree-3">
            <div class="tree-trunk"></div>
            <div class="tree-top"></div>
        </div>
        <div class="tree tree-4">
            <div class="tree-trunk"></div>
            <div class="tree-top"></div>
        </div>
        <div class="tree tree-5">
            <div class="tree-trunk"></div>
            <div class="tree-top"></div>
        </div>
        <div class="tree tree-6">
            <div class="tree-trunk"></div>
            <div class="tree-top"></div>
        </div>
        <div class="tree tree-7">
            <div class="tree-trunk"></div>
            <div class="tree-top"></div>
        </div>
        <div class="tree tree-8">
            <div class="tree-trunk"></div>
            <div class="tree-top"></div>
        </div>
        <div class="tree tree-9">
            <div class="tree-trunk"></div>
            <div class="tree-top"></div>
        </div>
        <div class="tree tree-10">
            <div class="tree-trunk"></div>
            <div class="tree-top"></div>
        </div>
    </div>
    
    <div class="music-controls">
        <button class="music-btn" onclick="toggleMusic()">🎵 Reproducir Música</button>
    </div>
    
    <div class="container">
        <div class="content">
            <div id="screen1" class="screen">
                <h1 class="metal-text">Tino, ¿quieres pololear conmigo?</h1>
                <div class="buttons">
                    <button class="btn btn-primary" onclick="handleYes()">SÍ</button>
                    <button class="btn btn-ghost" onclick="showScreen(3)">mmmh no lo sé Rick</button>
                </div>
            </div>
            
            <div id="screen2" class="screen hidden">
                <h1 class="metal-text big">¡QUE VIVAN LOS NOVIOS! 💑</h1>
                <div class="message-box">
                    <p class="message-text">
                        Quiero que sepas que esta pequeña caja de texto me faltarán muchísimos caracteres para poder decirte todo lo que quiero. Pero quiero que sepas que en este breve periodo de tiempo desde que te he conocido, has reescrito por completo como veo el querer.<br><br>
                        
                        Yo no veo un mañana sin verte y por eso me atreví a hacer esta completa ñoñería para llegar a tu corazón con lo que más me has dicho que te ha gustado de mí.<br><br>
                        
                        Es por eso que de ahora en adelante, quiero que estés en mi día a día, que si voy a un lugar, siempre llevarte conmigo de una forma u otra.<br><br>
                        
                        Te adoro, te quiero y te amo. 💫
                    </p>
                </div>
            </div>
            
            <div id="screen3" class="screen hidden">
                <h1 class="metal-text medium">¿CÓMO QUE NO? 😢</h1>
                <p class="metal-text small">Volverás al inicio en 5 segundos...</p>
            </div>
        </div>
    </div>

    <script>
        // Verificar si la música se carga correctamente
        const audio = document.getElementById('bg-music');
        audio.addEventListener('error', function(e) {
            console.log('Error cargando el audio:', e);
            alert('La canción no se pudo cargar. Asegúrate de que el archivo "cancion_propuesta.mp3" esté en la misma carpeta.');
        });

        let currentScreen = 1;
        let timeoutId = null;
        let musicPlaying = false;
        
        audio.volume = 0.7;

        function startMusicOnInteraction() {
            if (!musicPlaying) {
                audio.play().then(() => {
                    musicPlaying = true;
                    document.querySelector('.music-btn').textContent = '🎵 Pausar Música';
                }).catch(e => {
                    console.log("Esperando interacción del usuario para reproducir música");
                });
            }
        }

        document.addEventListener('click', function(event) {
            if (event.target.tagName === 'BUTTON') {
                startMusicOnInteraction();
            }
        });
        
        function toggleMusic() {
            if (musicPlaying) {
                audio.pause();
                document.querySelector('.music-btn').textContent = '🎵 Reproducir Música';
                musicPlaying = false;
            } else {
                audio.play().then(() => {
                    musicPlaying = true;
                    document.querySelector('.music-btn').textContent = '🎵 Pausar Música';
                }).catch(e => {
                    alert("Haz clic en 'SÍ' o 'No' primero para activar la música");
                });
            }
        }
        
        function showScreen(screenNumber) {
            document.getElementById('screen' + currentScreen).classList.add('hidden');
            document.getElementById('screen' + screenNumber).classList.remove('hidden');
            currentScreen = screenNumber;
            
            if (screenNumber === 3) {
                if (timeoutId) clearTimeout(timeoutId);
                timeoutId = setTimeout(() => {
                    showScreen(1);
                }, 5000);
            }
        }
        
        function handleYes() {
            showScreen(2);
            launchConfetti();
        }
        
        function launchConfetti() {
            const canvas = document.getElementById('confetti-canvas');
            const myConfetti = confetti.create(canvas, {
                resize: true,
                useWorker: true
            });
            
            const confettiSettings = {
                particleCount: 200,
                spread: 120,
                origin: { y: 0.6 },
                colors: ['#caf0f8', '#90e0ef', '#48cae4', '#0a9396', '#005f73']
            };
            
            myConfetti(confettiSettings);
            
            setTimeout(() => {
                myConfetti({...confettiSettings, angle: 60, spread: 90});
            }, 250);
            
            setTimeout(() => {
                myConfetti({...confettiSettings, angle: 120, spread: 90});
            }, 500);
        }
        
        document.addEventListener('DOMContentLoaded', function() {
            showScreen(1);
            // Verificar si estamos en un servidor web
            if (window.location.protocol === 'file:') {
                console.log('Ejecutando localmente desde archivo');
            } else {
                console.log('Ejecutando desde servidor web');
            }
        });
    </script>
</body>
</html>
