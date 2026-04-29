# Nagrom.Retrop
hihibyyeye
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Scary Page</title>
    <style>
        body {
            background-color: #000000;
            color: #8b0000;
            font-family: 'Courier New', monospace;
            height: 100vh;
            margin: 0;
            overflow: hidden;
            position: relative;
        }
        
        .russian-text {
            position: absolute;
            color: #660000;
            font-size: 14px;
            opacity: 0.7;
            font-family: 'Arial', sans-serif;
            z-index: 1;
        }
        
        .latin-text {
            position: absolute;
            color: #4a0080;
            font-size: 14px;
            opacity: 0.7;
            font-family: 'Georgia', serif;
            z-index: 1;
        }
        
        .center-message {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 48px;
            font-weight: bold;
            color: #ff0000;
            z-index: 10;
        }
        
        #matrix-canvas {
            position: absolute;
            top: 0;
            left: 0;
            z-index: 0;
        }
    </style>
</head>
<body>
    <canvas id="matrix-canvas"></canvas>
    
    <!-- Russian text scattered across the page -->
    <div class="russian-text" style="top: 5%; left: 10%;">Мы видим тебя</div>
    <div class="russian-text" style="top: 15%; left: 80%;">но ты не видишь нас</div>
    <div class="russian-text" style="top: 25%; left: 30%;">Мы видим тебя</div>
    <div class="russian-text" style="top: 35%; left: 60%;">но ты не видишь нас</div>
    <div class="russian-text" style="top: 45%; left: 15%;">Мы видим тебя</div>
    <div class="russian-text" style="top: 55%; left: 75%;">но ты не видишь нас</div>
    <div class="russian-text" style="top: 65%; left: 25%;">Мы видим тебя</div>
    <div class="russian-text" style="top: 75%; left: 50%;">но ты не видишь нас</div>
    <div class="russian-text" style="top: 85%; left: 35%;">Мы видим тебя</div>
    <div class="russian-text" style="top: 10%; left: 45%;">но ты не видишь нас</div>
    <div class="russian-text" style="top: 20%; left: 65%;">Мы видим тебя</div>
    <div class="russian-text" style="top: 30%; left: 5%;">но ты не видишь нас</div>
    <div class="russian-text" style="top: 40%; left: 85%;">Мы видим тебя</div>
    <div class="russian-text" style="top: 50%; left: 20%;">но ты не видишь нас</div>
    <div class="russian-text" style="top: 60%; left: 70%;">Мы видим тебя</div>
    <div class="russian-text" style="top: 70%; left: 40%;">но ты не видишь нас</div>
    <div class="russian-text" style="top: 80%; left: 90%;">Мы видим тебя</div>
    <div class="russian-text" style="top: 90%; left: 55%;">но ты не видишь нас</div>
    
    <!-- Latin text scattered across the page -->
    <div class="latin-text" style="top: 8%; left: 20%;">Sic volo</div>
    <div class="latin-text" style="top: 12%; left: 70%;">Deus vult</div>
    <div class="latin-text" style="top: 22%; left: 40%;">Sic volo</div>
    <div class="latin-text" style="top: 32%; left: 15%;">Deus vult</div>
    <div class="latin-text" style="top: 42%; left: 85%;">Sic volo</div>
    <div class="latin-text" style="top: 52%; left: 35%;">Deus vult</div>
    <div class="latin-text" style="top: 62%; left: 60%;">Sic volo</div>
    <div class="latin-text" style="top: 72%; left: 25%;">Deus vult</div>
    <div class="latin-text" style="top: 82%; left: 75%;">Sic volo</div>
    <div class="latin-text" style="top: 18%; left: 50%;">Deus vult</div>
    <div class="latin-text" style="top: 28%; left: 10%;">Sic volo</div>
    <div class="latin-text" style="top: 38%; left: 90%;">Deus vult</div>
    <div class="latin-text" style="top: 48%; left: 30%;">Sic volo</div>
    <div class="latin-text" style="top: 58%; left: 65%;">Deus vult</div>
    <div class="latin-text" style="top: 68%; left: 45%;">Sic volo</div>
    <div class="latin-text" style="top: 78%; left: 80%;">Deus vult</div>
    <div class="latin-text" style="top: 88%; left: 15%;">Sic volo</div>
    <div class="latin-text" style="top: 6%; left: 55%;">Deus vult</div>
    
    <!-- Center message -->
    <div class="center-message">nagrom retrop were coming for you</div>
    
    <script>
        // Matrix rain effect using canvas
        const canvas = document.getElementById('matrix-canvas');
        const ctx = canvas.getContext('2d');
        
        // Make the canvas full screen
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        
        // Characters to use in the rain
        const matrix = "ABCDEFGHIJKLMNOPQRSTUVWXYZ123456789@#$%^&*()*&^%+-/~{[|`]}";
        const matrixArray = matrix.split("");
        
        const fontSize = 10;
        const columns = canvas.width / fontSize;
        
        // An array of drops - one per column
        const drops = [];
        for(let x = 0; x < columns; x++) {
            drops[x] = Math.random() * -100; // Start at random positions above the screen
        }
        
        // Drawing the characters
        function draw() {
            // Black BG with slight transparency for trail effect
            ctx.fillStyle = 'rgba(0, 0, 0, 0.04)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            
            ctx.fillStyle = '#0F0'; // Green text
            ctx.font = fontSize + 'px monospace';
            
            // Loop through drops
            for(let i = 0; i < drops.length; i++) {
                // Random character from the matrix array
                const text = matrixArray[Math.floor(Math.random() * matrixArray.length)];
                
                // x = i * fontSize, y = value of drops[i] * fontSize
                ctx.fillText(text, i * fontSize, drops[i] * fontSize);
                
                // Reset the drop to top randomly after it has crossed the screen
                if(drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                    drops[i] = 0;
                }
                
                // Incrementing Y coordinate
                drops[i] += Math.random() * 2 + 1; // Random speed between 1-3
            }
        }
        
        // Call the draw function every 30ms for fast animation
        setInterval(draw, 30);
        
        // Handle window resize
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
        
        // Add some random flickering effect to the Russian and Latin text
        document.addEventListener('DOMContentLoaded', function() {
            const texts = document.querySelectorAll('.russian-text, .latin-text');
            
            setInterval(function() {
                const randomIndex = Math.floor(Math.random() * texts.length);
                const randomText = texts[randomIndex];
                
                randomText.style.opacity = Math.random() * 0.5 + 0.5;
            }, 500);
        });
    </script>
</body>
</html>
