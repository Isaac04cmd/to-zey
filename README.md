<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>to zey' ❤️</title>
    
    <style>
        /* ===== RESET & BASE STYLES ===== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* Root variables untuk kemudahan kustomisasi warna */
        :root {
            --primary-pink: #f2d3d3;
            --secondary-pink: #FFC0CB;
            --accent-coral: #FFB5A7;
            --warm-peach: #ffffff;
            --soft-yellow: #FFE4B5;
            --white: #FFFFFF;
            --text-dark: #4A4A4A;
            --heart-red: #FF6B6B;
            --shadow-light: rgba(0, 0, 0, 0.1);
            --shadow-medium: rgba(0, 0, 0, 0.2);
        }

        /* Body styling dengan gradient background */
        body {
            font-family: 'Comic Sans MS', 'Segoe UI', cursive, sans-serif;
            background: linear-gradient(135deg, var(--primary-pink) 0%, var(--warm-peach) 50%, var(--soft-yellow) 100%);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        /* ===== FLOATING HEARTS ANIMATION ===== */
        .floating-hearts {
            position: fixed;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .heart {
            position: absolute;
            font-size: 20px;
            animation: float 6s infinite ease-in-out;
            opacity: 0.3;
        }

        /* Animasi floating untuk hearts */
        @keyframes float {
            0%, 100% {
                transform: translateY(0) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.3;
            }
            50% {
                transform: translateY(-100vh) rotate(360deg);
                opacity: 0.3;
            }
            90% {
                opacity: 0.3;
            }
        }

        /* ===== MAIN CONTAINER ===== */
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 2;
        }

        /* ===== WELCOME SCREEN (Screen 1) ===== */
        .screen {
            display: none;
            animation: fadeIn 0.5s ease-in;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .screen.active {
            display: flex;
        }

        /* Animasi fade in untuk transisi screen */
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Title styling */
        .title {
            font-size: 2.5rem;
            color: var(--text-dark);
            text-align: center;
            margin-bottom: 30px;
            text-shadow: 2px 2px 4px var(--shadow-light);
            animation: pulse 2s infinite;
        }

        /* Animasi pulse untuk title */
        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
        }

        /* ===== CHARACTER ILLUSTRATION ===== */
        .character-container {
            text-align: center;
            margin: 30px 0;
        }

        /* SVG Character yang lucu dan ekspresif */
        .character {
            width: 200px;
            height: 200px;
            margin: 0 auto;
            animation: bounce 2s infinite;
        }

        /* Animasi bounce untuk karakter */
        @keyframes bounce {
            0%, 100% {
                transform: translateY(0);
            }
            25% {
                transform: translateY(-10px);
            }
            75% {
                transform: translateY(5px);
            }
        }

        /* Sad face animation untuk karakter menyesal */
        .sad-face {
            animation: sadSwing 3s infinite ease-in-out;
        }

        @keyframes sadSwing {
            0%, 100% {
                transform: rotate(-5deg);
            }
            50% {
                transform: rotate(5deg);
            }
        }

        /* ===== BUTTON STYLES ===== */
        .btn {
            background: linear-gradient(135deg, var(--heart-red), var(--primary-pink));
            color: var(--white);
            border: none;
            padding: 15px 40px;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px var(--shadow-light);
            margin: 10px;
            position: relative;
            overflow: hidden;
        }

        /* Button hover effect */
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px var(--shadow-medium);
        }

        /* Button click effect */
        .btn:active {
            transform: translateY(0);
        }

        /* Ripple effect untuk button */
        .btn::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.5);
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .btn:active::after {
            width: 300px;
            height: 300px;
        }

        /* ===== MINI GAME SECTION ===== */
        .game-container {
            background: var(--white);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 10px 30px var(--shadow-light);
            margin: 20px 0;
            max-width: 600px;
            width: 100%;
        }

        /* Heart collection game */
        .heart-game {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
            margin: 20px 0;
        }

        /* Individual heart button dalam game */
        .heart-btn {
            font-size: 3rem;
            background: none;
            border: none;
            cursor: pointer;
            transition: all 0.3s ease;
            filter: grayscale(100%);
            opacity: 0.5;
        }

        /* Heart button saat di-hover */
        .heart-btn:hover {
            transform: scale(1.2);
        }

        /* Heart button saat diklik/collected */
        .heart-btn.collected {
            filter: grayscale(0%);
            opacity: 1;
            animation: heartBeat 0.5s;
        }

        /* Animasi heartbeat saat heart diklik */
        @keyframes heartBeat {
            0% {
                transform: scale(1);
            }
            25% {
                transform: scale(1.3);
            }
            50% {
                transform: scale(1);
            }
            75% {
                transform: scale(1.3);
            }
            100% {
                transform: scale(1);
            }
        }

        /* Progress counter untuk game */
        .progress {
            text-align: center;
            font-size: 1.2rem;
            color: var(--text-dark);
            margin: 15px 0;
        }

        /* ===== MESSAGE BOX ===== */
        .message-box {
            background: linear-gradient(135deg, var(--white), var(--secondary-pink));
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
            box-shadow: 0 5px 20px var(--shadow-light);
            position: relative;
            overflow: hidden;
        }

        /* Decorative ribbon untuk message box */
        .message-box::before {
            content: '❤️';
            position: absolute;
            top: -10px;
            right: 20px;
            font-size: 2rem;
            animation: pulse 2s infinite;
        }

        /* Text styling dalam message box */
        .message {
            font-size: 1.1rem;
            line-height: 1.8;
            color: var(--text-dark);
            text-align: center;
        }

        /* ===== PROMISE CARDS ===== */
        .promises-container {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            justify-content: center;
            margin: 30px 0;
        }

        /* Individual promise card */
        .promise-card {
            background: var(--white);
            border: 2px solid var(--primary-pink);
            border-radius: 15px;
            padding: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            flex: 1 1 200px;
            max-width: 250px;
            position: relative;
            overflow: hidden;
        }

        /* Promise card hover effect */
        .promise-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px var(--shadow-light);
            border-color: var(--heart-red);
        }

        /* Promise card when revealed */
        .promise-card.revealed {
            background: linear-gradient(135deg, var(--primary-pink), var(--secondary-pink));
            color: var(--white);
            transform: rotateY(360deg);
            transition: transform 0.6s ease;
        }

        /* Promise icon */
        .promise-icon {
            font-size: 2rem;
            margin-bottom: 10px;
            display: block;
            text-align: center;
        }

        /* Promise text */
        .promise-text {
            font-size: 0.9rem;
            text-align: center;
            min-height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* ===== FINAL MESSAGE SCREEN ===== */
        .final-message {
            text-align: center;
            padding: 30px;
            background: var(--white);
            border-radius: 20px;
            box-shadow: 0 10px 40px var(--shadow-medium);
            max-width: 600px;
            margin: 0 auto;
        }

        /* Big heart animation untuk final screen */
        .big-heart {
            font-size: 5rem;
            color: var(--heart-red);
            animation: heartBeat 1.5s infinite;
            margin: 20px 0;
        }

        /* ===== RESPONSIVE DESIGN ===== */
        /* Tablet view */
        @media (max-width: 768px) {
            .title {
                font-size: 2rem;
            }
            
            .character {
                width: 150px;
                height: 150px;
            }
            
            .btn {
                padding: 12px 30px;
                font-size: 1rem;
            }
            
            .game-container {
                padding: 20px;
            }
            
            .heart-btn {
                font-size: 2.5rem;
            }
            
            .promise-card {
                flex: 1 1 150px;
                max-width: 200px;
            }
        }

        /* Mobile view */
        @media (max-width: 480px) {
            .container {
                padding: 15px;
            }
            
            .title {
                font-size: 1.5rem;
            }
            
            .character {
                width: 120px;
                height: 120px;
            }
            
            .btn {
                padding: 10px 25px;
                font-size: 0.9rem;
                margin: 5px;
            }
            
            .heart-btn {
                font-size: 2rem;
            }
            
            .message {
                font-size: 1rem;
            }
            
            .promise-card {
                flex: 1 1 100%;
                max-width: 100%;
            }
            
            .big-heart {
                font-size: 3rem;
            }
        }

        /* ===== UTILITY CLASSES ===== */
        .hidden {
            display: none !important;
        }

        .fade-in {
            animation: fadeIn 0.5s ease-in;
        }

        .shake {
            animation: shake 0.5s;
        }

        /* Shake animation untuk error atau attention */
        @keyframes shake {
            0%, 100% {
                transform: translateX(0);
            }
            25% {
                transform: translateX(-10px);
            }
            75% {
                transform: translateX(10px);
            }
        }
    </style>
</head>
<body>
    <!-- Floating Hearts Background Animation -->
    <div class="floating-hearts" id="floatingHearts"></div>

    <!-- Main Container -->
    <div class="container">
        
        <!-- Screen 1: Welcome & Sad Character -->
        <div class="screen active" id="screen1">
            <h1 class="title">Uca minta maaf ya zey' 😔🫰</h1>
            
            <div class="character-container">
                <!-- SVG Character dengan ekspresi sedih -->
                <svg class="character sad-face" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
                    <!-- Face circle -->
                    <circle cx="100" cy="100" r="80" fill="#FDBCB4" stroke="#FFB5A7" stroke-width="3"/>
                    
                    <!-- Sad eyes dengan air mata -->
                    <ellipse cx="75" cy="85" rx="8" ry="12" fill="#4A4A4A"/>
                    <ellipse cx="125" cy="85" rx="8" ry="12" fill="#4A4A4A"/>
                    
                    <!-- Tears -->
                    <ellipse cx="75" cy="105" rx="5" ry="8" fill="#87CEEB" opacity="0.7">
                        <animate attributeName="cy" from="95" to="120" dur="2s" repeatCount="indefinite"/>
                        <animate attributeName="opacity" from="0.7" to="0" dur="2s" repeatCount="indefinite"/>
                    </ellipse>
                    
                    <!-- Sad mouth -->
                    <path d="M 70 130 Q 100 115 130 130" stroke="#4A4A4A" stroke-width="3" fill="none" stroke-linecap="round"/>
                    
                    <!-- Blush marks -->
                    <circle cx="50" cy="110" r="15" fill="#FFB6C1" opacity="0.5"/>
                    <circle cx="150" cy="110" r="15" fill="#FFB6C1" opacity="0.5"/>
                </svg>
            </div>
            
            <div class="message-box">
                <p class="message">
                    Uca tau uca salah dalam kejadian beberapa hari terakhir ini, maaf udah bikin zey kecewa, kecewa sama sikap spontan dan cerobohnya uca... 
                    uca menyesal dengan sangat udah nyinggung perasaan zey' 💔
                </p>
            </div>
            
            <button class="btn" onclick="goToScreen(2)">
                uca mau nebus kesalahan uca 💝
            </button>
        </div>

        <!-- Screen 2: Heart Collection Game -->
        <div class="screen" id="screen2">
            <h1 class="title">collect the scattered pieces of my heart 💕</h1>
            
            <div class="game-container">
                <p class="message">
                    Setiap love ini bentuk cinta uca ke zey'. 
                    Klik semua woopyy untuk mengumpulkan kembali perasaanku...
                </p>
                
                <div class="progress">
                    woopyy terkumpul: <span id="heartCount">0</span>/8
                </div>
                
                <div class="heart-game" id="heartGame">
                    <!-- Hearts akan di-generate via JavaScript -->
                </div>
                
                <button class="btn hidden" id="continueBtn" onclick="goToScreen(3)">
                    Lanjutkan Permintaan Maaf ucaw💗
                </button>
            </div>
        </div>

        <!-- Screen 3: Interactive Promises -->
        <div class="screen" id="screen3">
            <h1 class="title">Janji ucaw ke zey' 🤝</h1>
            
            <div class="message-box">
                <p class="message">
                    Klik setiap kartu untuk membuka janji uca ke kamu, kita, aku...
                </p>
            </div>
            
            <div class="promises-container" id="promisesContainer">
                <!-- Promise Card 1 -->
                <div class="promise-card" onclick="revealPromise(this, 0)">
                    <span class="promise-icon">🎧</span>
                    <div class="promise-text">
                        <span class="hidden-text">Uca akan lebih mendengarkan perasaan zey</span>
                        <span class="initial-text">Klik untuk membuka</span>
                    </div>
                </div>
                
                <!-- Promise Card 2 -->
                <div class="promise-card" onclick="revealPromise(this, 1)">
                    <span class="promise-icon">🤔</span>
                    <div class="promise-text">
                        <span class="hidden-text">Uca mau banyak pelan pelan sekarang, berpikir sebelum bertindak</span>
                        <span class="initial-text">Klik untuk membuka</span>
                    </div>
                </div>
                
                <!-- Promise Card 3 -->
                <div class="promise-card" onclick="revealPromise(this, 2)">
                    <span class="promise-icon">💝</span>
                    <div class="promise-text">
                        <span class="hidden-text">Uca mau berusaha lebih menghargai perasaan zey'</span>
                        <span class="initial-text">Klik untuk membuka</span>
                    </div>
                </div>
                
                <!-- Promise Card 4 -->
                <div class="promise-card" onclick="revealPromise(this, 3)">
                    <span class="promise-icon">🌟</span>
                    <div class="promise-text">
                        <span class="hidden-text">Uca mau jadi pasangan yang lebih baik</span>
                        <span class="initial-text">Klik untuk membuka</span>
                    </div>
                </div>
                
                <!-- Promise Card 5 -->
                <div class="promise-card" onclick="revealPromise(this, 4)">
                    <span class="promise-icon">🤗</span>
                    <div class="promise-text">
                        <span class="hidden-text">Uca mau terus ada buat zey'</span>
                        <span class="initial-text">Klik untuk membuka</span>
                    </div>
                </div>
                
                <!-- Promise Card 6 -->
                <div class="promise-card" onclick="revealPromise(this, 5)">
                    <span class="promise-icon">🎯</span>
                    <div class="promise-text">
                        <span class="hidden-text">Uca mau lebih fokus ke kita, kamu, aku.</span>
                        <span class="initial-text">Klik untuk membuka</span>
                    </div>
                </div>
            </div>
            
            <button class="btn hidden" id="finalBtn" onclick="goToScreen(4)">
                Lihat Pesan Terakhirku 💌
            </button>
        </div>

        <!-- Screen 4: Final Message -->
        <div class="screen" id="screen4">
            <div class="final-message">
                <h1 class="title">woopyuu zeey' ❤️</h1>
                
                <div class="big-heart">💖</div>
                
                <div class="character-container">
                    <!-- Happy character SVG -->
                    <svg class="character" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
                        <!-- Face circle -->
                        <circle cx="100" cy="100" r="80" fill="#FDBCB4" stroke="#FFB5A7" stroke-width="3"/>
                        
                        <!-- Happy eyes -->
                        <path d="M 65 85 Q 75 75 85 85" stroke="#4A4A4A" stroke-width="3" fill="none" stroke-linecap="round"/>
                        <path d="M 115 85 Q 125 75 135 85" stroke="#4A4A4A" stroke-width="3" fill="none" stroke-linecap="round"/>
                        
                        <!-- Big smile -->
                        <path d="M 60 120 Q 100 140 140 120" stroke="#4A4A4A" stroke-width="3" fill="#FF6B6B" stroke-linecap="round"/>
                        
                        <!-- Hearts around face -->
                        <text x="30" y="70" font-size="20" fill="#FF6B6B">❤️</text>
                        <text x="150" y="70" font-size="20" fill="#FF6B6B">❤️</text>
                        <text x="30" y="150" font-size="20" fill="#FF6B6B">💕</text>
                        <text x="150" y="150" font-size="20" fill="#FF6B6B">💕</text>
                        
                        <!-- Blush -->
                        <circle cx="50" cy="110" r="15" fill="#FFB6C1" opacity="0.6"/>
                        <circle cx="150" cy="110" r="15" fill="#FFB6C1" opacity="0.6"/>
                    </svg>
                </div>
                
                <p class="message">
                    Terimakacii banyak sudah ngasih kesempatan buat uca minta maaf. 
                    Uca janji mau terus belajar buat kita, kamu, aku. 
                    <p>
                    everything you're 🫶
                    </p>
                    <br><br>
                    <strong>Semoga kamu mau maafin aku yaa..💑</strong>
                </p>
                
                <button class="btn" onclick="restart()">
                    Ulangi dari Awal 🔄
                </button>
                
                <!-- Audio element untuk sound effects (optional) -->
                <audio id="heartSound" preload="auto">
                    <!-- Anda bisa menambahkan file audio jika diperlukan -->
                </audio>
            </div>
        </div>
    </div>

    <script>
        // ===== INITIALIZATION =====
        
        // Initialize floating hearts di background
        function createFloatingHearts() {
            const container = document.getElementById('floatingHearts');
            const hearts = ['❤️', '💕', '💖', '💗', '💝'];
            
            // Create 15 floating hearts
            for (let i = 0; i < 15; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
                heart.style.left = Math.random() * 100 + '%';
                heart.style.animationDelay = Math.random() * 6 + 's';
                heart.style.fontSize = (Math.random() * 20 + 15) + 'px';
                container.appendChild(heart);
            }
        }
        
        // ===== SCREEN NAVIGATION =====
        
        /**
         * Navigate to specific screen
         * @param {number} screenNumber - Screen number to navigate to
         */
        function goToScreen(screenNumber) {
            // Hide all screens
            document.querySelectorAll('.screen').forEach(screen => {
                screen.classList.remove('active');
            });
            
            // Show target screen
            const targetScreen = document.getElementById('screen' + screenNumber);
            if (targetScreen) {
                targetScreen.classList.add('active');
                
                // Initialize screen-specific features
                if (screenNumber === 2) {
                    initHeartGame();
                } else if (screenNumber === 3) {
                    resetPromises();
                }
            }
            
            // Smooth scroll to top
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }
        
        // ===== HEART COLLECTION GAME =====
        
        let collectedHearts = 0;
        const totalHearts = 8;
        
        /**
         * Initialize heart collection game
         */
        function initHeartGame() {
            const gameContainer = document.getElementById('heartGame');
            gameContainer.innerHTML = '';
            collectedHearts = 0;
            updateHeartCounter();
            
            // Create heart buttons
            const heartEmojis = ['❤️', '💕', '💖', '💗', '💝', '💓', '💞', '💘'];
            
            heartEmojis.forEach((emoji, index) => {
                const heartBtn = document.createElement('button');
                heartBtn.className = 'heart-btn';
                heartBtn.textContent = emoji;
                heartBtn.onclick = () => collectHeart(heartBtn);
                
                // Random delay untuk animasi
                setTimeout(() => {
                    gameContainer.appendChild(heartBtn);
                }, index * 100);
            });
            
            // Hide continue button initially
            document.getElementById('continueBtn').classList.add('hidden');
        }
        
        /**
         * Handle heart collection
         * @param {HTMLElement} heartElement - The heart button element
         */
        function collectHeart(heartElement) {
            if (!heartElement.classList.contains('collected')) {
                heartElement.classList.add('collected');
                collectedHearts++;
                updateHeartCounter();
                
                // Play collection sound effect (if audio available)
                playHeartSound();
                
                // Check if all hearts collected
                if (collectedHearts === totalHearts) {
                    setTimeout(() => {
                        document.getElementById('continueBtn').classList.remove('hidden');
                        showCompletionMessage();
                    }, 500);
                }
            }
        }
        
        /**
         * Update heart counter display
         */
        function updateHeartCounter() {
            document.getElementById('heartCount').textContent = collectedHearts;
        }
        
        /**
         * Show completion message for heart game
         */
        function showCompletionMessage() {
            const gameContainer = document.querySelector('#screen2 .game-container');
            const message = document.createElement('div');
            message.className = 'message-box fade-in';
            message.innerHTML = '<p class="message">Luar biasa! Kamu telah mengumpulkan semua hatiku! 💖</p>';
            gameContainer.insertBefore(message, document.getElementById('continueBtn'));
        }
        
        // ===== PROMISE CARDS INTERACTION =====
        
        let revealedPromises = 0;
        const totalPromises = 6;
        
        /**
         * Reveal promise card with animation
         * @param {HTMLElement} card - The promise card element
         * @param {number} index - Index of the promise
         */
        function revealPromise(card, index) {
            if (!card.classList.contains('revealed')) {
                card.classList.add('revealed');
                
                // Change text content
                const textContainer = card.querySelector('.promise-text');
                const hiddenText = card.querySelector('.hidden-text').textContent;
                textContainer.innerHTML = hiddenText;
                
                // Increment counter
                revealedPromises++;
                
                // Check if all promises revealed
                if (revealedPromises === totalPromises) {
                    setTimeout(() => {
                        document.getElementById('finalBtn').classList.remove('hidden');
                    }, 800);
                }
                
                // Add celebration effect
                createSparkles(card);
            }
        }
        
        /**
         * Reset all promise cards
         */
        function resetPromises() {
            revealedPromises = 0;
            document.querySelectorAll('.promise-card').forEach(card => {
                card.classList.remove('revealed');
                const textContainer = card.querySelector('.promise-text');
                const initialText = card.querySelector('.initial-text');
                if (initialText) {
                    textContainer.innerHTML = '<span class="initial-text">Klik untuk membuka</span>';
                }
            });
            document.getElementById('finalBtn').classList.add('hidden');
        }
        
        // ===== VISUAL EFFECTS =====
        
        /**
         * Create sparkle effect on element
         * @param {HTMLElement} element - Target element for sparkles
         */
        function createSparkles(element) {
            const rect = element.getBoundingClientRect();
            const sparkles = ['✨', '⭐', '💫'];
            
            for (let i = 0; i < 5; i++) {
                const sparkle = document.createElement('div');
                sparkle.textContent = sparkles[Math.floor(Math.random() * sparkles.length)];
                sparkle.style.position = 'fixed';
                sparkle.style.left = rect.left + Math.random() * rect.width + 'px';
                sparkle.style.top = rect.top + Math.random() * rect.height + 'px';
                sparkle.style.fontSize = '20px';
                sparkle.style.pointerEvents = 'none';
                sparkle.style.animation = 'float 2s ease-out forwards';
                sparkle.style.zIndex = '1000';
                
                document.body.appendChild(sparkle);
                
                // Remove sparkle after animation
                setTimeout(() => {
                    sparkle.remove();
                }, 2000);
            }
        }
        
        /**
         * Play heart collection sound effect
         */
        function playHeartSound() {
            // Create a simple beep sound using Web Audio API
            try {
                const audioContext = new (window.AudioContext || window.webkitAudioContext)();
                const oscillator = audioContext.createOscillator();
                const gainNode = audioContext.createGain();
                
                oscillator.connect(gainNode);
                gainNode.connect(audioContext.destination);
                
                oscillator.frequency.value = 800; // Frequency in Hz
                oscillator.type = 'sine';
                
                gainNode.gain.setValueAtTime(0.3, audioContext.currentTime);
                gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.1);
                
                oscillator.start(audioContext.currentTime);
                oscillator.stop(audioContext.currentTime + 0.1);
            } catch (e) {
                // Fallback jika Web Audio API tidak tersedia
                console.log('Audio not available');
            }
        }
        
        // ===== RESTART FUNCTION =====
        
        /**
         * Restart the entire experience
         */
        function restart() {
            // Reset all variables
            collectedHearts = 0;
            revealedPromises = 0;
            
            // Go back to first screen
            goToScreen(1);
            
            // Reset game states
            const heartGame = document.getElementById('heartGame');
            if (heartGame) {
                heartGame.innerHTML = '';
            }
            
            // Hide buttons
            document.getElementById('continueBtn').classList.add('hidden');
            document.getElementById('finalBtn').classList.add('hidden');
            
            // Remove any temporary messages
            document.querySelectorAll('.fade-in').forEach(el => {
                if (el.classList.contains('message-box') && !el.hasAttribute('data-permanent')) {
                    el.remove();
                }
            });
        }
        
        // ===== INITIALIZATION ON PAGE LOAD =====
        
        /**
         * Initialize all components when page loads
         */
        window.addEventListener('DOMContentLoaded', function() {
            // Create floating hearts background
            createFloatingHearts();
            
            // Add touch support for mobile devices
            addTouchSupport();
            
            // Initialize first screen
            goToScreen(1);
            
            // Add keyboard navigation support
            addKeyboardNavigation();
            
            // Preload animations
            preloadAnimations();
        });
        
        // ===== MOBILE & ACCESSIBILITY FEATURES =====
        
        /**
         * Add touch support for better mobile experience
         */
        function addTouchSupport() {
            // Prevent double-tap zoom on buttons
            document.querySelectorAll('.btn, .heart-btn, .promise-card').forEach(element => {
                element.addEventListener('touchend', function(e) {
                    e.preventDefault();
                    this.click();
                });
            });
            
            // Add touch feedback
            document.addEventListener('touchstart', function(e) {
                if (e.target.classList.contains('btn') || 
                    e.target.classList.contains('heart-btn') || 
                    e.target.classList.contains('promise-card')) {
                    e.target.style.transform = 'scale(0.95)';
                }
            });
            
            document.addEventListener('touchend', function(e) {
                if (e.target.classList.contains('btn') || 
                    e.target.classList.contains('heart-btn') || 
                    e.target.classList.contains('promise-card')) {
                    setTimeout(() => {
                        e.target.style.transform = '';
                    }, 100);
                }
            });
        }
        
        /**
         * Add keyboard navigation support
         */
        function addKeyboardNavigation() {
            document.addEventListener('keydown', function(e) {
                // Arrow keys for navigation
                if (e.key === 'ArrowRight' || e.key === ' ') {
                    const activeScreen = document.querySelector('.screen.active');
                    const nextBtn = activeScreen.querySelector('.btn:not(.hidden)');
                    if (nextBtn) {
                        nextBtn.click();
                    }
                } else if (e.key === 'ArrowLeft') {
                    // Optional: Add back navigation if needed
                }
                
                // Enter key for interaction
                if (e.key === 'Enter') {
                    if (document.activeElement.classList.contains('heart-btn') ||
                        document.activeElement.classList.contains('promise-card')) {
                        document.activeElement.click();
                    }
                }
            });
        }
        
        /**
         * Preload animations for smooth transitions
         */
        function preloadAnimations() {
            // Force browser to pre-render animations
            const temp = document.createElement('div');
            temp.style.position = 'absolute';
            temp.style.left = '-9999px';
            temp.className = 'preload-animation';
            
            // Add animation classes
            ['fade-in', 'bounce', 'pulse', 'heartBeat'].forEach(animClass => {
                const el = document.createElement('div');
                el.className = animClass;
                temp.appendChild(el);
            });
            
            document.body.appendChild(temp);
            
            // Remove after animations are loaded
            setTimeout(() => {
                temp.remove();
            }, 100);
        }
        
        // ===== PERFORMANCE OPTIMIZATION =====
        
        /**
         * Throttle function for performance
         * @param {Function} func - Function to throttle
         * @param {number} limit - Time limit in ms
         */
        function throttle(func, limit) {
            let inThrottle;
            return function() {
                const args = arguments;
                const context = this;
                if (!inThrottle) {
                    func.apply(context, args);
                    inThrottle = true;
                    setTimeout(() => inThrottle = false, limit);
                }
            }
        }
        
        // ===== OPTIONAL: BACKGROUND MUSIC =====
        
        /**
         * Toggle background music (if you want to add it)
         * Note: Requires user interaction to start due to browser policies
         */
        function toggleBackgroundMusic() {
            // This is a placeholder for background music functionality
            // You would need to add an audio file and control it here
            console.log('Music feature can be added here');
        }
        
        // ===== EASTER EGG =====
        
        // Konami code easter egg for fun surprise
        const konamiCode = ['ArrowUp', 'ArrowUp', 'ArrowDown', 'ArrowDown', 
                           'ArrowLeft', 'ArrowRight', 'ArrowLeft', 'ArrowRight', 'b', 'a'];
        let konamiIndex = 0;
        
        document.addEventListener('keydown', function(e) {
            if (e.key === konamiCode[konamiIndex]) {
                konamiIndex++;
                if (konamiIndex === konamiCode.length) {
                    activateEasterEgg();
                    konamiIndex = 0;
                }
            } else {
                konamiIndex = 0;
            }
        });
        
        /**
         * Activate special easter egg surprise
         */
        function activateEasterEgg() {
            // Create rainbow effect
            document.body.style.animation = 'rainbow 3s linear infinite';
            
            // Add special message
            const message = document.createElement('div');
            message.style.position = 'fixed';
            message.style.top = '50%';
            message.style.left = '50%';
            message.style.transform = 'translate(-50%, -50%)';
            message.style.fontSize = '3rem';
            message.style.zIndex = '9999';
            message.style.animation = 'heartBeat 1s infinite';
            message.textContent = '🌈 LOVE UNLOCKED! 🌈';
            document.body.appendChild(message);
            
            setTimeout(() => {
                message.remove();
                document.body.style.animation = '';
            }, 3000);
        }
        
        // Rainbow animation for easter egg
        const style = document.createElement('style');
        style.textContent = `
            @keyframes rainbow {
                0% { filter: hue-rotate(0deg); }
                100% { filter: hue-rotate(360deg); }
            }
        `;
        document.head.appendChild(style);
        
        // ===== ERROR HANDLING =====
        
        /**
         * Global error handler
         */
        window.addEventListener('error', function(e) {
            console.error('An error occurred:', e.error);
            // Prevent the experience from breaking
            return true;
        });
        
        // ===== ANALYTICS (Optional) =====
        
        /**
         * Track user interactions (for improvement purposes)
         * @param {string} action - Action performed
         * @param {string} label - Additional label
         */
        function trackEvent(action, label) {
            // This is where you could add analytics tracking
            console.log(`Event: ${action} - ${label}`);
        }
        
        // Track screen views
        const originalGoToScreen = goToScreen;
        goToScreen = function(screenNumber) {
            originalGoToScreen(screenNumber);
            trackEvent('screen_view', 'screen_' + screenNumber);
        };
        
        // ===== RESPONSIVE VIEWPORT FIX =====
        
        /**
         * Fix viewport height on mobile browsers
         */
        function setViewportHeight() {
            const vh = window.innerHeight * 0.01;
            document.documentElement.style.setProperty('--vh', `${vh}px`);
        }
        
        setViewportHeight();
        window.addEventListener('resize', throttle(setViewportHeight, 100));
        
        // ===== PREVENT TEXT SELECTION ON DOUBLE TAP =====
        
        document.addEventListener('selectstart', function(e) {
            if (e.target.tagName !== 'INPUT' && e.target.tagName !== 'TEXTAREA') {
                e.preventDefault();
            }
        });
        
        // ===== AUTO-SAVE PROGRESS (Optional) =====
        
        /**
         * Save progress to localStorage
         */
        function saveProgress() {
            const progress = {
                currentScreen: document.querySelector('.screen.active').id,
                collectedHearts: collectedHearts,
                revealedPromises: revealedPromises
            };
            // Note: localStorage not available in Claude artifacts
            // This is for when you use the code in your own environment
            try {
                localStorage.setItem('apologyProgress', JSON.stringify(progress));
            } catch(e) {
                console.log('Progress saving not available in this environment');
            }
        }
        
        /**
         * Load saved progress
         */
        function loadProgress() {
            try {
                const saved = localStorage.getItem('apologyProgress');
                if (saved) {
                    const progress = JSON.parse(saved);
                    // Restore progress here if needed
                    console.log('Progress loaded:', progress);
                }
            } catch(e) {
                console.log('Progress loading not available in this environment');
            }
        }
        
        // ===== FINAL INITIALIZATION =====
        
        console.log('💕 Website Maaf Interaktif telah siap! 💕');
        console.log('Dibuat dengan penuh cinta dan penyesalan...');
        console.log('Tip: Coba tekan Konami Code untuk surprise! ⬆⬆⬇⬇⬅➡⬅➡BA');
    </script>
</body>
</html>
