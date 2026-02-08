<!doctype html>
<html lang="en" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Be My Valentine? 💕</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&amp;family=Quicksand:wght@400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
    }
    
    .font-pacifico {
      font-family: 'Pacifico', cursive;
    }
    
    .font-quicksand {
      font-family: 'Quicksand', sans-serif;
    }
    
    @keyframes float {
      0%, 100% { transform: translateY(0px) rotate(0deg); }
      50% { transform: translateY(-20px) rotate(5deg); }
    }
    
    @keyframes pulse-heart {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.1); }
    }
    
    @keyframes confetti-fall {
      0% { transform: translateY(-100%) rotate(0deg); opacity: 1; }
      100% { transform: translateY(100%) rotate(720deg); opacity: 0; }
    }
    
    @keyframes bounce-in {
      0% { transform: scale(0); opacity: 0; }
      50% { transform: scale(1.2); }
      100% { transform: scale(1); opacity: 1; }
    }
    
    @keyframes wiggle {
      0%, 100% { transform: rotate(-3deg); }
      50% { transform: rotate(3deg); }
    }
    
    .float-animation {
      animation: float 3s ease-in-out infinite;
    }
    
    .pulse-heart {
      animation: pulse-heart 1s ease-in-out infinite;
    }
    
    .bounce-in {
      animation: bounce-in 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55) forwards;
    }
    
    .wiggle {
      animation: wiggle 0.5s ease-in-out infinite;
    }
    
    .confetti {
      position: fixed;
      width: 10px;
      height: 10px;
      top: -10px;
      animation: confetti-fall 3s linear forwards;
    }
    
    .heart-bg {
      position: absolute;
      opacity: 0.1;
      font-size: 40px;
      pointer-events: none;
    }
    
    .no-btn {
      transition: all 0.1s ease;
    }
    
    .celebration-card {
      transition: all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    }
    
    .celebration-card:hover {
      transform: translateY(-8px) scale(1.05);
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full font-quicksand">
  <div id="app" class="h-full w-full overflow-auto relative" style="background: linear-gradient(135deg, #fce4ec 0%, #f8bbd9 50%, #f48fb1 100%);"><!-- Floating Hearts Background -->
   <div id="hearts-bg" class="absolute inset-0 overflow-hidden pointer-events-none"></div><!-- Main Content -->
   <div class="relative z-10 min-h-full flex flex-col items-center justify-center p-6"><!-- Proposal Screen -->
    <div id="proposal-screen" class="text-center max-w-lg mx-auto"><!-- Big Heart -->
     <div class="text-8xl mb-6 pulse-heart">
      💕
     </div><!-- Couple Photo -->
     <div class="mb-8 float-animation">
      <div class="inline-block bg-white p-3 rounded-2xl shadow-2xl transform rotate-2 hover:rotate-0 transition-transform duration-300"><img src="mj.png" alt="Our photo together" loading="lazy" class="w-48 h-48 md:w-56 md:h-56 object-cover rounded-xl" onerror="console.error('Image failed to load:', this.src); this.style.background='linear-gradient(135deg, #fda4af 0%, #fb7185 100%)'; this.alt='Replace with your photo';">
       <div class="absolute -top-3 -right-3 text-4xl animate-pulse">
        💖
       </div>
       <div class="absolute -bottom-3 -left-3 text-4xl animate-pulse" style="animation-delay: 0.5s;">
        💕
       </div>
      </div>
     </div><!-- Question -->
     <h1 id="proposal-question" class="font-pacifico text-4xl md:text-5xl text-pink-800 mb-8 leading-relaxed">Shubham, will you be my Valentine?</h1><!-- Cute Bear/Character -->
     <div class="text-6xl mb-6 float-animation">
      🧸💝
     </div><!-- Buttons -->
     <div class="flex flex-col sm:flex-row gap-4 items-center justify-center relative min-h-[120px]"><button id="yes-btn" class="px-10 py-4 bg-gradient-to-r from-pink-500 to-rose-500 text-white text-xl font-bold rounded-full shadow-lg hover:shadow-xl hover:scale-110 transition-all duration-300 wiggle"> Yes! 💖 </button> <button id="no-btn" class="no-btn px-10 py-4 bg-gray-300 text-gray-600 text-xl font-bold rounded-full shadow-md absolute sm:relative"> No 😢 </button>
     </div>
     <p class="text-pink-600 mt-6 text-sm italic opacity-70">Hint: Try clicking No... if you can! 😏</p>
    </div><!-- Success Screen (Hidden Initially) -->
    <div id="success-screen" class="text-center max-w-2xl mx-auto hidden"><!-- Celebration Emoji -->
     <div class="text-7xl mb-4 bounce-in">
      🎉💕🎉
     </div><!-- Success Message -->
     <h1 id="success-title" class="font-pacifico text-4xl md:text-5xl text-pink-800 mb-4 bounce-in" style="animation-delay: 0.2s;">Yay! 🥳</h1>
     <p id="success-subtitle" class="text-xl md:text-2xl text-pink-700 mb-8 bounce-in" style="animation-delay: 0.4s;">I knew you would choose Yes! 💖</p><!-- Celebration Options -->
     <div class="bounce-in" style="animation-delay: 0.6s;">
      <h2 class="font-pacifico text-2xl md:text-3xl text-pink-800 mb-6">How do you want to celebrate Valentine's? 🌹</h2>
      <div class="grid grid-cols-2 gap-4 max-w-md mx-auto">
       <div class="celebration-card bg-white/80 backdrop-blur-sm rounded-2xl p-6 shadow-lg cursor-pointer border-2 border-transparent hover:border-pink-400" data-choice="home">
        <div class="text-5xl mb-3">
         🏠
        </div>
        <h3 class="font-bold text-pink-800 text-lg">At Home</h3>
        <p class="text-pink-600 text-sm mt-1">Cozy &amp; romantic</p>
       </div>
       <div class="celebration-card bg-white/80 backdrop-blur-sm rounded-2xl p-6 shadow-lg cursor-pointer border-2 border-transparent hover:border-pink-400" data-choice="restaurant">
        <div class="text-5xl mb-3">
         🍽️
        </div>
        <h3 class="font-bold text-pink-800 text-lg">At Restaurant</h3>
        <p class="text-pink-600 text-sm mt-1">Fine dining</p>
       </div>
       <div class="celebration-card bg-white/80 backdrop-blur-sm rounded-2xl p-6 shadow-lg cursor-pointer border-2 border-transparent hover:border-pink-400" data-choice="cafe">
        <div class="text-5xl mb-3">
         ☕
        </div>
        <h3 class="font-bold text-pink-800 text-lg">At Cafe</h3>
        <p class="text-pink-600 text-sm mt-1">Sweet &amp; casual</p>
       </div>
       <div class="celebration-card bg-white/80 backdrop-blur-sm rounded-2xl p-6 shadow-lg cursor-pointer border-2 border-transparent hover:border-pink-400" data-choice="picnic">
        <div class="text-5xl mb-3">
         🧺
        </div>
        <h3 class="font-bold text-pink-800 text-lg">Picnic</h3>
        <p class="text-pink-600 text-sm mt-1">Nature &amp; fun</p>
       </div>
      </div>
     </div>
    </div><!-- Final Choice Screen (Hidden Initially) -->
    <div id="final-screen" class="text-center max-w-lg mx-auto hidden">
     <div class="text-7xl mb-6 bounce-in">
      💑
     </div>
     <h1 class="font-pacifico text-4xl md:text-5xl text-pink-800 mb-4 bounce-in" style="animation-delay: 0.2s;">Perfect Choice!</h1>
     <p id="final-choice-text" class="text-xl md:text-2xl text-pink-700 mb-6 bounce-in" style="animation-delay: 0.4s;"></p>
     <div class="text-6xl bounce-in" style="animation-delay: 0.6s;">
      ❤️🌹❤️
     </div>
     <p class="text-pink-600 mt-8 text-lg bounce-in" style="animation-delay: 0.8s;">Can't wait to spend Valentine's with you! 💕</p>
    </div>
   </div><!-- Confetti Container -->
   <div id="confetti-container" class="fixed inset-0 pointer-events-none z-50"></div>
  </div>
  <script>
    const defaultConfig = {
      proposal_name: 'Shubham',
      success_message: 'I knew you would choose Yes! 💖',
      primary_color: '#ec4899',
      secondary_color: '#ffffff',
      text_color: '#831843',
      accent_color: '#f472b6',
      bg_color: '#fce4ec'
    };

    let config = { ...defaultConfig };

    // Initialize floating hearts background
    function createFloatingHearts() {
      const container = document.getElementById('hearts-bg');
      const hearts = ['💕', '💖', '💗', '💓', '💝', '❤️', '🌹'];
      
      for (let i = 0; i < 15; i++) {
        const heart = document.createElement('div');
        heart.className = 'heart-bg float-animation';
        heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
        heart.style.left = Math.random() * 100 + '%';
        heart.style.top = Math.random() * 100 + '%';
        heart.style.animationDelay = Math.random() * 3 + 's';
        heart.style.fontSize = (20 + Math.random() * 40) + 'px';
        container.appendChild(heart);
      }
    }

    // No button escape logic
    function setupNoButton() {
      const noBtn = document.getElementById('no-btn');
      const container = document.getElementById('proposal-screen');
      
      function moveButton(e) {
        const containerRect = container.getBoundingClientRect();
        const btnRect = noBtn.getBoundingClientRect();
        
        // Calculate random position within container bounds
        const maxX = containerRect.width - btnRect.width - 20;
        const maxY = 200;
        
        let newX = Math.random() * maxX - maxX/2;
        let newY = Math.random() * maxY - maxY/2;
        
        // Make sure button moves away from cursor
        const cursorX = e.clientX - containerRect.left - containerRect.width/2;
        const cursorY = e.clientY - containerRect.top;
        
        if (Math.abs(newX - cursorX) < 100) {
          newX = cursorX > 0 ? -Math.abs(newX) - 50 : Math.abs(newX) + 50;
        }
        
        noBtn.style.transform = `translate(${newX}px, ${newY}px)`;
      }
      
      noBtn.addEventListener('mouseenter', moveButton);
      noBtn.addEventListener('mousemove', moveButton);
      noBtn.addEventListener('touchstart', (e) => {
        e.preventDefault();
        moveButton(e.touches[0]);
      });
    }

    // Confetti explosion
    function createConfetti() {
      const container = document.getElementById('confetti-container');
      const colors = ['#ec4899', '#f472b6', '#fb7185', '#fda4af', '#fecdd3', '#ff6b6b', '#ffd93d'];
      
      for (let i = 0; i < 100; i++) {
        setTimeout(() => {
          const confetti = document.createElement('div');
          confetti.className = 'confetti';
          confetti.style.left = Math.random() * 100 + '%';
          confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
          confetti.style.borderRadius = Math.random() > 0.5 ? '50%' : '0';
          confetti.style.width = (5 + Math.random() * 10) + 'px';
          confetti.style.height = (5 + Math.random() * 10) + 'px';
          confetti.style.animationDuration = (2 + Math.random() * 2) + 's';
          container.appendChild(confetti);
          
          setTimeout(() => confetti.remove(), 4000);
        }, i * 30);
      }
    }

    // Yes button click handler
    function setupYesButton() {
      const yesBtn = document.getElementById('yes-btn');
      
      yesBtn.addEventListener('click', () => {
        createConfetti();
        
        setTimeout(() => {
          document.getElementById('proposal-screen').classList.add('hidden');
          document.getElementById('success-screen').classList.remove('hidden');
        }, 500);
      });
    }

    // Celebration choice handlers
    function setupCelebrationChoices() {
      const cards = document.querySelectorAll('.celebration-card');
      const choiceMessages = {
        home: "A cozy night at home it is! 🏠💕 Netflix, snuggles, and lots of love!",
        restaurant: "Fancy dinner date! 🍽️✨ Let's dress up and enjoy a romantic evening!",
        cafe: "Coffee date vibes! ☕💖 Sweet treats and sweeter moments together!",
        picnic: "Adventure awaits! 🧺🌸 Fresh air, good food, and the best company!"
      };
      
      cards.forEach(card => {
        card.addEventListener('click', () => {
          const choice = card.dataset.choice;
          document.getElementById('final-choice-text').textContent = choiceMessages[choice];
          
          createConfetti();
          
          setTimeout(() => {
            document.getElementById('success-screen').classList.add('hidden');
            document.getElementById('final-screen').classList.remove('hidden');
          }, 300);
        });
      });
    }

    // Update UI based on config
    async function onConfigChange(cfg) {
      config = { ...defaultConfig, ...cfg };
      
      const name = config.proposal_name || defaultConfig.proposal_name;
      const successMsg = config.success_message || defaultConfig.success_message;
      
      document.getElementById('proposal-question').textContent = `${name}, will you be my Valentine?`;
      document.getElementById('success-subtitle').textContent = successMsg;
    }

    // Element SDK setup
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities: (cfg) => ({
          recolorables: [
            {
              get: () => cfg.primary_color || defaultConfig.primary_color,
              set: (value) => { cfg.primary_color = value; window.elementSdk.setConfig({ primary_color: value }); }
            },
            {
              get: () => cfg.secondary_color || defaultConfig.secondary_color,
              set: (value) => { cfg.secondary_color = value; window.elementSdk.setConfig({ secondary_color: value }); }
            },
            {
              get: () => cfg.text_color || defaultConfig.text_color,
              set: (value) => { cfg.text_color = value; window.elementSdk.setConfig({ text_color: value }); }
            }
          ],
          borderables: [],
          fontEditable: undefined,
          fontSizeable: undefined
        }),
        mapToEditPanelValues: (cfg) => new Map([
          ['proposal_name', cfg.proposal_name || defaultConfig.proposal_name],
          ['success_message', cfg.success_message || defaultConfig.success_message]
        ])
      });
    }

    // Initialize everything
    createFloatingHearts();
    setupNoButton();
    setupYesButton();
    setupCelebrationChoices();
    onConfigChange(config);
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c7f37a854663c5e',t:'MTc3MDA5MzI4Mi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
