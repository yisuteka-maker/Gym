<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mulu Gym - ፊቱነስ እና ጂም</title>
  
  <!-- Font Awesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" />
  
  <!-- Firebase SDKs -->
  <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore-compat.js"></script>

  <style>
    :root {
      --primary-color: #ff4500;
      --secondary-color: #111111;
      --accent-color: #222222;
      --light-bg: #0d0d0d;
      --card-bg: #1a1a1a;
      --white: #ffffff;
      --text-gray: #cccccc;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background-color: var(--light-bg);
      color: var(--white);
      line-height: 1.6;
    }

    /* Navbar */
    header {
      background: var(--secondary-color);
      color: var(--white);
      padding: 1rem 2rem;
      position: sticky;
      top: 0;
      z-index: 1000;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid #222;
    }

    .logo {
      font-size: 1.8rem;
      font-weight: bold;
      color: var(--primary-color);
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .logo img {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      object-fit: cover;
    }

    nav ul {
      display: flex;
      list-style: none;
      gap: 20px;
    }

    nav a {
      color: var(--white);
      text-decoration: none;
      font-weight: 500;
      transition: color 0.3s;
    }

    nav a:hover {
      color: var(--primary-color);
    }

    .lang-btn {
      background: var(--primary-color);
      color: var(--white);
      border: none;
      padding: 6px 14px;
      border-radius: 4px;
      cursor: pointer;
      font-weight: bold;
    }

    /* Hero Section (Gym Place PNG Background) */
    .hero {
      background: linear-gradient(rgba(0,0,0,0.75), rgba(0,0,0,0.75)), url('gym place.png') center/cover no-repeat;
      height: 85vh;
      color: var(--white);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 0 20px;
    }

    .hero h1 {
      font-size: 3.2rem;
      margin-bottom: 1rem;
      text-transform: uppercase;
      letter-spacing: 1px;
    }

    .hero p {
      font-size: 1.2rem;
      margin-bottom: 2rem;
      max-width: 600px;
      color: var(--text-gray);
    }

    .btn {
      background: var(--primary-color);
      color: var(--white);
      padding: 12px 28px;
      text-decoration: none;
      border-radius: 25px;
      font-size: 1rem;
      font-weight: bold;
      transition: background 0.3s;
      border: none;
      cursor: pointer;
    }

    .btn:hover {
      background: #e03e00;
    }

    /* Section Styling */
    section {
      padding: 4rem 2rem;
      max-width: 1200px;
      margin: 0 auto;
    }

    .section-title {
      text-align: center;
      font-size: 2.2rem;
      margin-bottom: 2rem;
      position: relative;
    }

    .section-title::after {
      content: '';
      width: 60px;
      height: 4px;
      background: var(--primary-color);
      display: block;
      margin: 8px auto 0;
    }

    /* Services */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
    }

    .service-card {
      background: var(--card-bg);
      padding: 2rem;
      border-radius: 8px;
      text-align: center;
      border: 1px solid #222;
    }

    .service-card i {
      font-size: 2.5rem;
      color: var(--primary-color);
      margin-bottom: 1rem;
    }

    .service-card p {
      color: var(--text-gray);
    }

    /* Gallery (Gym Place PNG) */
    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 15px;
    }

    .gallery-grid img {
      width: 100%;
      height: 240px;
      object-fit: cover;
      border-radius: 8px;
      transition: transform 0.3s;
      border: 1px solid #222;
    }

    .gallery-grid img:hover {
      transform: scale(1.03);
    }

    /* Reviews Section */
    .reviews-container {
      background: var(--card-bg);
      padding: 2rem;
      border-radius: 8px;
      border: 1px solid #222;
    }

    .avg-rating {
      text-align: center;
      font-size: 1.5rem;
      margin-bottom: 1.5rem;
    }

    /* ቢጫ ከለር ተነስቶ በ Orange ተክቷል */
    .stars {
      color: var(--primary-color);
    }

    .review-form {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin-bottom: 2rem;
    }

    .review-form input, .review-form textarea, .review-form select {
      padding: 12px;
      background: #111;
      border: 1px solid #333;
      border-radius: 4px;
      font-size: 1rem;
      color: var(--white);
    }

    .reviews-list {
      display: flex;
      flex-direction: column;
      gap: 15px;
    }

    .review-item {
      border-bottom: 1px solid #333;
      padding-bottom: 10px;
    }

    .review-header {
      display: flex;
      justify-content: space-between;
      font-weight: bold;
    }

    /* Contact & Telegram */
    .contact-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 30px;
    }

    .contact-info {
      display: flex;
      flex-direction: column;
      gap: 15px;
    }

    .contact-item {
      display: flex;
      align-items: center;
      gap: 15px;
      font-size: 1.1rem;
    }

    .contact-item i {
      font-size: 1.5rem;
      color: var(--primary-color);
    }

    .telegram-btn {
      background: #0088cc;
      color: var(--white);
      padding: 12px 20px;
      border-radius: 6px;
      text-decoration: none;
      display: inline-flex;
      align-items: center;
      gap: 10px;
      font-weight: bold;
      width: fit-content;
    }

    .map-container iframe {
      width: 100%;
      height: 280px;
      border: 0;
      border-radius: 8px;
    }

    /* Footer */
    footer {
      background: var(--secondary-color);
      color: var(--text-gray);
      text-align: center;
      padding: 1.5rem;
      margin-top: 2rem;
      border-top: 1px solid #222;
    }

    @media (max-width: 768px) {
      header {
        flex-direction: column;
        gap: 10px;
      }
      .hero h1 {
        font-size: 2.2rem;
      }
    }
  </style>
</head>
<body>

  <!-- Header & Navigation -->
  <header>
    <div class="logo">
      <img src="logo pic .png" alt="Mulu Gym Logo" onerror="this.src='https://via.placeholder.com/40'" />
      Mulu Gym
    </div>
    <nav>
      <ul>
        <li><a href="#home" data-en="Home" data-am="መነሻ">Home</a></li>
        <li><a href="#services" data-en="Services" data-am="አገልግሎቶች">Services</a></li>
        <li><a href="#gallery" data-en="Gallery" data-am="ፎቶዎች">Gallery</a></li>
        <li><a href="#reviews" data-en="Reviews" data-am="አስተያየቶች">Reviews</a></li>
        <li><a href="#contact" data-en="Contact" data-am="አድራሻ">Contact</a></li>
      </ul>
    </nav>
    <button class="lang-btn" onclick="toggleLanguage()">አማርኛ</button>
  </header>

  <!-- Hero Section -->
  <div class="hero" id="home">
    <h1 data-en="Welcome to Mulu Gym" data-am="እንኳን ወደ ሙሉ ጂም በደህና መጡ">Welcome to Mulu Gym</h1>
    <p data-en="Transform your body and mind with our modern equipment and professional trainers." data-am="በዘመናዊ የጂም መሣሪያዎቻችን እና በባለሙያ አሰልጣኞቻችን ጤናዎንና ሰውነትዎን ይገንቡ።">Transform your body and mind with our modern equipment and professional trainers.</p>
    <a href="#contact" class="btn" data-en="Join Us Today" data-am="ዛሬውኑ ይቀላቀሉን">Join Us Today</a>
  </div>

  <!-- Services Section -->
  <section id="services">
    <h2 class="section-title" data-en="Our Services" data-am="አገልግሎቶቻችን">Our Services</h2>
    <div class="services-grid">
      <div class="service-card">
        <i class="fa-solid fa-dumbbell"></i>
        <h3 data-en="Bodybuilding" data-am="የሰውነት ግንባታ">Bodybuilding</h3>
        <p data-en="Complete weight training facilities for all levels." data-am="ለማንኛውም ደረጃ የሚሆኑ የተሟሉ የክብደት ማነሻ መሣሪያዎች።">Complete weight training facilities for all levels.</p>
      </div>
      <div class="service-card">
        <i class="fa-solid fa-heart-pulse"></i>
        <h3 data-en="Cardio Fitness" data-am="ካርዲዮ እና ፊቱነስ">Cardio Fitness</h3>
        <p data-en="Treadmills, bikes, and endurance building tools." data-am="የሩጫ መሣሪያዎች፣ ብስክሌቶች እና የጽናት ማዳበሪያዎች።">Treadmills, bikes, and endurance building tools.</p>
      </div>
      <div class="service-card">
        <i class="fa-solid fa-user-ninja"></i>
        <h3 data-en="Personal Trainer" data-am="የግል አሰልጣኝ">Personal Trainer</h3>
        <p data-en="One-on-one professional guidance tailored for you." data-am="ለእርስዎ የተዘጋጀ የቅርብ የሙያ አሰልጠና እና ክትትል ።">One-on-one professional guidance tailored for you.</p>
      </div>
    </div>
  </section>

  <!-- Gallery Section -->
  <section id="gallery">
    <h2 class="section-title" data-en="Gym Gallery" data-am="የጂሙ ገጽታ">Gym Gallery</h2>
    <div class="gallery-grid">
      <!-- gym place.png ን እዚህ ጋር ይጠቀማል -->
      <img src="gym place.png" alt="Mulu Gym Place" onerror="this.src='https://images.unsplash.com/photo-1534438327276-14e5300c3a48?w=500'" />
      <img src="gym place.png" alt="Gym Area" onerror="this.src='https://images.unsplash.com/photo-1517838277536-f5f99be501cd?w=500'" />
      <img src="gym place.png" alt="Equipments" onerror="this.src='https://images.unsplash.com/photo-1581009146145-b5ef050c2e1e?w=500'" />
    </div>
  </section>

  <!-- Customer Reviews -->
  <section id="reviews">
    <h2 class="section-title" data-en="Customer Reviews" data-am="የደንበኞች አስተያየት">Customer Reviews</h2>
    <div class="reviews-container">
      <div class="avg-rating" id="avgRating">
        <span data-en="Average Rating:" data-am="አማካይ ደረጃ፡">Average Rating:</span> 
        <span id="score">0.0</span> <span class="stars">★</span>
      </div>

      <!-- Form -->
      <form class="review-form" id="reviewForm">
        <input type="text" id="reviewerName" placeholder="Your Name / ስምዎን ያስገቡ" required />
        <select id="reviewerRating" required>
          <option value="5">5 Stars (እጅግ በጣም ጥሩ)</option>
          <option value="4">4 Stars (በጣም ጥሩ)</option>
          <option value="3">3 Stars (ጥሩ)</option>
          <option value="2">2 Stars (መካከለኛ)</option>
          <option value="1">1 Star (ዝቅተኛ)</option>
        </select>
        <textarea id="reviewerComment" rows="3" placeholder="Write your review... / አስተያየትዎን እዚህ ይጻፉ..." required></textarea>
        <button type="submit" class="btn" data-en="Submit Review" data-am="አስተያየት ላክ">Submit Review</button>
      </form>

      <!-- Reviews Display List -->
      <div class="reviews-list" id="reviewsList">
      </div>
    </div>
  </section>

  <!-- Contact Section -->
  <section id="contact">
    <h2 class="section-title" data-en="Contact Us & Location" data-am="አድራሻችን እና ቦታ">Contact Us & Location</h2>
    <div class="contact-container">
      <div class="contact-info">
        <div class="contact-item">
          <i class="fa-solid fa-location-dot"></i>
          <span>Addis Ababa, Ethiopia / አዲስ አበባ፣ ኢትዮጵያ</span>
        </div>
        <div class="contact-item">
          <i class="fa-solid fa-phone"></i>
          <span>+251 900 000 000</span>
        </div>
        <div class="contact-item">
          <i class="fa-solid fa-envelope"></i>
          <span>info@mulugym.com</span>
        </div>
        
        <!-- Telegram Link -->
        <a href="https://t.me/your_telegram_username" target="_blank" class="telegram-btn">
          <i class="fa-brands fa-telegram"></i> Join Telegram Channel
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

  <!-- Firebase & Language Script -->
  <script>
    const firebaseConfig = {
      apiKey: "YOUR_API_KEY",
      authDomain: "mulu-gym.firebaseapp.com",
      projectId: "mulu-gym",
      storageBucket: "mulu-gym.appspot.com",
      messagingSenderId: "YOUR_SENDER_ID",
      appId: "YOUR_APP_ID"
    };

    firebase.initializeApp(firebaseConfig);
    const db = firebase.firestore();

    const reviewForm = document.getElementById('reviewForm');
    const reviewsList = document.getElementById('reviewsList');
    const scoreEl = document.getElementById('score');

    db.collection('reviews').orderBy('timestamp', 'desc').onSnapshot(snapshot => {
      reviewsList.innerHTML = '';
      let totalRating = 0;
      let count = snapshot.docs.length;

      snapshot.docs.forEach(doc => {
        const data = doc.data();
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

      if (count > 0) {
        scoreEl.innerText = (totalRating / count).toFixed(1);
      } else {
        scoreEl.innerText = '0.0';
      }
    });

    reviewForm.addEventListener('submit', (e) => {
      e.preventDefault();
      const name = document.getElementById('reviewerName').value;
      const rating = Number(document.getElementById('reviewerRating').value);
      const comment = document.getElementById('reviewerComment').value;

      db.collection('reviews').add({
        name: name,
        rating: rating,
        comment: comment,
        timestamp: firebase.firestore.FieldValue.serverTimestamp()
      }).then(() => {
        reviewForm.reset();
      }).catch(err => console.error("Error adding review: ", err));
    });

    let currentLang = 'en';
    function toggleLanguage() {
      currentLang = currentLang === 'en' ? 'am' : 'en';
      document.querySelector('.lang-btn').innerText = currentLang === 'en' ? 'አማርኛ' : 'English';

      document.querySelectorAll('[data-en]').forEach(el => {
        el.innerText = el.getAttribute(`data-${currentLang}`);
      });
    }
  </script>
</body>
</html>
