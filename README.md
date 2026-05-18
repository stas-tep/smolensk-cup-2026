<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes, viewport-fit=cover">
    <title>Смоленский летний кубок 2026 · Корпорация SMOLENSK</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Inter', sans-serif; background: #0a0a1a; color: white; scroll-behavior: smooth; overflow-x: hidden; }

        /* ФОН С РАЗЛИТОЙ КРАСКОЙ */
        .ink-bg { position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; overflow: hidden; }
        .splat { position: absolute; border-radius: 65% 35% 70% 30% / 45% 55% 45% 55%; filter: blur(40px); opacity: 0.5; animation: floatSplat 16s infinite alternate; }
        @keyframes floatSplat { 0% { transform: translate(0,0) scale(1) rotate(0deg); } 100% { transform: translate(2%,3%) scale(1.08) rotate(3deg); } }
        .squiggle { position: absolute; border-radius: 40% 60% 70% 30% / 50% 60% 40% 50%; filter: blur(28px); opacity: 0.35; animation: squirm 14s infinite alternate; }
        @keyframes squirm { 0% { transform: rotate(0deg) scale(1); } 100% { transform: rotate(5deg) scale(1.04); } }
        .drop { position: absolute; border-radius: 50%; filter: blur(6px); animation: drip 8s infinite alternate; }
        @keyframes drip { 0% { transform: translateY(0) scale(1); opacity: 0.4; } 100% { transform: translateY(12px) scale(0.9); opacity: 0.7; } }

        .container { max-width: 1400px; margin: 0 auto; padding: 0 32px; position: relative; z-index: 10; }

        /* ШАПКА */
        .header { padding: 24px 0 20px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 20px; border-bottom: 2px solid rgba(255,200,80,0.6); }
        .logo { font-size: 24px; font-weight: 800; background: linear-gradient(135deg,#FFE484,#ffaa33,#ff5500); -webkit-background-clip: text; background-clip: text; color: transparent; }
        .nav-links { display: flex; gap: 28px; align-items: center; flex-wrap: wrap; }
        .nav-links a { color: #FFE4B5; text-decoration: none; font-weight: 600; transition: 0.2s; font-size: 1rem; }
        .nav-links a:hover { color: #ffaa33; text-shadow: 0 0 4px #ffaa33; }
        .buy-btn { background: linear-gradient(95deg,#ef4444,#f97316); border: none; padding: 10px 28px; border-radius: 60px; font-weight: 800; color: white; cursor: pointer; transition: 0.2s; box-shadow: 0 4px 0 #a16207; }
        .buy-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 0 #a16207; background: linear-gradient(95deg,#f97316,#eab308); }

        /* ГЛАВНЫЙ ЗАГОЛОВОК */
        .hero-title-block { display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; margin: 60px 0 50px; gap: 40px; }
        .title-wrapper { position: relative; display: inline-block; }
        .main-title { font-size: 64px; font-weight: 900; line-height: 1.1; letter-spacing: -1px; background: linear-gradient(135deg,#FFF5E0,#FFDD88,#FF8844); -webkit-background-clip: text; background-clip: text; color: transparent; position: relative; z-index: 2; }
        .title-oval { position: absolute; top: -15px; left: -25px; right: -25px; bottom: -15px; border: 3px solid rgba(255,200,80,0.8); border-radius: 60% 40% 70% 30% / 50% 60% 40% 50%; animation: borderWobble 6s infinite alternate; pointer-events: none; }
        @keyframes borderWobble { 0% { border-radius: 60% 40% 70% 30% / 50% 60% 40% 50%; transform: rotate(0deg); } 100% { border-radius: 40% 60% 30% 70% / 60% 40% 60% 40%; transform: rotate(2deg); } }
        .main-title small { font-size: 22px; font-weight: 500; color: #FFDD99; display: block; margin-top: 8px; }

        /* ТАЙМЕР */
        .circle-timer { background: rgba(0,0,0,0.55); backdrop-filter: blur(12px); border-radius: 50%; width: 180px; height: 180px; display: flex; flex-direction: column; align-items: center; justify-content: center; border: 2px solid #facc15; box-shadow: 0 0 32px rgba(255,180,0,0.5); position: relative; flex-shrink: 0; }
        .timer-sticks-circle { position: absolute; width: 100%; height: 100%; top: 0; left: 0; }
        .stick-dot { position: absolute; width: 6px; height: 24px; background: rgba(255,255,255,0.3); border-radius: 3px; transform-origin: center; }
        .stick-dot.active { background: #facc15; box-shadow: 0 0 6px #ffcc44; }
        .timer-inner { text-align: center; z-index: 2; }
        .timer-label-small { font-size: 12px; font-weight: 700; color: #FFDD88; letter-spacing: 2px; }
        .timer-days { font-size: 52px; font-weight: 800; font-family: monospace; background: linear-gradient(135deg,#fff,#FFDD88); -webkit-background-clip: text; background-clip: text; color: transparent; line-height: 1; }
        .timer-unit { font-size: 13px; color: #FFE4B5; font-weight: 600; }

        /* КАРУСЕЛЬ (универсальная для постов и видео) */
        .carousel-section { margin: 70px 0; position: relative; min-height: 540px; }
        .carousel-container { position: relative; min-height: 520px; display: flex; align-items: center; justify-content: center; perspective: 1200px; }
        .carousel-card { position: absolute; width: 330px; background: rgba(12,16,28,0.92); backdrop-filter: blur(14px); border-radius: 32px; overflow: hidden; border: 1px solid rgba(255,180,60,0.5); box-shadow: 0 20px 35px -12px rgba(0,0,0,0.6); transition: all 0.55s cubic-bezier(0.25, 0.95, 0.4, 1.05); cursor: pointer; z-index: 10; opacity: 0.85; }
        .carousel-card.pos-0 { transform: translateX(-500px) translateZ(-110px) rotateY(15deg) scale(0.68); left: 50%; top: 50%; margin-left: -165px; margin-top: -170px; opacity: 0.55; z-index: 3; }
        .carousel-card.pos-1 { transform: translateX(-270px) translateZ(-55px) rotateY(8deg) scale(0.84); left: 50%; top: 50%; margin-left: -165px; margin-top: -170px; opacity: 0.72; z-index: 8; }
        .carousel-card.pos-2 { transform: translateX(0) rotateY(0deg) scale(1); left: 50%; top: 50%; margin-left: -165px; margin-top: -170px; opacity: 1; z-index: 20; border-width: 2px; border-color: #facc15; cursor: default; }
        .carousel-card.pos-3 { transform: translateX(270px) translateZ(-55px) rotateY(-8deg) scale(0.84); left: 50%; top: 50%; margin-left: -165px; margin-top: -170px; opacity: 0.72; z-index: 8; }
        .carousel-card.pos-4 { transform: translateX(500px) translateZ(-110px) rotateY(-15deg) scale(0.68); left: 50%; top: 50%; margin-left: -165px; margin-top: -170px; opacity: 0.55; z-index: 3; }
        .card-image { width: 100%; height: 200px; background-size: cover; background-position: center; position: relative; display: flex; align-items: center; justify-content: center; }
        .carousel-card:not(.pos-2) .open-overlay { position: absolute; width: 58px; height: 58px; background: rgba(0,0,0,0.7); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 26px; backdrop-filter: blur(4px); border: 1.5px solid #ffaa44; color: #ffaa44; transition: 0.2s; pointer-events: none; }
        .carousel-card:not(.pos-2):hover .open-overlay { transform: scale(1.12); background: #ff7700; color: #0a0a0c; }
        .card-content { padding: 18px 20px; background: rgba(0,0,0,0.8); }
        .card-title { font-weight: 700; font-size: 1rem; color: #FFE4B5; margin-bottom: 6px; }
        .card-sub { font-size: 0.7rem; color: #FFAA66; }
        .center-btn { position: absolute; bottom: 18px; left: 50%; transform: translateX(-50%); background: linear-gradient(95deg,#ff7700,#ffaa33); border: none; padding: 9px 28px; border-radius: 60px; font-weight: 700; font-size: 0.95rem; color: #0f0f1c; cursor: pointer; z-index: 25; transition: 0.2s; white-space: nowrap; }
        .center-btn:hover { transform: translateX(-50%) scale(1.05); background: linear-gradient(95deg,#ffaa33,#ffdd77); }
        @media (max-width: 1100px) { .carousel-card { width: 290px; margin-left: -145px; margin-top: -150px; } .carousel-card.pos-0 { transform: translateX(-430px) scale(0.64); } .carousel-card.pos-1 { transform: translateX(-230px) scale(0.8); } .carousel-card.pos-3 { transform: translateX(230px) scale(0.8); } .carousel-card.pos-4 { transform: translateX(430px) scale(0.64); } .card-image { height: 180px; } }
        @media (max-width: 850px) { .carousel-card { width: 250px; margin-left: -125px; margin-top: -130px; } .carousel-card.pos-0 { transform: translateX(-370px) scale(0.6); } .carousel-card.pos-1 { transform: translateX(-200px) scale(0.74); } .carousel-card.pos-3 { transform: translateX(200px) scale(0.74); } .carousel-card.pos-4 { transform: translateX(370px) scale(0.6); } .card-image { height: 155px; } }
        @media (max-width: 650px) { .carousel-section { min-height: 460px; } .carousel-card { width: 210px; margin-left: -105px; margin-top: -110px; } .carousel-card.pos-0 { transform: translateX(-300px) scale(0.55); } .carousel-card.pos-1 { transform: translateX(-160px) scale(0.7); } .carousel-card.pos-3 { transform: translateX(160px) scale(0.7); } .carousel-card.pos-4 { transform: translateX(300px) scale(0.55); } .card-image { height: 130px; } }

        /* КРИВЫЕ ЗАГОЛОВКИ РАЗДЕЛОВ (УВЕЛИЧЕННЫЕ) */
        .cursive-title { text-align: center; margin-bottom: 35px; position: relative; }
        .cursive-title span { display: inline-block; font-size: 3.8rem; font-weight: 900; text-transform: uppercase; letter-spacing: 5px; background: linear-gradient(135deg,#FFE484,#FFAA44,#FF5500); -webkit-background-clip: text; background-clip: text; color: transparent; filter: drop-shadow(0 0 10px rgba(255,100,0,0.4)); }
        .title-crooked-1 { transform: rotate(-5deg) skewX(-4deg); text-decoration: underline wavy #ffaa55; text-underline-offset: 15px; }
        .title-crooked-2 { transform: rotate(4deg) skewX(3deg); text-decoration: underline wavy #ff8844; text-underline-offset: 13px; }
        .title-crooked-3 { transform: rotate(-3deg) skewX(5deg); text-decoration: underline wavy #ffaa66; text-underline-offset: 16px; }
        .title-crooked-4 { transform: rotate(6deg) skewX(-3deg); text-decoration: underline wavy #ff9933; text-underline-offset: 12px; }

        /* ГРАФИК */
        .schedule-grid { display: flex; flex-direction: column; gap: 28px; margin: 40px 0; }
        .prize-info { background: rgba(0,0,0,0.55); border-radius: 48px; padding: 24px 32px; text-align: center; border: 1px solid #facc15; }
        .prize-info h3 { font-size: 1.8rem; font-weight: 800; background: linear-gradient(135deg,#FFE484,#FFAA44); -webkit-background-clip: text; background-clip: text; color: transparent; }
        .prize-amount { font-size: 2.8rem; font-weight: 900; color: #facc15; text-shadow: 0 0 8px rgba(255,200,0,0.5); margin: 12px 0; }
        .schedule-row { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 28px; }
        .schedule-card { background: rgba(12,16,28,0.85); backdrop-filter: blur(12px); border-radius: 36px; padding: 24px; border: 1px solid rgba(255,180,60,0.5); transition: 0.2s; }
        .schedule-card:hover { border-color: #facc15; transform: translateY(-4px); }
        .schedule-day { font-size: 1.4rem; font-weight: 800; color: #facc15; margin-bottom: 12px; display: flex; align-items: center; gap: 8px; }
        .schedule-place { font-size: 1.2rem; font-weight: 700; color: white; margin: 8px 0; }
        .schedule-prize { font-size: 1.3rem; font-weight: 800; background: linear-gradient(135deg,#FFD966,#FF8C33); -webkit-background-clip: text; background-clip: text; color: transparent; margin: 8px 0; }
        .total-prize { margin-top: 28px; background: linear-gradient(95deg,rgba(255,100,0,0.2),rgba(255,200,0,0.1)); border-radius: 40px; padding: 20px; text-align: center; border: 1px dashed #ffaa55; }

        /* ПОБЕДИТЕЛИ И УЧАСТНИКИ (ОБЫЧНЫЙ ВИД) */
        .winners-compact { display: flex; flex-wrap: wrap; gap: 35px; justify-content: center; margin: 60px 0 40px; }
        .winners-card { flex: 1; min-width: 300px; background: rgba(12,16,28,0.78); backdrop-filter: blur(14px); border-radius: 44px; padding: 28px 24px; border: 1px solid rgba(255,180,60,0.55); }
        .winners-card h3 { text-align: center; font-size: 1.7rem; font-weight: 800; background: linear-gradient(135deg,#FFE484,#FFAA44); -webkit-background-clip: text; background-clip: text; color: transparent; margin-bottom: 25px; }
        .winner-item, .stage-item-compact { background: rgba(0,0,0,0.45); border-radius: 60px; padding: 14px 20px; margin-bottom: 14px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px; border-left: 4px solid #facc15; transition: 0.2s; }
        .stage-item-compact { cursor: pointer; }
        .stage-item-compact:hover { background: rgba(255,100,0,0.2); transform: translateX(4px); }
        .stage-name { font-weight: 700; color: #FFD966; font-size: 1rem; }
        .stage-count { font-size: 0.75rem; background: #ff770033; padding: 3px 12px; border-radius: 40px; }
        .participants-list-compact { max-height: 0; overflow: hidden; transition: max-height 0.4s cubic-bezier(0.33, 1, 0.68, 1); margin-top: 0; }
        .stage-item-compact.open .participants-list-compact { max-height: 350px; margin-top: 14px; }
        .participant-row { display: flex; align-items: center; gap: 12px; background: rgba(0,0,0,0.35); border-radius: 50px; padding: 10px 18px; margin-bottom: 10px; font-size: 0.9rem; }

        /* БОКОВАЯ НАВИГАЦИЯ */
        .side-nav { position: fixed; right: 20px; top: 50%; transform: translateY(-50%); z-index: 1000; display: flex; flex-direction: column; gap: 16px; }
        .nav-dot { width: 48px; height: 48px; border-radius: 40% 60% 55% 45% / 50% 45% 55% 50%; background: rgba(20,20,40,0.75); backdrop-filter: blur(8px); border: 1.5px solid rgba(255,200,80,0.7); display: flex; align-items: center; justify-content: center; cursor: pointer; transition: 0.3s; font-size: 14px; font-weight: 800; color: #FFE484; }
        .nav-dot:hover { background: linear-gradient(135deg,#ff7700,#facc15); color: #0a0a0c; transform: scale(1.12); }
        .nav-dot.active { background: linear-gradient(135deg,#ffaa33,#ff5500); color: white; box-shadow: 0 0 18px rgba(255,100,0,0.7); }

        /* ФУТЕР */
        .fullscreen-footer { width: 100vw; position: relative; left: 50%; right: 50%; margin-left: -50vw; margin-right: -50vw; margin-top: 70px; padding: 80px 20px; background: radial-gradient(ellipse at 50% 30%,rgba(255,100,0,0.25),rgba(0,0,0,0.95)); text-align: center; border-top: 3px solid #facc15; border-bottom: 3px solid #facc15; }
        .glow-text { font-size: 58px; font-weight: 900; background: linear-gradient(135deg,#FFEEAA,#FFAA44,#FF5500); -webkit-background-clip: text; background-clip: text; color: transparent; animation: epicGlow 2s ease infinite alternate; }
        @keyframes epicGlow { 0% { filter: drop-shadow(0 0 5px #ff6600); } 100% { filter: drop-shadow(0 0 28px #ffaa33); } }
        .footer-sub { margin-top: 22px; color: #FFE4B5; font-size: 1rem; }

        /* МОДАЛКА */
        .post-modal { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.94); backdrop-filter: blur(16px); z-index: 1000; display: flex; align-items: center; justify-content: center; visibility: hidden; opacity: 0; transition: 0.25s; }
        .post-modal.active { visibility: visible; opacity: 1; }
        .modal-content { max-width: 620px; width: 90%; background: linear-gradient(145deg,#141a28,#0b0f18); border-radius: 52px; padding: 36px; border: 2px solid #facc15; max-height: 85vh; overflow-y: auto; }
        .modal-close { position: absolute; top: 22px; right: 28px; font-size: 30px; cursor: pointer; color: #FFE4B5; transition: 0.2s; }
        .modal-close:hover { color: #ff7700; transform: scale(1.1); }

        @media (max-width: 850px) { .container { padding: 0 24px; } .main-title { font-size: 48px; } .cursive-title span { font-size: 2.8rem; } }
        @media (max-width: 700px) { .header { flex-direction: column; text-align: center; } .hero-title-block { flex-direction: column; align-items: center; text-align: center; } .main-title { font-size: 42px; } .circle-timer { width: 150px; height: 150px; } .winners-compact { flex-direction: column; } .side-nav { display: none; } .cursive-title span { font-size: 2.2rem; letter-spacing: 3px; } }
    </style>
</head>
<body>
<div class="ink-bg">
    <div class="splat" style="width:450px;height:450px;background:#ef4444;top:-120px;left:-120px;opacity:0.45"></div>
    <div class="splat" style="width:520px;height:520px;background:#3b82f6;bottom:-130px;right:-130px;opacity:0.4"></div>
    <div class="splat" style="width:380px;height:380px;background:#facc15;top:20%;right:-50px;opacity:0.45"></div>
    <div class="splat" style="width:420px;height:420px;background:#22c55e;bottom:10%;left:-80px;opacity:0.4"></div>
    <div class="splat" style="width:300px;height:300px;background:#a855f7;top:60%;right:10%;opacity:0.35"></div>
</div>

<div class="container">
    <div class="header">
        <div class="logo">КОРПОРАЦИЯ SMOLENSK 2026</div>
        <div class="nav-links">
            <a href="#" onclick="scrollToBlock('carouselPosts')">ПОСТЫ</a>
            <a href="#" onclick="scrollToBlock('carouselVideos')">ВИДЕО</a>
            <a href="#" onclick="scrollToBlock('scheduleBlock')">ГРАФИК</a>
            <a href="#" onclick="scrollToBlock('winnersBlock')">РЕЙТИНГ</a>
            <button class="buy-btn" onclick="openModal()">УЧАСТВОВАТЬ</button>
        </div>
    </div>

    <div class="hero-title-block" id="hero-title-block">
        <div class="title-wrapper"><div class="title-oval"></div><div class="main-title">СМОЛЕНСКИЙ <br>ЛЕТНИЙ КУБОК 2026<small>главное событие лета</small></div></div>
        <div class="circle-timer" id="circleTimer"><div class="timer-sticks-circle" id="stickCircle"></div><div class="timer-inner"><div class="timer-label-small">ОСТАЛОСЬ</div><div class="timer-days" id="circleDays">87</div><div class="timer-unit">ДНЕЙ</div></div></div>
    </div>

    <!-- ПОСТЫ с кривым заголовком -->
    <div id="carouselPosts" class="carousel-section">
        <div class="cursive-title"><span class="title-crooked-1">📰 ПОСТЫ</span></div>
        <div class="carousel-container" id="postsCarousel"></div>
    </div>

    <!-- ВИДЕО с кривым заголовком -->
    <div id="carouselVideos" class="carousel-section">
        <div class="cursive-title"><span class="title-crooked-2">🎬 ВИДЕО</span></div>
        <div class="carousel-container" id="videosCarousel"></div>
    </div>

    <!-- ГРАФИК с кривым заголовком -->
    <div id="scheduleBlock" class="section" style="margin-top: 20px;">
        <div class="cursive-title"><span class="title-crooked-3">📅 ГРАФИК</span></div>
        <div class="schedule-grid">
            <div class="prize-info"><h3>🏆 ОБЩИЙ ПРИЗОВОЙ ФОНД 🏆</h3><div class="prize-amount">??? ₽</div><p style="color:#ddd;">Сумма будет объявлена позже</p></div>
            <div class="schedule-row">
                <div class="schedule-card"><div class="schedule-day">🎯 ??? ИЮЛЯ</div><div class="schedule-place">Квалификация</div><div class="schedule-prize">Приз: ??? ₽</div></div>
                <div class="schedule-card"><div class="schedule-day">⚡ ??? ИЮЛЯ</div><div class="schedule-place">1/4 финала</div><div class="schedule-prize">Приз: ??? ₽</div></div>
                <div class="schedule-card"><div class="schedule-day">🔥 ??? ИЮЛЯ</div><div class="schedule-place">Полуфинал</div><div class="schedule-prize">Приз: ??? ₽</div></div>
                <div class="schedule-card"><div class="schedule-day">🏆 ??? ИЮЛЯ</div><div class="schedule-place">Финал</div><div class="schedule-prize">Приз: ??? ₽</div></div>
                <div class="schedule-card"><div class="schedule-day">🎁 ??? ИЮЛЯ</div><div class="schedule-place">Закрытие</div><div class="schedule-prize">Приз: ??? ₽</div></div>
            </div>
            <div class="total-prize"><p>⭐ <strong>КАК ЭТО РАБОТАЕТ?</strong> В каждый день розыгрыша случайным образом выбираются победители! ⭐</p></div>
        </div>
    </div>

<!-- ПОБЕДИТЕЛИ И УЧАСТНИКИ (ОБЫЧНЫЙ ВИД) -->
<div id="winnersBlock" class="winners-compact">
    <div class="winners-card">
        <h3>🏆 ПОБЕДИТЕЛИ</h3>
        <div class="winner-item"><span>🥇 Квалификация</span><span>Скоро определится</span><span>??? ₽</span></div>
        <div class="winner-item"><span>🥈 1/4 финала</span><span>Скоро определится</span><span>??? ₽</span></div>
        <div class="winner-item"><span>🥉 Полуфинал</span><span>Скоро определится</span><span>??? ₽</span></div>
        <div class="winner-item"><span>🏅 Финал</span><span>Скоро определится</span><span>??? ₽</span></div>
    </div>
    <div class="winners-card">
        <h3>👥 УЧАСТНИКИ</h3>
        <div class="stage-item-compact"><div style="display:flex; justify-content:space-between;"><span class="stage-name">1 ЭТАП · Квалификация</span><span class="stage-count">0 уч.</span><span style="color:#ffaa55;">▼</span></div><div class="participants-list-compact"><div class="participant-row">Пока нет участников</div></div></div>
        <div class="stage-item-compact"><div style="display:flex; justify-content:space-between;"><span class="stage-name">2 ЭТАП · 1/4 финала</span><span class="stage-count">0 уч.</span><span style="color:#ffaa55;">▼</span></div><div class="participants-list-compact"><div class="participant-row">Пока нет участников</div></div></div>
        <div class="stage-item-compact"><div style="display:flex; justify-content:space-between;"><span class="stage-name">3 ЭТАП · Полуфинал</span><span class="stage-count">0 уч.</span><span style="color:#ffaa55;">▼</span></div><div class="participants-list-compact"><div class="participant-row">Пока нет участников</div></div></div>
        <div class="stage-item-compact"><div style="display:flex; justify-content:space-between;"><span class="stage-name">4 ЭТАП · Финал</span><span class="stage-count">0 уч.</span><span style="color:#ffaa55;">▼</span></div><div class="participants-list-compact"><div class="participant-row">Пока нет участников</div></div></div>
    </div>
</div>

<div id="footerBlock" class="fullscreen-footer"><div class="glow-text">УВИДИМСЯ НА КУБКЕ 2026</div><div class="footer-sub">КОРПОРАЦИЯ SMOLENSK · Летний кубок 2026</div></div>

<div id="buyModal" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.92); backdrop-filter:blur(12px); z-index:1000; align-items:center; justify-content:center;">
    <div style="background:linear-gradient(145deg,#141a28,#0b0f18); border-radius:48px; max-width:420px; width:90%; padding:28px 24px; text-align:center; border:2px solid #facc15;">
        <div style="font-size:42px;">🎲</div>
        <h3 style="font-size:26px; font-weight:800; color:#FFE484;">УЧАСТВОВАТЬ</h3>
        <p style="color:#ccc; margin:8px 0 20px;">Стоимость участия в розыгрыше</p>
        <div style="display:flex; flex-direction:column; gap:12px; margin-bottom:28px;"><button class="pay-option" data-price="100" data-chance="1" style="background:rgba(255,100,0,0.15); border:1px solid #facc15; border-radius:60px; padding:12px; font-weight:700; color:#FFE484; cursor:pointer;">✨ 100 ₽ ✨</button></div>
        <button onclick="closeModal()" style="background:transparent; border:1px solid #555; padding:8px 24px; border-radius:50px; color:#ccc; cursor:pointer;">Вернуться</button>
    </div>
</div>

<div id="postModal" class="post-modal"><div class="modal-content"><div class="modal-close" onclick="closePostModal()">&times;</div><div id="modalBody"></div></div></div>

<script>
    // === ДАННЫЕ ДЛЯ ПОСТОВ ===
    const postsData = [
        { title:"СКОРО", subtitle:"18 мая 2026", full:"СКОРО… Собираем максимальное количество лайков 🔥", image:"https://i.ytimg.com/vi/xqKJ6UT-oQU/maxresdefault.jpg" },
        { title:"Смоленский кубок 2026", subtitle:"1 июня 2026", full:"В течение месяца будет проводиться масштабный розыгрыш.", image:"https://i.ytimg.com/vi/EhNJkT4SkWQ/hqdefault.jpg" },
        { title:"ПРИЗОВОЙ ФОНД", subtitle:"5 мая 2026", full:"Благодаря спонсорам призовой фонд Летнего кубка увеличивается. Следите за обновлениями!", image:"https://i.ytimg.com/vi/o_uVHyQ0X0g/hqdefault.jpg" },
        { title:"МУЗЫКАЛЬНЫЙ ПЛЕЙЛИСТ", subtitle:"28 апреля 2026", full:"В разделе «Музыкальная волна» вы найдёте эксклюзивные треки, которые создают атмосферу праздника.", image:"https://i.ytimg.com/vi/x0NcDqqSahc/hqdefault.jpg" },
        { title:"НОВЫЙ ДИЗАЙН", subtitle:"20 апреля 2026", full:"Встречайте полностью обновлённый сайт Корпорации SMOLENSK. Наслаждайтесь новым опытом!", image:"https://i.ytimg.com/vi/EhNJkT4SkWQ/hqdefault.jpg" }
    ];

    // === ДАННЫЕ ДЛЯ ВИДЕО (VK) ===
    const videosData = [
        { title:"Трейлер 2026", url:"https://vkvideo.ru/video-229194546_456239028", image:"https://i.ytimg.com/vi/x0NcDqqSahc/hqdefault.jpg" },
        { title:"За кулисами", url:"https://vkvideo.ru/video-229194546_456239026", image:"https://i.ytimg.com/vi/EhNJkT4SkWQ/hqdefault.jpg" },
        { title:"Интервью", url:"https://vkvideo.ru/video-229194546_456239023", image:"https://i.ytimg.com/vi/o_uVHyQ0X0g/hqdefault.jpg" },
        { title:"Лучшие моменты", url:"https://vkvideo.ru/video-229194546_456239028", image:"https://i.ytimg.com/vi/x0NcDqqSahc/hqdefault.jpg" },
        { title:"Анонс финала", url:"https://vkvideo.ru/video-229194546_456239026", image:"https://i.ytimg.com/vi/EhNJkT4SkWQ/hqdefault.jpg" }
    ];

    // УНИВЕРСАЛЬНАЯ КАРУСЕЛЬ (с плавной анимацией)
    function createCarousel(containerId, items, type) {
        const container = document.getElementById(containerId);
        if (!container) return;
        let cards = [];
        
        function createCard(item, posIdx) {
            const card = document.createElement('div');
            card.className = `carousel-card pos-${posIdx}`;
            card.dataset.index = posIdx;
            const imageDiv = document.createElement('div');
            imageDiv.className = 'card-image';
            imageDiv.style.backgroundImage = `url(${item.image})`;
            imageDiv.style.backgroundSize = 'cover';
            imageDiv.style.backgroundPosition = 'center';
            if (posIdx !== 2) {
                const overlay = document.createElement('div');
                overlay.className = 'open-overlay';
                overlay.innerHTML = type === 'post' ? '📖' : '▶';
                imageDiv.appendChild(overlay);
            }
            card.appendChild(imageDiv);
            const contentDiv = document.createElement('div');
            contentDiv.className = 'card-content';
            if (type === 'post') {
                contentDiv.innerHTML = `<div class="card-title">${item.title}</div><div class="card-sub">${item.subtitle}</div>`;
            } else {
                contentDiv.innerHTML = `<div class="card-title">${item.title}</div>`;
            }
            card.appendChild(contentDiv);
            return card;
        }
        
        function updatePositions(cardsArray) {
            cardsArray.forEach((card, idx) => { card.className = `carousel-card pos-${idx}`; });
            const centerCard = cardsArray[2];
            const oldBtn = centerCard.querySelector('.center-btn');
            if (oldBtn) oldBtn.remove();
            const btn = document.createElement('button');
            btn.className = 'center-btn';
            btn.textContent = type === 'post' ? '📖 ЧИТАТЬ' : '🎬 СМОТРЕТЬ';
            btn.onclick = (e) => {
                e.stopPropagation();
                const idx = parseInt(centerCard.dataset.index);
                if (type === 'post') {
                    const post = items[idx];
                    document.getElementById('modalBody').innerHTML = `<h2 style="color:#FFE484; margin-bottom:18px;">${post.title}</h2><div style="color:#FFAA66; margin-bottom:18px;">${post.subtitle}</div><img src="${post.image}" style="width:100%; border-radius:28px; margin:18px 0"><p style="color:#ddd; line-height:1.6;">${post.full}</p>`;
                    document.getElementById('postModal').classList.add('active');
                } else {
                    window.open(items[idx].url, '_blank');
                }
            };
            centerCard.querySelector('.card-image').appendChild(btn);
        }
        
        for (let i = 0; i < items.length; i++) {
            const card = createCard(items[i], i);
            container.appendChild(card);
            cards.push(card);
        }
        
        function bringToCenter(clickedCard) {
            if (clickedCard.classList.contains('pos-2')) return;
            const centerIdx = cards.findIndex(c => c.classList.contains('pos-2'));
            const clickIdx = cards.indexOf(clickedCard);
            if (clickIdx === -1 || centerIdx === -1) return;
            const shift = clickIdx - centerIdx;
            if (shift === 0) return;
            const newOrder = [...cards];
            if (shift > 0) { for (let i = 0; i < shift; i++) newOrder.unshift(newOrder.pop()); }
            else { for (let i = 0; i < -shift; i++) newOrder.push(newOrder.shift()); }
            cards = newOrder;
            cards.forEach(c => container.appendChild(c));
            updatePositions(cards);
        }
        
        cards.forEach(card => {
            card.addEventListener('click', (e) => {
                if (e.target.classList && (e.target.classList.contains('center-btn') || e.target.parentElement?.classList?.contains('center-btn'))) return;
                if (!card.classList.contains('pos-2')) bringToCenter(card);
            });
        });
        updatePositions(cards);
        window.addEventListener('resize', () => updatePositions(cards));
        return cards;
    }
    
    createCarousel('postsCarousel', postsData, 'post');
    createCarousel('videosCarousel', videosData, 'video');
    
    // ТАЙМЕР
    function updateCircleTimer() { const target = new Date(2026,6,1); const diff = target - new Date(); let daysLeft = Math.max(0, Math.floor(diff/86400000)); document.getElementById('circleDays').innerText = daysLeft; const progress = daysLeft/365; const totalSticks=24, activeSticks=Math.round((1-progress)*totalSticks), container=document.getElementById('stickCircle'); if(container){ container.innerHTML=''; const radius=72, center=90; for(let i=0;i<totalSticks;i++){ const angle=i*360/totalSticks*Math.PI/180, x=center+radius*Math.cos(angle)-3, y=center+radius*Math.sin(angle)-12; const stick=document.createElement('div'); stick.className='stick-dot'; if(i<activeSticks) stick.classList.add('active'); stick.style.left=x+'px'; stick.style.top=y+'px'; stick.style.transform=`rotate(${angle*180/Math.PI}deg)`; container.appendChild(stick); } } }
    updateCircleTimer(); setInterval(updateCircleTimer,86400000);
    
    // АККОРДЕОН
    document.querySelectorAll('.stage-item-compact').forEach(item => { item.addEventListener('click', () => { item.classList.toggle('open'); }); });
    
    // НАВИГАЦИЯ
    const sideNav = document.createElement('div'); sideNav.className='side-nav';
    const navItems = [{ id:'hero-title-block', label:'01' },{ id:'carouselPosts', label:'02' },{ id:'carouselVideos', label:'03' },{ id:'scheduleBlock', label:'04' },{ id:'winnersBlock', label:'05' }];
    navItems.forEach(item=>{ const dot=document.createElement('div'); dot.className='nav-dot'; dot.innerHTML=`<span>${item.label}</span>`; dot.onclick=()=>{ const el=document.getElementById(item.id); if(el) el.scrollIntoView({ behavior:'smooth', block:'start' }); }; sideNav.appendChild(dot); });
    document.body.appendChild(sideNav);
    function updateActiveNav(){ const scrollPos=window.scrollY+200; let activeId=null; for(let item of navItems){ const el=document.getElementById(item.id); if(el){ const top=el.offsetTop, bottom=top+el.offsetHeight; if(scrollPos>=top && scrollPos<bottom){ activeId=item.id; break; } } } document.querySelectorAll('.nav-dot').forEach((dot,idx)=>{ dot.classList.remove('active'); if(navItems[idx]?.id===activeId) dot.classList.add('active'); }); }
    window.addEventListener('scroll',updateActiveNav); window.addEventListener('load',updateActiveNav);
    window.scrollToBlock = (id) => { const el = document.getElementById(id); if(el) el.scrollIntoView({ behavior:'smooth', block:'start' }); };
    window.openModal = () => document.getElementById('buyModal').style.display='flex';
    window.closeModal = () => document.getElementById('buyModal').style.display='none';
    window.closePostModal = () => document.getElementById('postModal').classList.remove('active');
    document.querySelectorAll('.pay-option').forEach(btn=>btn.addEventListener('click',()=>{ alert('Оплата через СБП: +7 908 288-70-62'); closeModal(); }));
</script>
</body>
</html>
