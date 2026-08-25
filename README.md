<html lang="am">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mulu Gym - ሙሉ ጂም እና ፊቱነስ ማዕከል</title>
  
  <!-- Font Awesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" />
  
  <!-- Firebase SDKs -->
  <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore-compat.js"></script>

  <style>
    /* Yellow and Black Theme Setup */
    :root {
      --primary-color: #ffcc00; /* Vibrant Yellow */
      --secondary-color: #0a0a0a; /* Pitch Black */
      --card-bg: #141414; /* Dark Gray Card */
      --text-main: #ffffff;
      --text-muted: #b3b3b3;
      --border-color: #262626;
      --btn-text: #000000;
    }

    /* Alternative White Button/Accent Mode */
    .white-accent-mode {
      --primary-color: #ffffff;
      --btn-text: #000000;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Arial, sans-serif;
      scroll-behavior: smooth;
    }

    body {
      background-color: var(--secondary-color);
      color: var(--text-main);
      line-height: 1.7;
    }

    /* Header & Navigation */
    header {
      background: rgba(10, 10, 10, 0.95);
      padding: 1rem 2rem;
      position: sticky;
      top: 0;
      z-index: 1000;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 2px solid var(--primary-color);
      backdrop-filter: blur(5px);
    }

    .logo {
      font-size: 1.8rem;
      font-weight: 800;
      color: var(--primary-color);
      display: flex;
      align-items: center;
      gap: 12px;
      text-transform: uppercase;
    }

    .logo img {
      width: 45px;
      height: 45px;
      border-radius: 50%;
      object-fit: cover;
      border: 2px solid var(--primary-color);
    }

    nav ul {
      display: flex;
      list-style: none;
      gap: 20px;
    }

    nav a {
      color: var(--text-main);
      text-decoration: none;
      font-weight: 600;
      transition: color 0.3s;
    }

    nav a:hover {
      color: var(--primary-color);
    }

    .header-btns {
      display: flex;
      gap: 10px;
    }

    .theme-btn, .lang-btn {
      background: var(--primary-color);
      color: var(--btn-text);
      border: none;
      padding: 8px 16px;
      border-radius: 4px;
      cursor: pointer;
      font-weight: bold;
      transition: 0.3s;
    }

    .theme-btn:hover, .lang-btn:hover {
      opacity: 0.85;
    }

    /* Hero Section */
    .hero {
      background: linear-gradient(rgba(0,0,0,0.85), rgba(0,0,0,0.85)), url('gym place.png') center/cover no-repeat;
      height: 85vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 0 20px;
    }

    .hero h1 {
      font-size: 3.5rem;
      color: var(--primary-color);
      margin-bottom: 1rem;
      text-transform: uppercase;
      letter-spacing: 2px;
    }

    .hero p {
      font-size: 1.25rem;
      margin-bottom: 2rem;
      max-width: 700px;
      color: var(--text-muted);
    }

    .btn {
      background: var(--primary-color);
      color: var(--btn-text);
      padding: 14px 32px;
      text-decoration: none;
      border-radius: 4px;
      font-size: 1.1rem;
      font-weight: bold;
      transition: 0.3s;
      border: none;
      cursor: pointer;
      display: inline-block;
    }

    .btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(255, 204, 0, 0.3);
    }

    /* General Section Styling */
    section {
      padding: 5rem 2rem;
      max-width: 1200px;
      margin: 0 auto;
    }

    .section-title {
      text-align: center;
      font-size: 2.5rem;
      margin-bottom: 2.5rem;
      color: var(--primary-color);
      text-transform: uppercase;
      position: relative;
    }

    .section-title::after {
      content: '';
      width: 70px;
      height: 4px;
      background: var(--primary-color);
      display: block;
      margin: 10px auto 0;
    }

    /* About Us - 8 Paragraphs Layout */
    .about-content {
      background: var(--card-bg);
      padding: 2.5rem;
      border-radius: 8px;
      border: 1px solid var(--border-color);
      display: flex;
      flex-direction: column;
      gap: 1.5rem;
    }

    .about-content p {
      color: var(--text-muted);
      font-size: 1.05rem;
      text-align: justify;
      border-left: 3px solid var(--primary-color);
      padding-left: 15px;
    }

    /* Services Grid (No Photos - Icons Only) */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 25px;
    }

    .service-card {
      background: var(--card-bg);
      padding: 2.5rem 1.5rem;
      border-radius: 8px;
      text-align: center;
      border: 1px solid var(--border-color);
      transition: 0.3s;
    }

    .service-card:hover {
      border-color: var(--primary-color);
      transform: translateY(-5px);
    }

    .service-card i {
      font-size: 3rem;
      color: var(--primary-color);
      margin-bottom: 1.2rem;
    }

    .service-card h3 {
      font-size: 1.4rem;
      margin-bottom: 0.8rem;
      color: var(--text-main);
    }

    .service-card p {
      color: var(--text-muted);
      font-size: 0.95rem;
    }

    /* Booking System */
    .booking-container {
      background: var(--card-bg);
      padding: 2.5rem;
      border-radius: 8px;
      border: 1px solid var(--border-color);
      max-width: 700px;
      margin: 0 auto;
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
    }

    .booking-form input, .booking-form select, .booking-form textarea {
      padding: 14px;
      background: #000;
      border: 1px solid var(--border-color);
      border-radius: 4px;
      font-size: 1rem;
      color: var(--text-main);
    }

    .booking-form input:focus, .booking-form select:focus {
      outline: none;
      border-color: var(--primary-color);
    }

    /* Gallery Grid */
    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 20px;
    }

    .gallery-grid img {
      width: 100%;
      height: 250px;
      object-fit: cover;
      border-radius: 8px;
      border: 1px solid var(--border-color);
      transition: transform 0.3s;
    }

    .gallery-grid img:hover {
      transform: scale(1.03);
      border-color: var(--primary-color);
    }

    /* Reviews Section */
    .reviews-container {
      background: var(--card-bg);
      padding: 2.5rem;
      border-radius: 8px;
      border: 1px solid var(--border-color);
    }

    .avg-rating {
      text-align: center;
      font-size: 1.6rem;
      margin-bottom: 2rem;
      font-weight: bold;
    }

    .stars {
      color: var(--primary-color);
    }

    .review-form {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin-bottom: 2.5rem;
    }

    .review-form input, .review-form textarea, .review-form select {
      padding: 12px;
      background: #000;
      border: 1px solid var(--border-color);
      border-radius: 4px;
      font-size: 1rem;
      color: var(--text-main);
    }

    .reviews-list {
      display: flex;
      flex-direction: column;
      gap: 20px;
    }

    .review-item {
      border-bottom: 1px solid var(--border-color);
      padding-bottom: 15px;
    }

    .review-header {
      display: flex;
      justify-content: space-between;
      font-weight: bold;
      margin-bottom: 5px;
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
    }

    .contact-item {
      display: flex;
      align-items: center;
      gap: 15px;
      font-size: 1.1rem;
    }

    .contact-item i {
      font-size: 1.6rem;
      color: var(--primary-color);
    }

    .telegram-btn {
      background: #0088cc;
      color: #fff;
      padding: 14px 24px;
      border-radius: 4px;
      text-decoration: none;
      display: inline-flex;
      align-items: center;
      gap: 10px;
      font-weight: bold;
      width: fit-content;
      transition: 0.3s;
    }

    .telegram-btn:hover {
      background: #006699;
    }

    .map-container iframe {
      width: 100%;
      height: 300px;
      border: 0;
      border-radius: 8px;
    }

    /* Footer */
    footer {
      background: #000;
      color: var(--text-muted);
      text-align: center;
      padding: 2rem;
      border-top: 1px solid var(--border-color);
    }

    @media (max-width: 768px) {
      header {
        flex-direction: column;
        gap: 15px;
      }
      .hero h1 {
        font-size: 2.3rem;
      }
      nav ul {
        flex-wrap: wrap;
        justify-content: center;
      }
    }
  </style>
</head>
<body>

  <!-- Header & Navigation -->
  <header>
    <div class="logo">
      <img src="logo pic .png" alt="Mulu Gym Logo" onerror="this.src='https://via.placeholder.com/45/ffcc00/000000?text=MG'" />
      Mulu Gym
    </div>
    <nav>
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
    <div class="header-btns">
      <button class="theme-btn" onclick="toggleTheme()" title="Switch Accent Color">White Accent</button>
      <button class="lang-btn" onclick="toggleLanguage()">English</button>
    </div>
  </header>

  <!-- Hero Section -->
  <div class="hero" id="home">
    <h1 data-en="Welcome to Mulu Gym" data-am="እንኳን ወደ ሙሉ ጂም በደህና መጡ">እንኳን ወደ ሙሉ ጂም በደህና መጡ</h1>
    <p data-en="Transform your body and mind with our state-of-the-art equipment and professional combat & fitness trainers." data-am="በዘመናዊ የስፖርት መሣሪያዎቻችን እና በባለሙያ አሰልጣኞቻችን ጤናዎን፣ ሰውነትዎን እና የአእምሮ ብቃትዎን ይገንቡ።">በዘመናዊ የስፖርት መሣሪያዎቻችን እና በባለሙያ አሰልጣኞቻችን ጤናዎን፣ ሰውነትዎን እና የአእምሮ ብቃትዎን ይገንቡ።</p>
    <a href="#booking" class="btn" data-en="Book Now" data-am="አሁኑኑ ቦታ ይያዙ">አሁኑኑ ቦታ ይያዙ</a>
  </div>

  <!-- About Us Section - 8 Paragraphs -->
  <section id="about">
    <h2 class="section-title" data-en="About Us" data-am="ስለ እኛ">ስለ እኛ</h2>
    <div class="about-content">
      <p>1. ሙሉ ጂም በአዲስ አበባ ከተማ ውስጥ ለጤና እና ለአካል ብቃት ትልቅ ትኩረት በመስጠት የተቋቋመ ዘመናዊ የስፖርት ማዕከል ነው። ዓላማችን እያንዳንዱ አባል ጤናማ፣ ጠንካራ እና የተሟላ የአካልና የአእምሮ ብቃት እንዲኖረው ማስቻል ነው።</p>
      <p>2. ማዕከላችን በዘመናዊ የጂም መሳሪያዎች የተደራጀ ሲሆን፣ ለተለያዩ የስፖርት አይነቶች የተመቹ ሰፊ ክፍሎች አሉት። እያንዳንዱ ክፍል አባላት በነፃነት እና በደህንነት ስፖርታቸውን እንዲሰሩ ተደርጎ የተዘጋጀ ነው።</p>
      <p>3. በሙሉ ጂም ውስጥ የሚያሰለጥኑት አሰልጣኞች በሙያው የካበተ ልምድ ያላቸው እና የሰለጠኑ ባለሙያዎች ናቸው። ለእያንዳንዱ አባል እንደ ፍላጎቱ እና እንደ አካል ብቃት ደረጃው ተስማሚ የሆነ የስልጠና ፕሮግራም ያዘጋጃሉ።</p>
      <p>4. መደበኛ የአካል ብቃት እንቅስቃሴ ማድረግ የልብ ጤናን ያሻሽላል፣ የሰውነትን የበሽታ መከላከል አቅም ይጨምራል እንዲሁም የአእምሮ ውጥረትን ይቀንሳል። በማዕከላችን የሚሰጡት አገልግሎቶች ለነዚህ ሁሉ አዎንታዊ ውጤቶች የተቃኙ ናቸው።</p>
      <p>5. ከክብደት ማነሳት በተጨማሪ በቦክሲንግ፣ ሙአይ ታይ እና ታይክዋንዶ የስፖርት አይነቶች የሰውነትን ቅልጥፍና እና እራስን የመከላከል አቅም ማዳበር ይቻላል። ኤሮቢክስ ደግሞ የሰውነት ስብን ለመቀነስ እና የልብ ምት ፍጥነትን ለማስተካከል እጅግ ተራዳኢ ነው።</p>
      <p>6. ከጠንካራ ስልጠና በኋላ ሰውነትን ለማሳረፍ እና ጡንቻዎችን ለማዝናናት የሚያገለግሉ ዘመናዊ የስቲም (Steam) እና የሞቀ ሻወር (Shower) አገልግሎቶች በማዕከላችን ተዘጋጅተዋል።</p>
      <p>7. ሙሉ ጂም የስፖርት ቦታ ብቻ ሳይሆን አባላት እርስ በእርስ የሚደጋገፉበት፣ የሚነሳሱበት እና አዳዲስ ወዳጀነቶችን የሚመሰርቱበት አዎንታዊ የማህበረሰብ መንፈስ ያለው ቦታ ነው።</p>
      <p>8. ጤናዎን ለመጠበቅ እና የተሻለ የሰውነት ቋም ለመገንባት በሚያደርጉት ጉዞ ሙሉ ጂም ከጎንዎ ነው። ዛሬውኑ ይቀላቀሉን እና የህይወት ለውጥዎን ከእኛ ጋር ይጀምሩ!</p>
    </div>
  </section>

  <!-- Services Section (No Photos - Icons Only) -->
  <section id="services">
    <h2 class="section-title" data-en="Our Services" data-am="አገልግሎቶቻችን">አገልግሎቶቻችን</h2>
    <div class="services-grid">
      <div class="service-card">
        <i class="fa-solid fa-hand-rock"></i>
        <h3 data-en="Boxing" data-am="ቦክሲንግ">ቦክሲንግ</h3>
        <p data-en="Professional boxing techniques, stamina building, and self-defense training." data-am="የቦክስ ስልጠና፣ የጽናት ማዳበሪያ እና ራስን የመከላከል ብቃት ማሳደጊያ።">የቦክስ ስልጠና፣ የጽናት ማዳበሪያ እና ራስን የመከላከል ብቃት ማሳደጊያ።</p>
      </div>
      <div class="service-card">
        <i class="fa-solid fa-person-fighting"></i>
        <h3 data-en="Muay Thai" data-am="ሙአይ ታይ">ሙአይ ታይ</h3>
        <p data-en="Traditional Thai martial arts training for total body strength and agility." data-am="የታይላንድ ባህላዊ የውጊያ ስፖርት ለጠንካራ የሰውነት ቅልጥፍና እና ጥንካሬ።">የታይላንድ ባህላዊ የውጊያ ስፖርት ለጠንካራ የሰውነት ቅልጥፍና እና ጥንካሬ።</p>
      </div>
      <div class="service-card">
        <i class="fa-solid fa-person-running"></i>
        <h3 data-en="Aerobics" data-am="ኤሮቢክስ">ኤሮቢክስ</h3>
        <p data-en="High-energy group workouts to burn fat and boost cardiovascular health." data-am="ስብን ለመቀነስ እና የልብ ጤናን ለማሻሻል የሚረዱ የቡድን ኤሮቢክስ እንቅስቃሴዎች።">ስብን ለመቀነስ እና የልብ ጤናን ለማሻሻል የሚረዱ የቡድን ኤሮቢክስ እንቅስቃሴዎች።</p>
      </div>
      <div class="service-card">
        <i class="fa-solid fa-dumbbell"></i>
        <h3 data-en="Personal Training" data-am="የግል አሰልጣኝ">የግል አሰልጣኝ</h3>
        <p data-en="Customized one-on-one fitness and nutrition coaching." data-am="ለእርስዎ ብቻ ተስማሚ የሆነ የቅርብ የሙያ አሰልጠና እና የምግብ አመጋገብ ክትትል ።">ለእርስዎ ብቻ ተስማሚ የሆነ የቅርብ የሙያ አሰልጠና እና የምግብ አመጋገብ ክትትል ።</p>
      </div>
      <div class="service-card">
        <i class="fa-solid fa-hot-tub-person"></i>
        <h3 data-en="Steam" data-am="ስቲም">ስቲም</h3>
        <p data-en="Relaxing steam bath to detoxify and unwind after heavy workouts." data-am="ከጠንካራ ስፖርት በኋላ ጡንቻዎችን ለማዝናናት የሚያገለግል ዘመናዊ የስቲም ገላ።">ከጠንካራ ስፖርት በኋላ ጡንቻዎችን ለማዝናናት የሚያገለግል ዘመናዊ የስቲም ገላ።</p>
      </div>
      <div class="service-card">
        <i class="fa-solid fa-shower"></i>
        <h3 data-en="Shower" data-am="ሻወር">ሻወር</h3>
        <p data-en="Clean and refreshing hot & cold shower facilities." data-am="ጽዳቱን የጠበቀ የሞቅ እና ቀዝቃዛ ሻወር አገልግሎት።">ጽዳቱን የጠበቀ የሞቅ እና ቀዝቃዛ ሻወር አገልግሎት።</p>
      </div>
      <div class="service-card">
        <i class="fa-solid fa-user-ninja"></i>
        <h3 data-en="Taekwondo" data-am="ታይክዋንዶ">ታይክዋንዶ</h3>
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
          <input type="tel" id="bookPhone" placeholder="09xxxxxxxx" required />
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
        <button type="submit" class="btn" data-en="Confirm & Send via Telegram" data-am="ቦታ ያስይዙ (በቴሌግራም ይላኩ)">ቦታ ያስይዙ (በቴሌግራም ይላኩ)</button>
      </form>
    </div>
  </section>

  <!-- Gallery Section (All GitHub PNG Pictures except Logo) -->
  <section id="gallery">
    <h2 class="section-title" data-en="Gym Gallery" data-am="የጂሙ ገጽታ">የጂሙ ገጽታ</h2>
    <div class="gallery-grid">
      <img src="gym place.png" alt="Gym Main Area" onerror="this.src='https://images.unsplash.com/photo-1534438327276-14e5300c3a48?w=500'" />
      <img src="gym place 2.png" alt="Workout Zone" onerror="this.src='https://images.unsplash.com/photo-1517838277536-f5f99be501cd?w=500'" />
      <img src="gym_equipment.png" alt="Gym Equipment" onerror="this.src='https://images.unsplash.com/photo-1581009146145-b5ef050c2e1e?w=500'" />
      <img src="gym_workout.png" alt="Training Area" onerror="this.src='https://images.unsplash.com/photo-1571902943202-507ec2618e8f?w=500'" />
      <img src="gym_boxing.png" alt="Boxing Ring" onerror="this.src='https://images.unsplash.com/photo-1549719386-74dfcbf7dbed?w=500'" />
      <img src="gym_facility.png" alt="Facility Overview" onerror="this.src='https://images.unsplash.com/photo-1540497077202-7c8a3999166f?w=500'" />
    </div>
  </section>

  <!-- Customer Reviews -->
  <section id="reviews">
    <h2 class="section-title" data-en="Customer Reviews" data-am="የደንበኞች አስተያየት">የደንበኞች አስተያየት</h2>
    <div class="reviews-container">
      <div class="avg-rating" id="avgRating">
        <span data-en="Average Rating:" data-am="አማካይ ደረጃ፡">አማካይ ደረጃ፡</span> 
        <span id="score">0.0</span> <span class="stars">★</span>
      </div>

      <!-- Review Form -->
      <form class="review-form" id="reviewForm">
        <input type="text" id="reviewerName" placeholder="ስምዎን ያስገቡ" required />
        <select id="reviewerRating" required>
          <option value="5">5 Stars (እጅግ በጣም ጥሩ ★★★★★)</option>
          <option value="4">4 Stars (በጣም ጥሩ ★★★★)</option>
          <option value="3">3 Stars (ጥሩ ★★★)</option>
          <option value="2">2 Stars (መካከለኛ ★★)</option>
          <option value="1">1 Star (ዝቅተኛ ★)</option>
        </select>
        <textarea id="reviewerComment" rows="3" placeholder="አስተያየትዎን እዚህ ይጻፉ..." required></textarea>
        <button type="submit" class="btn" data-en="Submit Review" data-am="አስተያየት ላክ">አስተያየት ላክ</button>
      </form>

      <!-- Reviews Display List -->
      <div class="reviews-list" id="reviewsList">
      </div>
    </div>
  </section>

  <!-- Contact Section -->
  <section id="contact">
    <h2 class="section-title" data-en="Contact Us" data-am="አድራሻችን">አድራሻችን</h2>
    <div class="contact-container">
      <div class="contact-info">
        <div class="contact-item">
          <i class="fa-solid fa-location-dot"></i>
          <span>አዲስ አበባ፣ ኢትዮጵያ (Addis Ababa, Ethiopia)</span>
        </div>
        <div class="contact-item">
          <i class="fa-solid fa-phone"></i>
          <span>+251 900 000 000</span>
        </div>
        <div class="contact-item">
          <i class="fa-solid fa-envelope"></i>
          <span>info@mulugym.com</span>
        </div>
        
        <!-- Telegram Channel / Direct Link -->
        <a href="https://t.me/your_telegram_username" target="_blank" class="telegram-btn" id="tgLink">
          <i class="fa-brands fa-telegram"></i> ቴሌግራም ቻናላችንን ይቀላቀሉ
        </a>
      </div>

      <!-- Location Map -->
      <div class="map-container">
        <iframe 
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d126105.71714041797!2d38.7062438!3d9.0107934!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x164b85cef5ab402d%3A0x8467b6b037a24d49!2sAddis%20Ababa!5e0!3m2!1sen!2set!4v1700000000000!5m2!1sen!2set" 
          allowfullscreen="" 
          loading="lazy">
        </iframe>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <p>&copy; 2026 Mulu Gym. All Rights Reserved. | 🚀 Developed by Yisshak</p>
  </footer>

  <!-- Scripts -->
  <script>
    // 1. Theme Color Switcher (Yellow & Black / White Accent)
    function toggleTheme() {
      document.body.classList.toggle('white-accent-mode');
      const btn = document.querySelector('.theme-btn');
      if(document.body.classList.contains('white-accent-mode')) {
        btn.innerText = "Yellow Accent";
      } else {
        btn.innerText = "White Accent";
      }
    }

    // 2. Language Switcher (Amharic / English)
    let currentLang = 'am';
    function toggleLanguage() {
      currentLang = currentLang === 'am' ? 'en' : 'am';
      document.querySelector('.lang-btn').innerText = currentLang === 'am' ? 'English' : 'አማርኛ';

      document.querySelectorAll('[data-en]').forEach(el => {
        el.innerText = el.getAttribute(`data-${currentLang}`);
      });
    }

    // 3. Booking System (Auto-Copy to Clipboard + Auto Telegram Redirect)
    function handleBooking(e) {
      e.preventDefault();
      const name = document.getElementById('bookName').value.trim();
      const phone = document.getElementById('bookPhone').value.trim();
      const service = document.getElementById('bookService').value;
      const date = document.getElementById('bookDate').value;
      const time = document.getElementById('bookTime').value;

      const bookingText = `📋 *አዲስ የጂም ቡኪንግ (Mulu Gym Booking)*\n\n👤 *ስም:* ${name}\n📞 *ስልክ:* ${phone}\n🏋️‍♂️ *አገልግሎት:* ${service}\n📅 *ቀን:* ${date}\n⏰ *ሰዓት:* ${time}\n\nእባክዎን ምዝገባዬን ያረጋግጡልኝ!`;

      // Copy text to clipboard
      navigator.clipboard.writeText(bookingText).then(() => {
        alert("✅ የቡኪንግ መረጃዎ ተቀድቷል (Copied)! አሁን ወደ ቴሌግራም በመሄድ መልእክቱን ይላኩ።");
        redirectToTelegram(bookingText);
      }).catch(() => {
        redirectToTelegram(bookingText);
      });
    }

    function redirectToTelegram(text) {
      // Replace 'your_telegram_username' with your real Telegram username
      const telegramUsername = "your_telegram_username";
      const tgUrl = `https://t.me/${telegramUsername}?text=${encodeURIComponent(text)}`;
      window.open(tgUrl, '_blank');
    }

    // 4. Firebase & LocalStorage Permanent Reviews Logic
    const firebaseConfig = {
      apiKey: "YOUR_API_KEY",
      authDomain: "mulu-gym.firebaseapp.com",
      projectId: "mulu-gym",
      storageBucket: "mulu-gym.appspot.com",
      messagingSenderId: "YOUR_SENDER_ID",
      appId: "YOUR_APP_ID"
    };

    // Initialize Firebase (safely)
    let db = null;
    try {
      firebase.initializeApp(firebaseConfig);
      db = firebase.firestore();
    } catch (err) {
      console.log("Firebase not configured yet, using local storage fallback.");
    }

    const reviewForm = document.getElementById('reviewForm');
    const reviewsList = document.getElementById('reviewsList');
    const scoreEl = document.getElementById('score');

    // Local Storage Fallback Data Array
    let localReviews = JSON.parse(localStorage.getItem('mulu_gym_reviews')) || [
      { name: "ዮናስ አለሙ", rating: 5, comment: "ምርጥ ጂም ነው! አሰልጣኞቹ በጣም ተባባሪ እና ፕሮፌሽናል ናቸው።" },
      { name: "ቤተልሔም ኃይሉ", rating: 5, comment: "የኤሮቢክስ እና የስቲም አገልግሎታቸው እጅግ ደስ ይላል።" }
    ];

    function renderReviews(reviews) {
      reviewsList.innerHTML = '';
      let totalRating = 0;

      reviews.forEach(data => {
        totalRating += Number(data.rating);

        const item = document.createElement('div');
        item.className = 'review-item';
        item.innerHTML = `
          <div class="review-header">
            <span>${data.name}</span>
            <span class="stars">${'★'.repeat(data.rating)}</span>
          </div>
          <p>${data.comment}</p>
        `;
        reviewsList.appendChild(item);
      });

      if (reviews.length > 0) {
        scoreEl.innerText = (totalRating / reviews.length).toFixed(1);
      } else {
        scoreEl.innerText = '0.0';
      }
    }

    // Load Initial Reviews
    renderReviews(localReviews);

    // Form Submission
    reviewForm.addEventListener('submit', (e) => {
      e.preventDefault();
      const name = document.getElementById('reviewerName').value.trim();
      const rating = Number(document.getElementById('reviewerRating').value);
      const comment = document.getElementById('reviewerComment').value.trim();

      const newReview = { name, rating, comment };

      // Save to LocalStorage
      localReviews.unshift(newReview);
      localStorage.setItem('mulu_gym_reviews', JSON.stringify(localReviews));
      renderReviews(localReviews);

      // Save to Firebase if configured
      if (db) {
        db.collection('reviews').add({
          ...newReview,
          timestamp: firebase.firestore.FieldValue.serverTimestamp()
        }).catch(err => console.error("Firebase error: ", err));
      }

      reviewForm.reset();
      alert("አስተያየትዎ በጥሩ ሁኔታ ተመዝግቧል! እናመሰግናለን።");
    });
  </script>
</body>
</html>
