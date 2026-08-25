<!DOCTYPE html>
<html lang="am">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mulu Gym - ሙሉ ጂም እና ፊቱነስ ማዕከል</title>
  
  <!-- Favicon using exact logo file -->
  <link rel="icon" type="image/png" href="./logo%20pic%20.png" />

  <!-- Font Awesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" />
  
  <!-- Firebase SDKs -->
  <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore-compat.js"></script>

  <style>
    :root {
      --primary-color: #ffcc00; /* Signature Bright Yellow */
      --primary-glow: rgba(255, 204, 0, 0.35);
      --secondary-color: #0a0a0a; /* Pitch Black */
      --card-bg: rgba(20, 20, 20, 0.85); /* Dark Glassmorphism */
      --card-hover: rgba(30, 30, 30, 0.95);
      --text-main: #ffffff;
      --text-muted: #b3b3b3;
      --border-color: #262626;
      --btn-text: #000000;
    }

    .white-accent-mode {
      --primary-color: #ffffff;
      --primary-glow: rgba(255, 255, 255, 0.35);
      --btn-text: #000000;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      scroll-behavior: smooth;
    }

    body {
      background-color: var(--secondary-color);
      color: var(--text-main);
      line-height: 1.7;
      overflow-x: hidden;
    }

    /* Header & Navigation */
    header {
      background: rgba(10, 10, 10, 0.92);
      padding: 0.9rem 2rem;
      position: sticky;
      top: 0;
      z-index: 1000;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 2px solid var(--primary-color);
      backdrop-filter: blur(12px);
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.8);
    }

    .logo {
      font-size: 1.5rem;
      font-weight: 800;
      color: var(--primary-color);
      display: flex;
      align-items: center;
      gap: 12px;
      text-transform: uppercase;
      text-decoration: none;
      letter-spacing: 1px;
    }

    .logo img {
      width: 46px;
      height: 46px;
      border-radius: 50%;
      object-fit: cover;
      border: 2px solid var(--primary-color);
      box-shadow: 0 0 10px var(--primary-glow);
    }

    nav ul {
      display: flex;
      list-style: none;
      gap: 22px;
      align-items: center;
    }

    nav a {
      color: var(--text-main);
      text-decoration: none;
      font-weight: 600;
      font-size: 0.95rem;
      transition: color 0.3s ease;
    }

    nav a:hover {
      color: var(--primary-color);
    }

    .header-controls {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .theme-btn, .lang-btn {
      background: var(--primary-color);
      color: var(--btn-text);
      border: none;
      padding: 8px 14px;
      border-radius: 6px;
      cursor: pointer;
      font-weight: 700;
      font-size: 0.85rem;
      transition: all 0.3s ease;
      box-shadow: 0 0 8px var(--primary-glow);
    }

    .theme-btn:hover, .lang-btn:hover {
      opacity: 0.9;
      transform: translateY(-2px);
    }

    .mobile-menu-btn {
      display: none;
      background: none;
      border: none;
      color: var(--primary-color);
      font-size: 1.8rem;
      cursor: pointer;
    }

    /* Hero Section */
    .hero {
      background: linear-gradient(rgba(0, 0, 0, 0.78), rgba(10, 10, 10, 0.92)), 
                  url('./welcome%20pic%20.jpg') center/cover no-repeat;
      min-height: 88vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 2rem 20px;
    }

    .hero-subtitle-tag {
      color: var(--primary-color);
      font-size: 1.15rem;
      font-weight: 700;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 0.8rem;
    }

    .hero h1 {
      font-size: 3.8rem;
      color: #ffffff;
      margin-bottom: 1rem;
      text-transform: uppercase;
      letter-spacing: 2px;
      line-height: 1.1;
      text-shadow: 0 0 20px rgba(0, 0, 0, 0.9);
    }

    .hero h1 span {
      color: var(--primary-color);
    }

    .hero p {
      font-size: 1.25rem;
      margin-bottom: 2.2rem;
      max-width: 720px;
      color: var(--text-muted);
    }

    .hero-btn-group {
      display: flex;
      gap: 16px;
      flex-wrap: wrap;
      justify-content: center;
    }

    .btn {
      background: var(--primary-color);
      color: var(--btn-text);
      padding: 14px 32px;
      text-decoration: none;
      border-radius: 6px;
      font-size: 1rem;
      font-weight: 700;
      transition: all 0.3s ease;
      border: 2px solid var(--primary-color);
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 10px;
      text-transform: uppercase;
      box-shadow: 0 4px 15px var(--primary-glow);
    }

    .btn-secondary {
      background: transparent;
      color: var(--text-main);
      border: 2px solid var(--border-color);
      box-shadow: none;
    }

    .btn-secondary:hover {
      border-color: var(--primary-color);
      color: var(--primary-color);
      background: rgba(255, 204, 0, 0.05);
    }

    .btn:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 25px var(--primary-glow);
    }

    /* General Section Layout */
    section {
      padding: 5rem 2rem;
      max-width: 1200px;
      margin: 0 auto;
    }

    .section-title {
      text-align: center;
      font-size: 2.3rem;
      margin-bottom: 2.5rem;
      color: var(--primary-color);
      text-transform: uppercase;
      position: relative;
      letter-spacing: 1px;
    }

    .section-title::after {
      content: '';
      width: 70px;
      height: 4px;
      background: var(--primary-color);
      display: block;
      margin: 12px auto 0;
      border-radius: 2px;
      box-shadow: 0 0 10px var(--primary-glow);
    }

    /* About Us Section */
    .about-content {
      background: var(--card-bg);
      padding: 2.5rem;
      border-radius: 12px;
      border: 1px solid var(--border-color);
      display: flex;
      flex-direction: column;
      gap: 1.3rem;
      box-shadow: 0 8px 30px rgba(0, 0, 0, 0.5);
    }

    .about-content p {
      color: var(--text-muted);
      font-size: 1.02rem;
      text-align: justify;
      border-left: 3px solid var(--primary-color);
      padding-left: 16px;
    }

    /* Services Grid */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 25px;
    }

    .service-card {
      background: var(--card-bg);
      padding: 2.5rem 1.8rem;
      border-radius: 12px;
      text-align: center;
      border: 1px solid var(--border-color);
      transition: all 0.35s ease;
      position: relative;
      overflow: hidden;
    }

    .service-card:hover {
      border-color: var(--primary-color);
      transform: translateY(-8px);
      background: var(--card-hover);
      box-shadow: 0 10px 30px var(--primary-glow);
    }

    .service-card i {
      font-size: 3rem;
      color: var(--primary-color);
      margin-bottom: 1.2rem;
    }

    .service-card h3 {
      font-size: 1.35rem;
      margin-bottom: 0.8rem;
      color: var(--text-main);
    }

    .service-card p {
      color: var(--text-muted);
      font-size: 0.95rem;
    }

    /* Booking Section */
    .booking-container {
      background: var(--card-bg);
      padding: 2.5rem;
      border-radius: 12px;
      border: 1px solid var(--border-color);
      max-width: 720px;
      margin: 0 auto;
      box-shadow: 0 10px 35px rgba(0, 0, 0, 0.6);
    }

    .booking-form {
      display: flex;
      flex-direction: column;
      gap: 18px;
    }

    .form-group {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .form-group label {
      font-weight: 600;
      color: var(--text-main);
      font-size: 0.95rem;
    }

    .booking-form input, .booking-form select, .booking-form textarea {
      padding: 14px;
      background: #000000;
      border: 1px solid var(--border-color);
      border-radius: 6px;
      font-size: 1rem;
      color: var(--text-main);
      transition: border-color 0.3s;
    }

    .booking-form input:focus, .booking-form select:focus, .booking-form textarea:focus {
      outline: none;
      border-color: var(--primary-color);
      box-shadow: 0 0 8px var(--primary-glow);
    }

    /* Gallery Grid & Lightbox */
    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 22px;
    }

    .gallery-item {
      position: relative;
      overflow: hidden;
      border-radius: 12px;
      border: 1px solid var(--border-color);
      cursor: pointer;
      aspect-ratio: 4/3;
    }

    .gallery-item img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.5s ease;
      display: block;
    }

    .gallery-item:hover img {
      transform: scale(1.08);
    }

    .gallery-overlay {
      position: absolute;
      inset: 0;
      background: rgba(0, 0, 0, 0.65);
      display: flex;
      justify-content: center;
      align-items: center;
      opacity: 0;
      transition: opacity 0.3s ease;
    }

    .gallery-item:hover .gallery-overlay {
      opacity: 1;
    }

    .gallery-overlay i {
      font-size: 2.2rem;
      color: var(--primary-color);
    }

    /* Lightbox Modal */
    .lightbox-modal {
      display: none;
      position: fixed;
      inset: 0;
      z-index: 2000;
      background: rgba(0, 0, 0, 0.94);
      backdrop-filter: blur(12px);
      justify-content: center;
      align-items: center;
      flex-direction: column;
      padding: 20px;
    }

    .lightbox-modal.active {
      display: flex;
    }

    .lightbox-content {
      max-width: 90vw;
      max-height: 80vh;
      border-radius: 8px;
      border: 2px solid var(--primary-color);
      object-fit: contain;
      box-shadow: 0 0 30px var(--primary-glow);
    }

    .lightbox-caption {
      margin-top: 15px;
      color: var(--text-main);
      font-size: 1.1rem;
      font-weight: 600;
    }

    .lightbox-close {
      position: absolute;
      top: 25px;
      right: 30px;
      font-size: 2.5rem;
      color: #fff;
      cursor: pointer;
      transition: color 0.2s;
    }

    .lightbox-close:hover { color: var(--primary-color); }

    .lightbox-nav {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      font-size: 2.5rem;
      color: #fff;
      cursor: pointer;
      padding: 15px;
      user-select: none;
      transition: color 0.2s;
    }

    .lightbox-nav:hover { color: var(--primary-color); }
    .lightbox-prev { left: 20px; }
    .lightbox-next { right: 20px; }

    /* Reviews Section */
    .reviews-container {
      background: var(--card-bg);
      padding: 2.5rem;
      border-radius: 12px;
      border: 1px solid var(--border-color);
      box-shadow: 0 10px 35px rgba(0, 0, 0, 0.5);
    }

    .avg-rating-box {
      text-align: center;
      margin-bottom: 2.5rem;
      padding-bottom: 1.5rem;
      border-bottom: 1px solid var(--border-color);
    }

    .avg-rating-score {
      font-size: 3rem;
      font-weight: 800;
      color: var(--primary-color);
    }

    .interactive-stars {
      display: flex;
      gap: 8px;
      font-size: 2rem;
      color: var(--border-color);
      cursor: pointer;
      justify-content: center;
      margin: 10px 0;
    }

    .interactive-stars .star-btn {
      transition: color 0.2s;
    }

    .interactive-stars .star-btn.active, .interactive-stars .star-btn:hover {
      color: var(--primary-color);
    }

    .review-form {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin-bottom: 2.5rem;
    }

    .review-form input, .review-form textarea {
      padding: 14px;
      background: #000000;
      border: 1px solid var(--border-color);
      border-radius: 6px;
      font-size: 1rem;
      color: var(--text-main);
    }

    .reviews-list {
      display: flex;
      flex-direction: column;
      gap: 18px;
    }

    .review-item {
      background: #000000;
      border: 1px solid var(--border-color);
      border-radius: 8px;
      padding: 1.2rem;
      transition: border-color 0.3s;
    }

    .review-item:hover {
      border-color: var(--primary-color);
    }

    .review-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-weight: 700;
      margin-bottom: 8px;
    }

    .stars-display {
      color: var(--primary-color);
      letter-spacing: 2px;
    }

    /* Contact Section */
    .contact-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 30px;
    }

    .contact-info {
      display: flex;
      flex-direction: column;
      gap: 20px;
      background: var(--card-bg);
      padding: 2.2rem;
      border-radius: 12px;
      border: 1px solid var(--border-color);
    }

    .contact-item {
      display: flex;
      align-items: center;
      gap: 16px;
      font-size: 1.05rem;
    }

    .contact-item i {
      font-size: 1.5rem;
      color: var(--primary-color);
      width: 30px;
    }

    .telegram-btn {
      background: #0088cc;
      color: #ffffff;
      padding: 14px 24px;
      border-radius: 6px;
      text-decoration: none;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      font-weight: 700;
      transition: background 0.3s ease;
      border: none;
      margin-top: 10px;
    }

    .telegram-btn:hover {
      background: #006699;
      transform: translateY(-2px);
    }

    .directions-btn {
      background: var(--primary-color);
      color: var(--btn-text);
      padding: 12px 20px;
      border-radius: 6px;
      text-decoration: none;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      font-weight: 700;
      margin-top: 10px;
    }

    .map-container iframe {
      width: 100%;
      height: 320px;
      border: 0;
      border-radius: 12px;
      border: 1px solid var(--border-color);
    }

    /* Custom Notification Modal */
    .custom-modal {
      display: none;
      position: fixed;
      inset: 0;
      z-index: 3000;
      background: rgba(0, 0, 0, 0.85);
      backdrop-filter: blur(8px);
      justify-content: center;
      align-items: center;
      padding: 20px;
    }

    .custom-modal.active {
      display: flex;
    }

    .custom-modal-card {
      background: #141414;
      border: 2px solid var(--primary-color);
      padding: 2.5rem;
      border-radius: 12px;
      max-width: 480px;
      width: 100%;
      text-align: center;
      box-shadow: 0 0 30px var(--primary-glow);
    }

    .custom-modal-card i {
      font-size: 3.5rem;
      color: var(--primary-color);
      margin-bottom: 1rem;
    }

    .custom-modal-card h3 {
      font-size: 1.6rem;
      margin-bottom: 0.8rem;
    }

    .custom-modal-card p {
      color: var(--text-muted);
      margin-bottom: 1.8rem;
      font-size: 0.98rem;
    }

    /* Footer */
    footer {
      background: #000000;
      color: var(--text-muted);
      padding: 3rem 2rem 2rem;
      border-top: 2px solid var(--border-color);
    }

    .footer-content {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 20px;
      padding-bottom: 2rem;
      border-bottom: 1px solid var(--border-color);
    }

    .footer-brand {
      display: flex;
      align-items: center;
      gap: 12px;
      font-size: 1.3rem;
      font-weight: 800;
      color: var(--primary-color);
    }

    .footer-brand img {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      object-fit: cover;
      border: 1px solid var(--primary-color);
    }

    .footer-bottom {
      text-align: center;
      margin-top: 1.5rem;
      font-size: 0.95rem;
    }

    /* Responsive Styles */
    @media (max-width: 868px) {
      .mobile-menu-btn { display: block; }

      nav {
        display: none;
        position: absolute;
        top: 100%;
        left: 0;
        width: 100%;
        background: rgba(10, 10, 10, 0.98);
        border-bottom: 2px solid var(--primary-color);
        padding: 1.5rem 0;
      }

      nav.active { display: block; }

      nav ul {
        flex-direction: column;
        gap: 18px;
      }

      .hero h1 { font-size: 2.5rem; }
      .hero p { font-size: 1.05rem; }
    }
  </style>
</head>
<body>

  <!-- Header & Navigation Bar -->
  <header>
    <a href="#home" class="logo">
      <img src="./logo%20pic%20.png" alt="Mulu Gym Logo" onerror="this.src='./logo pic .png'" />
      Mulu Gym / ሙሉ ጂም
    </a>
    
    <nav id="navbar">
      <ul>
        <li><a href="#home" data-en="Home" data-am="መነሻ">መነሻ</a></li>
        <li><a href="#about" data-en="About Us" data-am="ስለ እኛ">ስለ እኛ</a></li>
        <li><a href="#services" data-en="Services" data-am="አገልግሎቶች">አገልግሎቶች</a></li>
        <li><a href="#booking" data-en="Booking" data-am="ቦታ ማስያዣ">ቦታ ማስያዣ</a></li>
        <li><a href="#gallery" data-en="Gallery" data-am="የጂሙ ገጽታ">የጂሙ ገጽታ</a></li>
        <li><a href="#reviews" data-en="Reviews" data-am="አስተያየቶች">አስተያየቶች</a></li>
        <li><a href="#contact" data-en="Contact" data-am="አድራሻ">አድራሻ</a></li>
      </ul>
    </nav>

    <div class="header-controls">
      <button class="theme-btn" onclick="toggleTheme()" title="Switch Accent Color">White Accent</button>
      <button class="lang-btn" onclick="toggleLanguage()">English</button>
      <button class="mobile-menu-btn" onclick="toggleMobileMenu()" aria-label="Toggle Menu">
        <i class="fa-solid fa-bars"></i>
      </button>
    </div>
  </header>

  <!-- Hero Section -->
  <div class="hero" id="home">
    <div class="hero-subtitle-tag" data-en="Strength • Discipline • Respect • Legacy" data-am="ጥንካሬ • ሥርዓት • ክብር • ቅርሥ">
      Strength • Discipline • Respect • Legacy
    </div>
    <h1 data-en="MULU GYM" data-am="ሙሉ ጂም">MULU <span>GYM</span></h1>
    <p data-en="Transform your body and mind with our state-of-the-art equipment and professional combat & fitness trainers." data-am="በዘመናዊ የስፖርት መሣሪያዎቻችን እና በባለሙያ አሰልጣኞቻችን ጤናዎን፣ ሰውነትዎን እና የአእምሮ ብቃትዎን ይገንቡ።">
      በዘመናዊ የስፖርት መሣሪያዎቻችን እና በባለሙያ አሰልጣኞቻችን ጤናዎን፣ ሰውነትዎን እና የአእምሮ ብቃትዎን ይገንቡ።
    </p>
    <div class="hero-btn-group">
      <a href="#booking" class="btn" data-en="Book Your Spot" data-am="ቦታ ይያዙ">
        <i class="fa-solid fa-calendar-check"></i> ቦታ ይያዙ
      </a>
      <a href="#gallery" class="btn btn-secondary" data-en="View Gallery" data-am="የጂሙን ገጽታ ይመልከቱ">
        <i class="fa-solid fa-images"></i> የጂሙን ገጽታ ይመልከቱ
      </a>
    </div>
  </div>

  <!-- About Us Section -->
  <section id="about">
    <h2 class="section-title" data-en="About Us" data-am="ስለ እኛ">ስለ እኛ</h2>
    <div class="about-content">
      <p data-en="1. Mulu Gym is a modern fitness center established in Addis Ababa, dedicated to promoting health and physical excellence. Our core mission is empowering every member to reach peak physical strength and personal well-being." data-am="1. ሙሉ ጂም በአዲስ አበባ ከተማ ውስጥ ለጤና እና ለአካል ብቃት ትልቅ ትኩረት በመስጠት የተቋቋመ ዘመናዊ የስፖርት ማዕከል ነው። ዓላማችን እያንዳንዱ አባል ጤናማ፣ ጠንካራ እና የተሟላ የአካልና የአእምሮ ብቃት እንዲኖረው ማስቻል ነው።">1. ሙሉ ጂም በአዲስ አበባ ከተማ ውስጥ ለጤና እና ለአካል ብቃት ትልቅ ትኩረት በመስጠት የተቋቋመ ዘመናዊ የስፖርት ማዕከል ነው። ዓላማችን እያንዳንዱ አባል ጤናማ፣ ጠንካራ እና የተሟላ የአካልና የአእምሮ ብቃት እንዲኖረው ማስቻል ነው።</p>

      <p data-en="2. Our facility is equipped with top-tier fitness gear, structured into spacious workout environments designed for safety, comfort, and versatile training routines." data-am="2. ማዕከላችን በዘመናዊ የጂም መሳሪያዎች የተደራጀ ሲሆን፣ ለተለያዩ የስፖርት አይነቶች የተመቹ ሰፊ ክፍሎች አሉት። እያንዳንዱ ክፍል አባላት በነፃነት እና በደህንነት ስፖርታቸውን እንዲሰሩ ተደርጎ የተዘጋጀ ነው።">2. ማዕከላችን በዘመናዊ የጂም መሳሪያዎች የተደራጀ ሲሆን፣ ለተለያዩ የስፖርት አይነቶች የተመቹ ሰፊ ክፍሎች አሉት። እያንዳንዱ ክፍል አባላት በነፃነት እና በደህንነት ስፖርታቸውን እንዲሰሩ ተደርጎ የተዘጋጀ ነው።</p>

      <p data-en="3. Our trainers are certified, highly experienced martial artists and fitness professionals who craft tailored training regimens suitable for every individual's goals." data-am="3. በሙሉ ጂም ውስጥ የሚያሰለጥኑት አሰልጣኞች በሙያው የካበተ ልምድ ያላቸው እና የሰለጠኑ ባለሙያዎች ናቸው። ለእያንዳንዱ አባል እንደ ፍላጎቱ እና እንደ አካል ብቃት ደረጃው ተስማሚ የሆነ የስልጠና ፕሮግራም ያዘጋጃሉ።">3. በሙሉ ጂም ውስጥ የሚያሰለጥኑት አሰልጣኞች በሙያው የካበተ ልምድ ያላቸው እና የሰለጠኑ ባለሙያዎች ናቸው። ለእያንዳንዱ አባል እንደ ፍላጎቱ እና እንደ አካል ብቃት ደረጃው ተስማሚ የሆነ የስልጠና ፕሮግራም ያዘጋጃሉ።</p>

      <p data-en="4. Consistent physical workout enhances cardiovascular health, boosts immune systems, and reduces mental stress. Our programs are designed to deliver these long-lasting results." data-am="4. መደበኛ የአካል ብቃት እንቅስቃሴ ማድረግ የልብ ጤናን ያሻሽላል፣ የሰውነትን የበሽታ መከላከል አቅም ይጨምራል እንዲሁም የአእምሮ ውጥረትን ይቀንሳል። በማዕከላችን የሚሰጡት አገልግሎቶች ለነዚህ ሁሉ አዎንታዊ ውጤቶች የተቃኙ ናቸው።">4. መደበኛ የአካል ብቃት እንቅስቃሴ ማድረግ የልብ ጤናን ያሻሽላል፣ የሰውነትን የበሽታ መከላከል አቅም ይጨምራል እንዲሁም የአእምሮ ውጥረትን ይቀንሳል። በማዕከላችን የሚሰጡት አገልግሎቶች ለነዚህ ሁሉ አዎንታዊ ውጤቶች የተቃኙ ናቸው።</p>

      <p data-en="5. In addition to strength training, we offer combat sports such as Boxing, Muay Thai, and Taekwondo to build agility and self-defense skills, along with high-energy Aerobics." data-am="5. ከክብደት ማነሳት በተጨማሪ በቦክሲንግ፣ ሙአይ ታይ እና ታይክዋንዶ የስፖርት አይነቶች የሰውነትን ቅልጥፍና እና እራስን የመከላከል አቅም ማዳበር ይቻላል። ኤሮቢክስ ደግሞ የሰውነት ስብን ለመቀነስ እና የልብ ምት ፍጥነትን ለማስተካከል እጅግ ተራዳኢ ነው።">5. ከክብደት ማነሳት በተጨማሪ በቦክሲንግ፣ ሙአይ ታይ እና ታይክዋንዶ የስፖርት አይነቶች የሰውነትን ቅልጥፍና እና እራስን የመከላከል አቅም ማዳበር ይቻላል። ኤሮቢክስ ደግሞ የሰውነት ስብን ለመቀነስ እና የልብ ምት ፍጥነትን ለማስተካከል እጅግ ተራዳኢ ነው።</p>

      <p data-en="6. For post-workout recovery, members can access clean steam rooms and hot showers engineered to relax muscles and detoxify the body efficiently." data-am="6. ከጠንካራ ስልጠና በኋላ ሰውነትን ለማሳረፍ እና ጡንቻዎችን ለማዝናናት የሚያገለግሉ ዘመናዊ የስቲም (Steam) እና የሞቀ ሻወር (Shower) አገልግሎቶች በማዕከላችን ተዘጋጅተዋል።">6. ከጠንካራ ስልጠና በኋላ ሰውነትን ለማሳረፍ እና ጡንቻዎችን ለማዝናናት የሚያገለግሉ ዘመናዊ የስቲም (Steam) እና የሞቀ ሻወር (Shower) አገልግሎቶች በማዕከላችን ተዘጋጅተዋል።</p>

      <p data-en="7. Mulu Gym fosters a supportive, highly motivating community where individuals inspire each other, build strong connections, and celebrate fitness milestones." data-am="7. ሙሉ ጂም የስፖርት ቦታ ብቻ ሳይሆን አባላት እርስ በእርስ የሚደጋገፉበት፣ የሚነሳሱበት እና አዳዲስ ወዳጀነቶችን የሚመሰርቱበት አዎንታዊ የማህበረሰብ መንፈስ ያለው ቦታ ነው።">7. ሙሉ ጂም የስፖርት ቦታ ብቻ ሳይሆን አባላት እርስ በእርስ የሚደጋገፉበት፣ የሚነሳሱበት እና አዳዲስ ወዳጀነቶችን የሚመሰርቱበት አዎንታዊ የማህበረሰብ መንፈስ ያለው ቦታ ነው።</p>

      <p data-en="8. Mulu Gym is right by your side throughout your transformation journey. Join us today and kickstart your healthy lifestyle with us!" data-am="8. ጤናዎን ለመጠበቅ እና የተሻለ የሰውነት ቋም ለመገንባት በሚያደርጉት ጉዞ ሙሉ ጂም ከጎንዎ ነው። ዛሬውኑ ይቀላቀሉን እና የህይወት ለውጥዎን ከእኛ ጋር ይጀምሩ!">8. ጤናዎን ለመጠበቅ እና የተሻለ የሰውነት ቋም ለመገንባት በሚያደርጉት ጉዞ ሙሉ ጂም ከጎንዎ ነው። ዛሬውኑ ይቀላቀሉን እና የህይወት ለውጥዎን ከእኛ ጋር ይጀምሩ!</p>
    </div>
  </section>

  <!-- Services Section -->
  <section id="services">
    <h2 class="section-title" data-en="Our Services" data-am="አገልግሎቶቻችን">አገልግሎቶቻችን</h2>
    <div class="services-grid">
      <div class="service-card">
        <i class="fa-solid fa-hand-rock"></i>
        <h3 data-en="Boxing 🥊" data-am="ቦክሲንግ 🥊">ቦክሲንግ 🥊</h3>
        <p data-en="Professional boxing techniques, stamina building, and self-defense training." data-am="የቦክስ ስልጠና፣ የጽናት ማዳበሪያ እና ራስን የመከላከል ብቃት ማሳደጊያ።">የቦክስ ስልጠና፣ የጽናት ማዳበሪያ እና ራስን የመከላከል ብቃት ማሳደጊያ።</p>
      </div>

      <div class="service-card">
        <i class="fa-solid fa-person-fighting"></i>
        <h3 data-en="Muay Thai 🥋" data-am="ሙአይ ታይ 🥋">ሙአይ ታይ 🥋</h3>
        <p data-en="Traditional Thai combat sports training for total body strength and agility." data-am="የታይላንድ ባህላዊ የውጊያ ስፖርት ለጠንካራ የሰውነት ቅልጥፍና እና ጥንካሬ።">የታይላንድ ባህላዊ የውጊያ ስፖርት ለጠንካራ የሰውነት ቅልጥፍና እና ጥንካሬ።</p>
      </div>

      <div class="service-card">
        <i class="fa-solid fa-person-running"></i>
        <h3 data-en="Aerobics 🏃" data-am="ኤሮቢክስ 🏃">ኤሮቢክስ 🏃</h3>
        <p data-en="High-energy group workouts to burn fat and boost cardiovascular health." data-am="ስብን ለመቀነስ እና የልብ ጤናን ለማሻሻል የሚረዱ የቡድን ኤሮቢክስ እንቅስቃሴዎች።">ስብን ለመቀነስ እና የልብ ጤናን ለማሻሻል የሚረዱ የቡድን ኤሮቢክስ እንቅስቃሴዎች።</p>
      </div>

      <div class="service-card">
        <i class="fa-solid fa-dumbbell"></i>
        <h3 data-en="Personal Training 🏋️" data-am="የግል አሰልጣኝ 🏋️">የግል አሰልጣኝ 🏋️</h3>
        <p data-en="Customized one-on-one fitness and nutrition coaching." data-am="ለእርስዎ ብቻ ተስማሚ የሆነ የቅርብ የሙያ አሰልጠና እና የምግብ አመጋገብ ክትትል ።">ለእርስዎ ብቻ ተስማሚ የሆነ የቅርብ የሙያ አሰልጠና እና የምግብ አመጋገብ ክትትል ።</p>
      </div>

      <div class="service-card">
        <i class="fa-solid fa-hot-tub-person"></i>
        <h3 data-en="Steam 🔥" data-am="ስቲም 🔥">ስቲም 🔥</h3>
        <p data-en="Relaxing steam bath to detoxify and unwind after heavy workouts." data-am="ከጠንካራ ስፖርት በኋላ ጡንቻዎችን ለማዝናናት የሚያገለግል ዘመናዊ የስቲም ገላ።">ከጠንካራ ስፖርት በኋላ ጡንቻዎችን ለማዝናናት የሚያገለግል ዘመናዊ የስቲም ገላ።</p>
      </div>

      <div class="service-card">
        <i class="fa-solid fa-shower"></i>
        <h3 data-en="Shower 🚿" data-am="ሻወር 🚿">ሻወር 🚿</h3>
        <p data-en="Clean and refreshing hot & cold shower facilities." data-am="ጽዳቱን የጠበቀ የሞቅ እና ቀዝቃዛ ሻወር አገልግሎት።">ጽዳቱን የጠበቀ የሞቅ እና ቀዝቃዛ ሻወር አገልግሎት።</p>
      </div>

      <div class="service-card">
        <i class="fa-solid fa-user-ninja"></i>
        <h3 data-en="Taekwondo 🥋" data-am="ታይክዋንዶ 🥋">ታይክዋንዶ 🥋</h3>
        <p data-en="Martial arts discipline focusing on kicks, flexibility, and focus." data-am="የእግር ምት፣ የመታጠፍ ብቃት እና ትኩረትን የሚያሳድግ የኮሪያ የውጊያ ስፖርት።">የእግር ምት፣ የመታጠፍ ብቃት እና ትኩረትን የሚያሳድግ የኮሪያ የውጊያ ስፖርት።</p>
      </div>
    </div>
  </section>

  <!-- Booking System Section -->
  <section id="booking">
    <h2 class="section-title" data-en="Book Your Spot" data-am="ቦታ ያስይዙ">ቦታ ያስይዙ</h2>
    <div class="booking-container">
      <form class="booking-form" id="bookingForm" onsubmit="handleBooking(event)">
        <div class="form-group">
          <label data-en="Full Name" data-am="ሙሉ ስም">ሙሉ ስም</label>
          <input type="text" id="bookName" placeholder="ስምዎን ያስገቡ" required />
        </div>
        <div class="form-group">
          <label data-en="Phone Number" data-am="ስልክ ቁጥር">ስልክ ቁጥር</label>
          <input type="tel" id="bookPhone" placeholder="+251 9xxxxxxxx" required />
        </div>
        <div class="form-group">
          <label data-en="Select Service" data-am="አገልግሎት ይምረጡ">አገልግሎት ይምረጡ</label>
          <select id="bookService" required>
            <option value="Boxing / ቦክሲንግ">Boxing (ቦክሲንግ)</option>
            <option value="Muay Thai / ሙአይ ታይ">Muay Thai (ሙአይ ታይ)</option>
            <option value="Aerobics / ኤሮቢክስ">Aerobics (ኤሮቢክስ)</option>
            <option value="Personal Training / የግል አሰልጣኝ">Personal Training (የግል አሰልጣኝ)</option>
            <option value="Steam / ስቲም">Steam (ስቲም)</option>
            <option value="Shower / ሻወር">Shower (ሻወር)</option>
            <option value="Taekwondo / ታይክዋንዶ">Taekwondo (ታይክዋንዶ)</option>
          </select>
        </div>
        <div class="form-group">
          <label data-en="Preferred Date" data-am="የሚጀምሩበት ቀን">የሚጀምሩበት ቀን</label>
          <input type="date" id="bookDate" required />
        </div>
        <div class="form-group">
          <label data-en="Preferred Time" data-am="የሚመችዎት ሰዓት">የሚመችዎት ሰዓት</label>
          <input type="time" id="bookTime" required />
        </div>
        <button type="submit" class="btn" data-en="Confirm Booking" data-am="ቦታ ያስይዙ">
          <i class="fa-solid fa-paper-plane"></i> ቦታ ያስይዙ
        </button>
      </form>
    </div>
  </section>

  <!-- Gym Gallery -->
  <section id="gallery">
    <h2 class="section-title" data-en="Gym Gallery" data-am="የጂሙ ገጽታ">የጂሙ ገጽታ</h2>
    <div class="gallery-grid">
      <div class="gallery-item" onclick="openLightbox(0)">
        <img src="./welcome%20pic%20.jpg" alt="Mulu Gym Main Entrance & Equipment" onerror="this.src='./welcome pic .jpg'" />
        <div class="gallery-overlay"><i class="fa-solid fa-magnifying-glass-plus"></i></div>
      </div>
      <div class="gallery-item" onclick="openLightbox(1)">
        <img src="./the%20gym%20place%20.jpg" alt="Mulu Gym Place & Fitness Area" onerror="this.src='./the gym place .jpg'" />
        <div class="gallery-overlay"><i class="fa-solid fa-magnifying-glass-plus"></i></div>
      </div>
      <div class="gallery-item" onclick="openLightbox(2)">
        <img src="./the%20gym%20house%20.jpg" alt="Mulu Gym House Facility View" onerror="this.src='./the gym house .jpg'" />
        <div class="gallery-overlay"><i class="fa-solid fa-magnifying-glass-plus"></i></div>
      </div>
      <div class="gallery-item" onclick="openLightbox(3)">
        <img src="./the%20gym%20house.jpg" alt="Mulu Gym House Training Hall" onerror="this.src='./the gym house.jpg'" />
        <div class="gallery-overlay"><i class="fa-solid fa-magnifying-glass-plus"></i></div>
      </div>
      <div class="gallery-item" onclick="openLightbox(4)">
        <img src="./for%20horizontal%20pic%20.jpg" alt="Mulu Gym Workout View" onerror="this.src='./for horizontal pic .jpg'" />
        <div class="gallery-overlay"><i class="fa-solid fa-magnifying-glass-plus"></i></div>
      </div>
    </div>
  </section>

  <!-- Lightbox Modal -->
  <div class="lightbox-modal" id="lightboxModal" onclick="closeLightboxOnBg(event)">
    <span class="lightbox-close" onclick="closeLightbox()">&times;</span>
    <span class="lightbox-nav lightbox-prev" onclick="changeLightboxImg(-1)">&#10094;</span>
    <img class="lightbox-content" id="lightboxImage" src="" alt="Gallery Large View" />
    <div class="lightbox-caption" id="lightboxCaption"></div>
    <span class="lightbox-nav lightbox-next" onclick="changeLightboxImg(1)">&#10095;</span>
  </div>

  <!-- Customer Reviews Section -->
  <section id="reviews">
    <h2 class="section-title" data-en="Customer Reviews" data-am="የደንበኞች አስተያየት">የደንበኞች አስተያየት</h2>
    <div class="reviews-container">
      <div class="avg-rating-box">
        <div class="avg-rating-score" id="score">4.9</div>
        <div class="stars-display" id="avgStarsDisplay">★★★★★</div>
        <p style="color:var(--text-muted); margin-top: 5px;" id="reviewCountText">Based on 0 Reviews</p>
      </div>

      <!-- Review Form -->
      <form class="review-form" id="reviewForm" onsubmit="handleReviewSubmit(event)">
        <input type="text" id="reviewerName" placeholder="ስምዎን ያስገቡ / Enter Your Name" required />
        
        <div style="text-align:center;">
          <label style="font-weight:600;" data-en="Select Rating" data-am="ደረጃ ይስጡ">ደረጃ ይስጡ</label>
          <div class="interactive-stars" id="starSelector">
            <span class="star-btn" data-value="1">★</span>
            <span class="star-btn" data-value="2">★</span>
            <span class="star-btn" data-value="3">★</span>
            <span class="star-btn" data-value="4">★</span>
            <span class="star-btn active" data-value="5">★</span>
          </div>
        </div>

        <textarea id="reviewerComment" rows="3" placeholder="አስተያየትዎን እዚህ ይጻፉ... / Write your comment..." required></textarea>
        <button type="submit" class="btn" data-en="Submit Review" data-am="አስተያየት ላክ">
          <i class="fa-solid fa-comment-dots"></i> አስተያየት ላክ
        </button>
      </form>

      <!-- Reviews Display List -->
      <div class="reviews-list" id="reviewsList"></div>
    </div>
  </section>

  <!-- Contact Section -->
  <section id="contact">
    <h2 class="section-title" data-en="Contact Us" data-am="አድራሻችን">አድራሻችን</h2>
    <div class="contact-container">
      <div class="contact-info">
        <div class="contact-item">
          <i class="fa-solid fa-location-dot"></i>
          <div>
            <strong>አድራሻ (Location):</strong><br />
            Ansar Hirna, Qobo Retailor
          </div>
        </div>
        <div class="contact-item">
          <i class="fa-solid fa-phone"></i>
          <div>
            <strong>ስልክ (Phone):</strong><br />
            +251 96 757 4757
          </div>
        </div>
        <div class="contact-item">
          <i class="fa-brands fa-telegram"></i>
          <div>
            <strong>ቴሌግራም (Telegram):</strong><br />
            @Abniwaa
          </div>
        </div>

        <a href="https://t.me/Abniwaa" target="_blank" class="telegram-btn">
          <i class="fa-brands fa-telegram"></i> Telegram ላይ ያግኙን
        </a>

        <a href="https://www.google.com/maps/search/?api=1&query=Ansar+Hirna+Qobo+Retailor" target="_blank" class="directions-btn">
          <i class="fa-solid fa-route"></i> Get Directions (አቅጣጫዎች)
        </a>
      </div>

      <div class="map-container">
        <iframe 
          src="https://maps.google.com/maps?q=Ansar%20Hirna%20Qobo%20Retailor&t=&z=13&ie=UTF8&iwloc=&output=embed" 
          allowfullscreen="" 
          loading="lazy">
        </iframe>
      </div>
    </div>
  </section>

  <!-- Custom Success Notification Modal -->
  <div class="custom-modal" id="successModal">
    <div class="custom-modal-card">
      <i class="fa-solid fa-circle-check"></i>
      <h3 id="modalTitle">ተሳክቷል! / Success!</h3>
      <p id="modalBody">ጥያቄዎ በጥሩ ሁኔታ ተልኳል። እናመሰግናለን!</p>
      <button class="btn" onclick="closeSuccessModal()">እሺ / OK</button>
    </div>
  </div>

  <!-- Footer -->
  <footer>
    <div class="footer-content">
      <div class="footer-brand">
        <img src="./logo%20pic%20.png" alt="Mulu Gym Logo" onerror="this.src='./logo pic .png'" />
        <span>Mulu Gym / ሙሉ ጂም</span>
      </div>
      <div>
        <a href="https://t.me/Abniwaa" target="_blank" style="color:var(--primary-color); text-decoration:none; font-weight:600;">
          <i class="fa-brands fa-telegram"></i> @Abniwaa on Telegram
        </a>
      </div>
    </div>
    <div class="footer-bottom">
      <p>&copy; 2026 Mulu Gym. All Rights Reserved.</p>
    </div>
  </footer>

  <!-- Scripts -->
  <script>
    // Mobile Navigation Toggle
    function toggleMobileMenu() {
      document.getElementById('navbar').classList.toggle('active');
    }
    document.querySelectorAll('nav a').forEach(link => {
      link.addEventListener('click', () => document.getElementById('navbar').classList.remove('active'));
    });

    // Theme Switcher
    function toggleTheme() {
      document.body.classList.toggle('white-accent-mode');
      const btn = document.querySelector('.theme-btn');
      btn.innerText = document.body.classList.contains('white-accent-mode') ? "Yellow Accent" : "White Accent";
    }

    // Language Switcher
    let currentLang = 'am';
    function toggleLanguage() {
      currentLang = currentLang === 'am' ? 'en' : 'am';
      document.querySelector('.lang-btn').innerText = currentLang === 'am' ? 'English' : 'አማርኛ';
      document.querySelectorAll('[data-en]').forEach(el => {
        el.innerText = el.getAttribute(`data-${currentLang}`);
      });
    }

    // Custom Modal Display
    function showNotification(title, message) {
      document.getElementById('modalTitle').innerText = title;
      document.getElementById('modalBody').innerText = message;
      document.getElementById('successModal').classList.add('active');
    }
    function closeSuccessModal() {
      document.getElementById('successModal').classList.remove('active');
    }

    // Booking Submission Handler (via Secure Backend Endpoint)
    async function handleBooking(e) {
      e.preventDefault();
      const name = document.getElementById('bookName').value.trim();
      const phone = document.getElementById('bookPhone').value.trim();
      const service = document.getElementById('bookService').value;
      const date = document.getElementById('bookDate').value;
      const time = document.getElementById('bookTime').value;

      if (!name || !phone || !service || !date || !time) {
        showNotification("ስህተት / Error", "እባክዎን ሁሉንም ቦታዎች በትክክል ይሙሉ!");
        return;
      }

      const payload = { name, phone, service, date, time };

      try {
        const res = await fetch('/api/booking', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(payload)
        });

        if (res.ok) {
          showNotification("ተሳክቷል! / Success", "የቦታ ማስያዝ ጥያቄዎ በተሳካ ሁኔታ ለሙሉ ጂም ተልኳል!");
        } else {
          showNotification("ማስታወቂያ", "ጥያቄዎ ተመዝግቧል። እባክዎን በቴሌግራምም ያረጋግጡልን።");
        }
      } catch (err) {
        // Fallback notification
        showNotification("ተመዝግቧል / Recorded", "የቡኪንግ መረጃዎ ተዘጋጅቷል! በቴሌግራም መልእክት ለመላክ @Abniwaa ን ያነጋግሩ።");
      }

      document.getElementById('bookingForm').reset();
    }

    // Lightbox Functionality
    const galleryImages = [
      { src: './welcome%20pic%20.jpg', alt: 'Mulu Gym Main Entrance & Equipment' },
      { src: './the%20gym%20place%20.jpg', alt: 'Mulu Gym Place & Fitness Area' },
      { src: './the%20gym%20house%20.jpg', alt: 'Mulu Gym House Facility View' },
      { src: './the%20gym%20house.jpg', alt: 'Mulu Gym House Training Hall' },
      { src: './for%20horizontal%20pic%20.jpg', alt: 'Mulu Gym Workout View' }
    ];
    let currentImgIndex = 0;

    function openLightbox(index) {
      currentImgIndex = index;
      document.getElementById('lightboxImage').src = galleryImages[currentImgIndex].src;
      document.getElementById('lightboxCaption').innerText = galleryImages[currentImgIndex].alt;
      document.getElementById('lightboxModal').classList.add('active');
    }
    function closeLightbox() {
      document.getElementById('lightboxModal').classList.remove('active');
    }
    function closeLightboxOnBg(e) {
      if (e.target.id === 'lightboxModal') closeLightbox();
    }
    function changeLightboxImg(step) {
      currentImgIndex = (currentImgIndex + step + galleryImages.length) % galleryImages.length;
      document.getElementById('lightboxImage').src = galleryImages[currentImgIndex].src;
      document.getElementById('lightboxCaption').innerText = galleryImages[currentImgIndex].alt;
    }
    document.addEventListener('keydown', (e) => {
      const modal = document.getElementById('lightboxModal');
      if (modal.classList.contains('active')) {
        if (e.key === 'Escape') closeLightbox();
        if (e.key === 'ArrowLeft') changeLightboxImg(-1);
        if (e.key === 'ArrowRight') changeLightboxImg(1);
      }
    });

    // Star Selector Logic
    let selectedRating = 5;
    const starBtns = document.querySelectorAll('#starSelector .star-btn');
    starBtns.forEach(btn => {
      btn.addEventListener('click', function() {
        selectedRating = parseInt(this.getAttribute('data-value'));
        starBtns.forEach(s => {
          const val = parseInt(s.getAttribute('data-value'));
          if (val <= selectedRating) {
            s.classList.add('active');
          } else {
            s.classList.remove('active');
          }
        });
      });
    });

    // Firebase & LocalStorage Reviews Logic
    let localReviews = JSON.parse(localStorage.getItem('mulu_gym_reviews')) || [];

    function renderReviews() {
      const reviewsList = document.getElementById('reviewsList');
      reviewsList.innerHTML = '';
      let totalScore = 0;

      localReviews.forEach(r => {
        totalScore += Number(r.rating);
        const card = document.createElement('div');
        card.className = 'review-item';
        card.innerHTML = `
          <div class="review-header">
            <span>${r.name}</span>
            <span class="stars-display">${'★'.repeat(r.rating)}${'☆'.repeat(5 - r.rating)}</span>
          </div>
          <p>${r.comment}</p>
          <small style="color:var(--text-muted); font-size:0.8rem;">${r.date || ''}</small>
        `;
        reviewsList.appendChild(card);
      });

      const count = localReviews.length;
      document.getElementById('reviewCountText').innerText = `Based on ${count} Reviews`;
      if (count > 0) {
        document.getElementById('score').innerText = (totalScore / count).toFixed(1);
      } else {
        document.getElementById('score').innerText = "5.0";
      }
    }

    renderReviews();

    async function handleReviewSubmit(e) {
      e.preventDefault();
      const name = document.getElementById('reviewerName').value.trim();
      const comment = document.getElementById('reviewerComment').value.trim();

      if (!name || !comment) return;

      const newReview = {
        name,
        rating: selectedRating,
        comment,
        date: new Date().toLocaleDateString('am-ET')
      };

      // Save locally
      localReviews.unshift(newReview);
      localStorage.setItem('mulu_gym_reviews', JSON.stringify(localReviews));
      renderReviews();

      // Submit to backend secure Telegram API
      try {
        await fetch('/api/review', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(newReview)
        });
      } catch (err) {
        console.log("Backend notification sent or pending.");
      }

      showNotification("እናመሰግናለን! / Thank You", "ስ```html
<!DOCTYPE html>
<html lang
