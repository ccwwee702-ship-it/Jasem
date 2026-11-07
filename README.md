
<!-- saved from url=(0042)https://ccwwee702-ship-it.github.io/Jasem/ -->
<html lang="ar"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8"></head><body># Jasem

<!-- saved from url=(0079)file:///C:/Users/ccwwe/Downloads/Mock%20%E2%80%94%20alza7f_%20UI%20Replica.html -->

  
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Mock — alza7f_ UI Replica</title>
  <style>
    /* ============================================
       1. RESET & BASE STYLES
       ============================================ */
    * { 
      box-sizing: border-box; 
      margin: 0; 
      padding: 0; 
    }
    
    html, body { 
      height: 100%; 
    }
    
    body {
      font-family: "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
      background: #000;
      color: #ddd;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      direction: rtl;
      overflow-y: auto;
      scrollbar-width: none;
    }
    
    body::-webkit-scrollbar { 
      display: none; 
    }

    /* ============================================
       2. LOADING SCREEN
       ============================================ */
    #loading-screen {
      position: fixed;
      inset: 0;
      z-index: 9999;
      background: #000;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      transition: opacity 0.8s ease-out;
    }
    
    #loading-screen.hidden {
      opacity: 0;
      pointer-events: none;
    }

    .loader-container {
      text-align: center;
    }

    .loader-logo {
      font-size: 48px;
      font-weight: 900;
      letter-spacing: 8px;
      color: #e6e6e6;
      margin-bottom: 40px;
      animation: pulse 2s ease-in-out infinite;
    }

    .loader-logo .accent {
      background: linear-gradient(90deg, #fff, #505150);
      -webkit-background-clip: text;
      background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .progress-container {
      width: 400px;
      max-width: 90vw;
      margin: 0 auto;
    }

    .progress-bar {
      width: 100%;
      height: 8px;
      background: rgba(255,255,255,0.05);
      border-radius: 10px;
      overflow: hidden;
      position: relative;
      border: 1px solid rgba(255,255,255,0.1);
      box-shadow: 0 4px 20px rgba(0,0,0,0.5);
    }

    .progress-fill {
      height: 100%;
      background: linear-gradient(90deg, #ffffff, #ffffff, #ffffff);
      background-size: 200% 100%;
      border-radius: 10px;
      width: 0%;
      transition: width 0.1s ease-out;
      animation: shimmer 2s linear infinite;
      box-shadow: 0 0 20px rgba(89, 90, 89, 0.5);
    }

    .progress-text {
      margin-top: 20px;
      font-size: 36px;
      font-weight: 700;
      color: #ffffff;
      font-family: "Courier New", monospace;
      text-shadow: 0 0 20px rgba(89, 90, 89, 0.5);
    }

    .loading-status {
      margin-top: 15px;
      font-size: 14px;
      color: rgba(255,255,255,0.5);
      letter-spacing: 2px;
      font-family: "Courier New", monospace;
    }

    /* ============================================
       3. ANIMATIONS
       ============================================ */
    @keyframes pulse {
      0%, 100% { 
        opacity: 1; 
        transform: scale(1); 
      }
      50% { 
        opacity: 0.8; 
        transform: scale(1.02); 
      }
    }

    @keyframes shimmer {
      0% { background-position: 200% 0; }
      100% { background-position: -200% 0; }
    }

    @keyframes lift { 
      to { 
        transform: none; 
        opacity: 1; 
      } 
    }

    /* ============================================
       4. GRID BACKGROUND
       ============================================ */
    .grid-bg {
      position: fixed;
      inset: 0;
      z-index: 0;
      background:
        linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
      background-size: 60px 60px, 60px 60px;
      pointer-events: none;
      filter: contrast(0.9) brightness(0.8);
    }
    
    .grid-bg::after {
      content: "";
      position: absolute;
      inset: 0;
      background: rgba(0,0,0,0.75);
    }

    /* ============================================
       5. TOP HEADER
       ============================================ */
    .topbar {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      height: 64px;
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 50;
      backdrop-filter: blur(6px);
      background: linear-gradient(180deg, rgba(0,0,0,0.45), rgba(0,0,0,0.25));
      border-bottom: 1px solid rgba(255,255,255,0.03);
      padding: 0 20px;
    }
    
    .topbar .brand {
      font-weight: 800;
      letter-spacing: 6px;
      font-size: 20px;
      color: #e6e6e6;
      display: flex;
      gap: 12px;
      align-items: center;
    }
    
    .topbar .brand .accent {
      color: #cfcfcf;
      background: linear-gradient(90deg, rgba(255,255,255,0.95), rgba(200,200,200,0.7));
      -webkit-background-clip: text;
      background-clip: text;
      -webkit-text-fill-color: transparent;
      font-weight: 900;
    }
    
    .topbar .note {
      position: absolute;
      right: 18px;
      font-size: 12px;
      color: rgba(200,200,200,0.45);
    }

    /* ============================================
       6. SIDE PANELS
       ============================================ */
    .side-panel {
      position: fixed;
      top: 86px;
      width: 220px;
      padding: 16px 12px;
      border-radius: 10px;
      background: linear-gradient(180deg, rgba(0, 0, 0, 0.65), rgba(0,0,0,0.55));
      border: 1px solid rgba(255,255,255,0.04);
      box-shadow: 0 8px 30px rgba(0,0,0,0.77), inset 0 1px 0 rgba(255, 255, 255, 0.06);
      color: #cfe9cf;
      font-size: 13px;
      z-index: 40;
    }
    
    .side-left { 
      left: 18px; 
    }
    
    .side-right { 
      right: 18px; 
    }

    .side-panel h4 {
      font-size: 12px;
      color: #b8d6b8;
      letter-spacing: 1px;
      margin-bottom: 10px;
    }
    
    .side-panel .btn {
      display: block;
      width: 100%;
      padding: 8px 10px;
      margin: 7px 0;
      border-radius: 6px;
      background: rgba(0,0,0,0.35);
      color: #dfffd7;
      text-decoration: none;
      font-size: 13px;
      border: 1px solid rgba(0,200,0,0.06);
      cursor: pointer;
      transition: transform 0.2s ease;
    }
    
    .side-panel .btn:hover { 
      transform: translateY(-2px); 
    }

    .side-panel .discord-link {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      margin-top: 16px;
      padding: 10px;
      background: rgba(0,0,0,0.5);
      border-radius: 6px;
      color: #ffffff;
      font-size: 13px;
      font-weight: 600;
      text-decoration: none;
      cursor: pointer;
      transition: transform 0.2s ease;
    }
    
    .side-panel .discord-link:hover {
      transform: translateY(-2px);
    }
    
    .side-panel .discord-icon {
      width: 20px;
      height: 20px;
      fill: currentColor;
    }

    /* ============================================
       7. MAIN CONTENT
       ============================================ */
    main.wrap {
      position: relative;
      z-index: 2;
      max-width: 1200px;
      margin: 120px auto 80px;
      padding: 24px;
      display: flex;
      gap: 28px;
      align-items: flex-start;
      flex-direction: column;
      min-height: 60vh;
    }

    /* ============================================
       8. PORTRAIT IMAGE
       ============================================ */
    .portrait-wrap {
      width: 560px;
      max-width: 92%;
      margin: 8px auto;
      padding: 8px;
      border-radius: 6px;
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(0,0,0,0.15));
      border: 2px solid rgba(255,255,255,0.06);
      box-shadow: 0 18px 40px rgba(0,0,0,0.7), 0 0 20px rgba(0,0,0,0.45) inset;
      animation: lift 700ms ease-out forwards;
      transform: translateY(8px);
      opacity: 0;
    }
    
    .portrait {
      display: block;
      width: 100%;
      height: 320px;
      object-fit: cover;
      border-radius: 4px;
      filter: grayscale(70%) contrast(1.05) brightness(0.9);
      box-shadow: 0 10px 30px rgba(0,0,0,0.6);
      border: 1px solid rgba(255,255,255,0.04);
    }

    /* ============================================
       9. TITLE
       ============================================ */
    .title {
      margin: 26px 0 12px;
      text-align: center;
      font-weight: 800;
      letter-spacing: 6px;
      font-size: 56px;
      color: #e6e6e6;
      display: flex;
      gap: 14px;
      align-items: center;
      justify-content: center;
      animation: lift 700ms ease-out forwards;
      animation-delay: 120ms;
      transform: translateY(8px);
      opacity: 0;
    }
    
    .title .accent { 
      font-weight: 900; 
      color: #cfcfcf; 
    }

    /* ============================================
       10. TERMINAL
       ============================================ */
    .terminal {
      width: 720px;
      max-width: 94%;
      margin: 8px auto;
      background: linear-gradient(180deg, rgba(0,0,0,0.55), rgba(0,0,0,0.3));
      border-radius: 10px;
      padding: 18px;
      border: 1px solid rgba(255,255,255,0.04);
      box-shadow: 0 16px 50px rgba(0,0,0,0.65);
      animation: lift 700ms ease-out forwards;
      animation-delay: 240ms;
      transform: translateY(8px);
      opacity: 0;
    }
    
    .terminal .header { 
      display: flex; 
      gap: 10px; 
      align-items: center; 
      margin-bottom: 8px; 
      color: #bdbdbd; 
      font-size: 13px; 
    }
    
    .circles { 
      display: flex; 
      gap: 6px; 
      opacity: 0.85; 
    }
    
    .circles span { 
      width: 10px; 
      height: 10px; 
      border-radius: 50%; 
      display: block; 
      box-shadow: 0 1px 0 rgba(255,255,255,0.02) inset; 
    }
    
    .c1 { background: #ff6b6b; } 
    .c2 { background: #ffb76b; } 
    .c3 { background: #6bff9e; }

    .terminal .content { 
      font-family: "Courier New", monospace; 
      color: #9ffea8; 
      background: transparent; 
      font-size: 15px; 
      padding: 10px 2px; 
      line-height: 1.6; 
    }
    
    .prompt { 
      color: #8bdfff; 
      font-weight: 700; 
    }
    
    .green { 
      color: #5ecf7a; 
      font-weight: 700; 
    }
    
    .arabic { 
      color: #3ddc6d; 
      font-weight: 700; 
      display: block; 
      margin-top: 8px; 
    }

    /* ============================================
       11. FOOTER
       ============================================ */
    .footer { 
      margin-top: 20px; 
      font-size: 11px; 
      color: rgba(200,200,200,0.23); 
      letter-spacing: 2px; 
      text-align: center; 
    }

    .muted { 
      color: rgba(200,200,200,0.45); 
      font-size: 13px; 
    }

    /* ============================================
       12. RESPONSIVE DESIGN
       ============================================ */
    @media (max-width: 920px) {
      .portrait { 
        height: 260px; 
      }
      
      .title { 
        font-size: 40px; 
      }
      
      .terminal { 
        width: 92%; 
      }
      
      .side-panel { 
        display: none; 
      }
      
      .loader-logo { 
        font-size: 36px; 
      }
      
      .progress-text { 
        font-size: 28px; 
      }
    }
    
    @media (max-width: 600px) {
      .title { 
        font-size: 30px; 
        letter-spacing: 3px; 
      }
      
      .loader-logo { 
        font-size: 28px; 
        letter-spacing: 4px; 
      }
      
      .progress-text { 
        font-size: 24px; 
      }
    }
  </style>


  <!-- ============================================
       LOADING SCREEN
       ============================================ -->
  <div id="loading-screen" class="hidden" style="display: none;">
    <div class="loader-container">
      <div class="loader-logo">
        <span class="accent">HACKED</span> BY alza7f_
      </div>
      <div class="progress-container">
        <div class="progress-bar">
          <div class="progress-fill" id="progress-fill" style="width: 100%;"></div>
        </div>
        <div class="progress-text" id="progress-text">100%</div>
        <div class="loading-status" id="loading-status">READY!</div>
      </div>
    </div>
  </div>

  <!-- ============================================
       GRID BACKGROUND
       ============================================ -->
  <div class="grid-bg" aria-hidden="true"></div>

  <!-- ============================================
       TOP BAR
       ============================================ -->
  

  <!-- ============================================
       LEFT PANEL
       ============================================ -->
  <nav class="side-panel side-left" role="navigation" aria-label="لوحة يسار">
    <h4>امك او مليون ريال ؟
    :</h4>
    <a class="btn" href="https://anansbsnsnnsns.github.io/ansass/#" onclick="return false">تحب امك ولا ابوك</a>
    <a class="btn" href="https://anansbsnsnnsns.github.io/ansass/#" onclick="كسمكم" <="" a=""></a>
    <a class="btn" href="https://anansbsnsnnsns.github.io/ansass/#" onclick="return false">ابو قحط اكبر ديوث ينزل امه ستوري !</a>
    <a class="btn" href="https://anansbsnsnnsns.github.io/ansass/#" onclick="return false"></a> حسابي دسكورد uu66.
    
  </nav>

  <!-- ============================================
       RIGHT PANEL
       ============================================ -->
  ازنى سيرفر ريسبيكت ماستر

  <!-- ============================================
       MAIN CONTENT
       ============================================ -->
  <main class="wrap" role="main" aria-live="polite">
    <!-- Portrait Image -->
    <div class="portrait-wrap">
      ابو قحط احب امك 💖
ابو قحط جيب امك ❤😍
                                          ----ريسبيكت ماستر ازنى سيرفر
    </div>
    
    <!-- Terminal -->
    
  </main>

  <!-- ============================================
       JAVASCRIPT
       ============================================ -->
  <script>
    // ============================================
    // 1. LOADING SCREEN LOGIC
    // ============================================
    (function initLoadingScreen() {
      const loadingScreen = document.getElementById('loading-screen');
      const progressFill = document.getElementById('progress-fill');
      const progressText = document.getElementById('progress-text');
      const loadingStatus = document.getElementById('loading-status');

      const statuses = [
        'INITIALIZING...',
        'LOADING SYSTEMS...',
        'CONNECTING...',
        'BYPASSING SECURITY...',
        'ACCESSING DATABASE...',
        'LOADING MODULES...',
        'FINALIZING...',
        'READY!'
      ];

      let progress = 0;
      const duration = 3000; // 3 seconds
      const interval = 30;
      const increment = (100 / duration) * interval;

      const loader = setInterval(() => {
        progress += increment;
        
        if (progress >= 100) {
          progress = 100;
          clearInterval(loader);
          
          progressFill.style.width = '100%';
          progressText.textContent = '100%';
          loadingStatus.textContent = 'READY!';
          
          setTimeout(() => {
            loadingScreen.classList.add('hidden');
            setTimeout(() => {
              loadingScreen.style.display = 'none';
              startTerminalAnimation();
            }, 800);
          }, 500);
        } else {
          progressFill.style.width = progress + '%';
          progressText.textContent = Math.floor(progress) + '%';
          
          const statusIndex = Math.floor((progress / 100) * (statuses.length - 1));
          loadingStatus.textContent = statuses[statusIndex];
        }
      }, interval);
    })();

    // ============================================
    // 2. TERMINAL ANIMATION
    // ============================================
    function startTerminalAnimation() {
      const term = document.getElementById('term');
      const lines = [
        '<div><span class="prompt">server@system:~$</span> <span>why?</span></div>',
        '<div class="arabic"><span class="green">alza7f_ :</span> السلام عليكم تعالو تيك  وترقبو مقطعكم alza7f_ </div>'
      ];

      term.innerHTML = '';
      let currentLineIndex = 0;

      function typeText(html, speed, callback) {
        const element = document.createElement('div');
        element.className = 'typing-line';
        term.appendChild(element);

        let charIndex = 0;
        const fullText = html;
        
        const typingInterval = setInterval(() => {
          charIndex++;
          element.innerHTML = fullText.slice(0, charIndex);
          element.scrollIntoView({ behavior: 'smooth', block: 'end' });
          
          if (charIndex >= fullText.length) {
            clearInterval(typingInterval);
            setTimeout(callback, 300);
          }
        }, speed);
      }

      function typeNextLine() {
        if (currentLineIndex >= lines.length) return;
        
        typeText(lines[currentLineIndex], 12, () => {
          currentLineIndex++;
          typeNextLine();
        });
      }

      setTimeout(typeNextLine, 500);
    }
  </script>



</body></html>
