<html lang="en" class="dark scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IRON FORGE | Luxury Gym & Combat Sports</title>
    
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        brand: {
                            black: '#050505',
                            card: '#0D0D0D',
                            yellow: '#FFD400',
                            red: '#E10600',
                            gray: '#A0A0A0',
                            border: '#222222'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        display: ['Oswald', 'sans-serif']
                    }
                }
            }
        }
    </script>
    
    <!-- Google Fonts & Icons -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&family=Oswald:wght@500;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        body { background-color: #050505; color: #ffffff; font-family: 'Inter', sans-serif; overflow-x: hidden; }
        h1, h2, h3, h4, .font-display { font-family: 'Oswald', sans-serif; text-transform: uppercase; letter-spacing: 0.05em; }
        .glow-yellow { box-shadow: 0 0 25px rgba(255, 212, 0, 0.25); }
        .glow-red { box-shadow: 0 0 25px rgba(225, 6, 0, 0.25); }
        .glass-panel { background: rgba(13, 13, 13, 0.85); backdrop-filter: blur(12px); border: 1px solid rgba(255, 255, 255, 0.08); }
        .glass-card { background: rgba(18, 18, 18, 0.85); backdrop-filter: blur(8px); border: 1px solid #222222; transition: all 0.3s ease; }
        .glass-card:hover { border-color: #FFD400; transform: translateY(-3px); }
        .gold-gradient-text { background: linear-gradient(135deg, #FFFFFF 0%, #FFD400 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
    </style>
</head>
<body class="selection:bg-brand-yellow selection:text-black antialiased">

    <!-- NAVIGATION HEADER -->
    <header class="fixed top-0 left-0 w-full z-40 glass-panel border-b border-brand-border/50">
        <div class="max-w-7xl mx-auto px-4 h-20 flex items-center justify-between">
            <a href="#" class="flex items-center gap-3">
                <div class="w-10 h-10 bg-brand-yellow flex items-center justify-center rounded-sm">
                    <i class="fa-solid fa-dumbbell text-black text-xl"></i>
                </div>
                <span class="font-display text-2xl font-bold tracking-wider text-white">IRON <span class="text-brand-yellow">FORGE</span></span>
            </a>

            <nav class="hidden md:flex items-center gap-8 text-sm font-semibold tracking-wider text-gray-300">
                <a href="#programs" id="navPrograms" class="hover:text-brand-yellow">PROGRAMS</a>
                <a href="#about" id="navAbout" class="hover:text-brand-yellow">ABOUT</a>
                <a href="#pricing" id="navPricing" class="hover:text-brand-yellow">MEMBERSHIP</a>
                <a href="#contact" id="navContact" class="hover:text-brand-yellow">CONTACT</a>
            </nav>

            <div class="flex items-center gap-3">
                <!-- LANGUAGE TOGGLE BUTTON -->
                <button onclick="toggleLanguage()" class="px-3 py-1.5 bg-brand-card border border-brand-yellow/50 text-brand-yellow font-bold text-xs rounded hover:bg-brand-yellow hover:text-black transition">
                    <i class="fa-solid fa-globe mr-1"></i><span id="langBtnText">አማርኛ</span>
                </button>

                <button onclick="openRegistrationModal()" id="navJoinBtn" class="px-5 py-2.5 bg-brand-yellow text-black font-display font-bold text-sm tracking-wider rounded hover:bg-yellow-400 glow-yellow">
                    JOIN NOW
                </button>
            </div>
        </div>
    </header>

    <!-- HERO SECTION -->
    <section class="relative min-h-screen flex items-center justify-center pt-20 overflow-hidden">
        <div class="absolute inset-0 z-0">
            <img src="https://images.unsplash.com/photo-1549719386-74dfcbf7dbed?q=80&w=2000&auto=format&fit=crop" class="w-full h-full object-cover filter brightness-40">
            <div class="absolute inset-0 bg-gradient-to-t from-brand-black via-brand-black/60 to-transparent"></div>
        </div>

        <div class="relative z-10 max-w-4xl mx-auto px-4 text-center">
            <h1 id="heroTitle" class="text-4xl sm:text-7xl font-display font-extrabold tracking-tight text-white mb-6">
                FORGE YOUR <br><span class="gold-gradient-text">STRENGTH & LEGACY</span>
            </h1>
            <p id="heroDesc" class="text-lg text-gray-300 mb-8 max-w-2xl mx-auto">Elite Boxing, Muay Thai, Aerobics and General Fitness. Train with passion, dominate your goals.</p>
            <div class="flex flex-col sm:flex-row justify-center gap-4">
                <button onclick="openRegistrationModal()" id="heroRegBtn" class="px-8 py-4 bg-brand-yellow text-black font-display font-bold text-lg rounded glow-yellow">REGISTER NOW</button>
                <a href="#pricing" id="heroPriceBtn" class="px-8 py-4 bg-brand-red text-white font-display font-bold text-lg rounded glow-red">PRICING PLANS</a>
            </div>
        </div>
    </section>

    <!-- PROGRAMS SECTION -->
    <section id="programs" class="py-20 bg-brand-black">
        <div class="max-w-7xl mx-auto px-4">
            <h2 id="programsTitle" class="text-3xl font-display font-bold text-center text-white mb-12">OUR TRAINING PROGRAMS</h2>
            <div id="programsContainer" class="grid grid-cols-1 md:grid-cols-4 gap-6"></div>
        </div>
    </section>

    <!-- PRICING SECTION -->
    <section id="pricing" class="py-20 bg-brand-card">
        <div class="max-w-7xl mx-auto px-4">
            <h2 id="pricingTitle" class="text-3xl font-display font-bold text-center text-white mb-12">MEMBERSHIP PACKAGES</h2>
            <div id="pricingContainer" class="grid grid-cols-1 md:grid-cols-4 gap-6"></div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="bg-brand-black py-8 border-t border-brand-border text-center text-gray-500 text-xs">
        <p>© 2026 IRON FORGE GYM. ALL RIGHTS RESERVED.</p>
        <button onclick="openAdminModal()" class="mt-2 text-brand-yellow underline"><i class="fa-solid fa-lock text-xs mr-1"></i> Admin Portal</button>
    </footer>

    <!-- DIGITAL REGISTRATION MODAL -->
    <div id="registrationModal" class="fixed inset-0 z-50 hidden bg-brand-black/95 backdrop-blur-xl overflow-y-auto">
        <div class="min-h-screen px-4 py-8 flex items-center justify-center">
            <div class="max-w-xl w-full glass-panel border border-brand-yellow/40 rounded p-6 sm:p-8 relative">
                
                <button onclick="closeRegistrationModal()" class="absolute top-4 right-4 text-gray-400 hover:text-white text-xl">
                    <i class="fa-solid fa-xmark"></i>
                </button>

                <div id="registrationFormContainer">
                    <h2 id="modalTitle" class="text-2xl font-display font-bold text-center text-white mb-6">GYM REGISTRATION FORM</h2>
                    <form onsubmit="handleRegistrationSubmit(event)" class="space-y-4">
                        <div>
                            <label id="lblProgram" class="block text-xs font-bold text-gray-300 mb-1">SELECTED PROGRAM</label>
                            <select id="regProgram" class="w-full bg-brand-black border border-brand-border rounded px-3 py-2 text-sm text-white">
                                <option value="Boxing">🥊 Boxing</option>
                                <option value="Muay Thai">🥋 Muay Thai</option>
                                <option value="Aerobics & Fitness">🏃 Aerobics & Fitness</option>
                                <option value="General Gym">💪 General Gym</option>
                            </select>
                        </div>

                        <div>
                            <label id="lblName" class="block text-xs font-bold text-gray-300 mb-1">FULL NAME *</label>
                            <input type="text" id="regName" required placeholder="John Doe" class="w-full bg-brand-black border border-brand-border rounded px-3 py-2 text-sm text-white">
                        </div>

                        <div class="grid grid-cols-2 gap-3">
                            <div>
                                <label id="lblPhone" class="block text-xs font-bold text-gray-300 mb-1">PHONE *</label>
                                <input type="tel" id="regPhone" required placeholder="09..." class="w-full bg-brand-black border border-brand-border rounded px-3 py-2 text-sm text-white">
                            </div>
                            <div>
                                <label id="lblAge" class="block text-xs font-bold text-gray-300 mb-1">AGE *</label>
                                <input type="number" id="regAge" required placeholder="22" class="w-full bg-brand-black border border-brand-border rounded px-3 py-2 text-sm text-white">
                            </div>
                        </div>

                        <div>
                            <label id="lblGender" class="block text-xs font-bold text-gray-300 mb-1">GENDER *</label>
                            <select id="regGender" class="w-full bg-brand-black border border-brand-border rounded px-3 py-2 text-sm text-white">
                                <option value="Male">Male / ወንድ</option>
                                <option value="Female">Female / ሴት</option>
                            </select>
                        </div>

                        <div>
                            <label id="lblPlan" class="block text-xs font-bold text-gray-300 mb-1">MEMBERSHIP PLAN *</label>
                            <select id="regPlan" class="w-full bg-brand-black border border-brand-border rounded px-3 py-2 text-sm text-white"></select>
                        </div>

                        <div>
                            <label id="lblEmergency" class="block text-xs font-bold text-gray-300 mb-1">EMERGENCY CONTACT NAME & PHONE *</label>
                            <input type="text" id="regEmergency" required placeholder="Name & Phone" class="w-full bg-brand-black border border-brand-border rounded px-3 py-2 text-sm text-white">
                        </div>

                        <button id="submitBtn" type="submit" class="w-full py-3 bg-brand-yellow text-black font-display font-bold text-sm rounded glow-yellow uppercase mt-4">
                            SUBMIT REGISTRATION
                        </button>
                    </form>
                </div>

                <!-- SUCCESS SCREEN AFTER REGISTRATION -->
                <div id="regSuccessScreen" class="hidden text-center py-6 space-y-6">
                    <div class="w-16 h-16 bg-brand-yellow/20 border-2 border-brand-yellow rounded-full flex items-center justify-center mx-auto text-brand-yellow text-3xl">
                        <i class="fa-solid fa-check"></i>
                    </div>

                    <div>
                        <h3 id="succHeader" class="text-2xl font-display font-bold text-white">REGISTRATION SUCCESSFUL!</h3>
                        <p id="succSub" class="text-sm text-gray-300 mt-2 font-semibold">
                            Your details have been submitted to the admin via Telegram.
                        </p>
                    </div>

                    <div class="p-4 bg-brand-black border border-brand-border rounded text-left text-xs space-y-2">
                        <p><span id="succIdLbl" class="text-gray-400">Reg ID:</span> <span id="resRegId" class="text-brand-yellow font-bold"></span></p>
                        <p><span id="succNameLbl" class="text-gray-400">Name:</span> <span id="resName" class="text-white font-bold"></span></p>
                        <p><span id="succProgLbl" class="text-gray-400">Program:</span> <span id="resProgram" class="text-white font-bold"></span></p>
                    </div>

                    <button onclick="closeRegistrationModal()" id="succDoneBtn" class="w-full py-3 bg-brand-yellow text-black font-bold text-xs uppercase rounded glow-yellow">
                        DONE
                    </button>
                </div>

            </div>
        </div>
    </div>

    <!-- ADMIN PANEL MODAL -->
    <div id="adminModal" class="fixed inset-0 z-50 hidden bg-brand-black/95 backdrop-blur-xl overflow-y-auto">
        <div class="min-h-screen px-4 py-8">
            <div class="max-w-5xl mx-auto flex justify-between items-center pb-6 border-b border-brand-border">
                <h2 class="text-2xl font-display font-bold text-white">IRON FORGE <span class="text-brand-yellow">ADMIN PANEL</span></h2>
                <button onclick="closeAdminModal()" class="px-4 py-1.5 bg-brand-card border border-brand-border text-xs text-gray-300 rounded">Exit Admin</button>
            </div>

            <!-- LOGIN FORM -->
            <div id="adminLoginView" class="max-w-md mx-auto my-16 glass-panel p-6 rounded space-y-4">
                <h3 class="text-xl font-display font-bold text-center">ADMIN AUTHENTICATION</h3>
                <form onsubmit="handleAdminLogin(event)" class="space-y-4">
                    <div>
                        <label class="block text-xs font-bold text-gray-300 mb-1">ENTER ADMIN PASSWORD</label>
                        <input type="password" id="adminPassInput" required class="w-full bg-brand-black border border-brand-border rounded px-3 py-2 text-sm text-white focus:border-brand-yellow">
                    </div>
                    <button type="submit" class="w-full py-2.5 bg-brand-yellow text-black font-bold text-xs uppercase rounded glow-yellow">LOGIN</button>
                </form>
            </div>

            <!-- DASHBOARD MAIN PANEL -->
            <div id="adminMainDashboard" class="max-w-5xl mx-auto pt-6 space-y-8 hidden">
                
                <!-- CHANGE PRICES SECTION -->
                <div class="glass-card p-6 rounded space-y-4">
                    <h3 class="font-display font-bold text-lg text-brand-yellow">1. የጂም ክፍያዎችን ማስተካከያ (MEMBERSHIP PRICES)</h3>
                    <div id="adminPriceEditorContainer" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4"></div>
                    <button onclick="saveAdminPrices()" class="px-6 py-2 bg-brand-yellow text-black font-bold text-xs rounded">Save Prices</button>
                </div>

                <!-- CHANGE PASSWORD SECTION -->
                <div class="glass-card p-6 rounded space-y-4">
                    <h3 class="font-display font-bold text-lg text-brand-red">2. የአድሚን ፓስወርድ ማስተካከያ (CHANGE PASSWORD)</h3>
                    <div class="max-w-md space-y-3">
                        <input type="password" id="newAdminPass" placeholder="አዲስ ፓስወርድ ያስገቡ" class="w-full bg-brand-black border border-brand-border px-3 py-2 text-sm rounded text-white">
                        <button onclick="changeAdminPassword()" class="px-6 py-2 bg-brand-red text-white font-bold text-xs rounded">Update Password</button>
                    </div>
                </div>

                <!-- REGISTRATIONS TABLE -->
                <div class="glass-card p-6 rounded space-y-4">
                    <h3 class="font-display font-bold text-lg text-white">3. የተመዘገቡ አባላት ዝርዝር (REGISTRATIONS)</h3>
                    <div class="overflow-x-auto">
                        <table class="w-full text-left text-xs text-gray-300">
                            <thead class="bg-brand-black text-brand-yellow uppercase">
                                <tr>
                                    <th class="p-2">ID</th>
                                    <th class="p-2">ስም</th>
                                    <th class="p-2">ስልክ</th>
                                    <th class="p-2">ፕሮግራም</th>
                                    <th class="p-2">ፓኬጅ</th>
                                    <th class="p-2">ቀን</th>
                                </tr>
                            </thead>
                            <tbody id="adminRegsTable" class="divide-y divide-brand-border"></tbody>
                        </table>
                    </div>
                </div>

            </div>
        </div>
    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        let currentLang = 'en'; // Default language

        // System State
        let adminPassword = "123gym456";

        let state = {
            programs: [
                { title: 'BOXING', titleAm: 'ቦክስ (BOXING)', desc: 'Professional boxing conditioning and ring technique.', descAm: 'የባለሙያ ቦክስ ስልጠና እና ቴክኒክ።', img: 'https://images.unsplash.com/photo-1549719386-74dfcbf7dbed?q=80&w=600&auto=format&fit=crop' },
                { title: 'MUAY THAI', titleAm: 'ሙአይ ታይ (MUAY THAI)', desc: 'Authentic 8-limbs combat discipline.', descAm: 'ትክክለኛው የሙአይ ታይ ውጊያ ስልጠና።', img: 'https://images.unsplash.com/photo-1599058945522-28d584b6f0ff?q=80&w=600&auto=format&fit=crop' },
                { title: 'AEROBICS & FITNESS', titleAm: 'ኤሮቢክስ (AEROBICS)', desc: 'HIIT cardio fat burn and rhythm workout.', descAm: 'የስብ ማቃጠል እና የልብ ጤንነት ስልጠና።', img: 'https://images.unsplash.com/photo-1518611012118-696072aa579a?q=80&w=600&auto=format&fit=crop' },
                { title: 'GENERAL GYM', titleAm: 'ጀነራል ጂም (FITNESS)', desc: 'Strength training and body building.', descAm: 'የሰውነት ግንባታ እና የጥንካሬ ስልጠና።', img: 'https://images.unsplash.com/photo-1534438327276-14e5300c3a48?q=80&w=600&auto=format&fit=crop' }
            ],
            pricing: [
                { id: 'm1', name: 'MONTHLY', nameAm: 'የ 1 ወር', price: '2,500 ETB' },
                { id: 'm3', name: '3 MONTHS', nameAm: 'የ 3 ወር', price: '6,800 ETB' },
                { id: 'm6', name: '6 MONTHS', nameAm: 'የ 6 ወር', price: '12,500 ETB' },
                { id: 'm12', name: 'YEARLY', nameAm: 'የ 1 ዓመት', price: '22,000 ETB' }
            ],
            registrations: []
        };

        const translations = {
            en: {
                langBtn: "አማርኛ",
                navPrograms: "PROGRAMS",
                navAbout: "ABOUT",
                navPricing: "MEMBERSHIP",
                navContact: "CONTACT",
                navJoinBtn: "JOIN NOW",
                heroTitle: 'FORGE YOUR <br><span class="gold-gradient-text">STRENGTH & LEGACY</span>',
                heroDesc: "Elite Boxing, Muay Thai, Aerobics and General Fitness. Train with passion, dominate your goals.",
                heroRegBtn: "REGISTER NOW",
                heroPriceBtn: "PRICING PLANS",
                programsTitle: "OUR TRAINING PROGRAMS",
                pricingTitle: "MEMBERSHIP PACKAGES",
                modalTitle: "GYM REGISTRATION FORM",
                lblProgram: "SELECTED PROGRAM",
                lblName: "FULL NAME *",
                lblPhone: "PHONE *",
                lblAge: "AGE *",
                lblGender: "GENDER *",
                lblPlan: "MEMBERSHIP PLAN *",
                lblEmergency: "EMERGENCY CONTACT NAME & PHONE *",
                submitBtn: "SUBMIT REGISTRATION",
                succHeader: "REGISTRATION SUCCESSFUL!",
                succSub: "Your details have been submitted to the admin via Telegram.",
                succIdLbl: "Reg ID:",
                succNameLbl: "Name:",
                succProgLbl: "Program:",
                succDoneBtn: "DONE",
                cardRegBtn: "REGISTER",
                cardChooseBtn: "CHOOSE PLAN"
            },
            am: {
                langBtn: "English",
                navPrograms: "ፕሮግራሞች",
                navAbout: "ስለ እኛ",
                navPricing: "አባልነት",
                navContact: "አድራሻ",
                navJoinBtn: "አሁኑኑ ተመዝገብ",
                heroTitle: 'ጥንካሬዎትን <br><span class="gold-gradient-text">እዚህ ይገንቡ</span>',
                heroDesc: "ቦክስ፣ ሙአይ ታይ፣ ኤሮቢክስ እና የሰውነት ማሰልጠኛ ጂም። በቁርጠኝነት ይሰልጥኑ፣ ግብዎን ያሳኩ።",
                heroRegBtn: "አሁኑኑ ይመዝገቡ",
                heroPriceBtn: "የክፍያ አማራጮች",
                programsTitle: "የስልጠና ፕሮግራሞቻችን",
                pricingTitle: "የአባልነት ክፍያ ፓኬጆች",
                modalTitle: "የጂም ምዝገባ ቅጽ",
                lblProgram: "የመረጡት ፕሮግራም",
                lblName: "ሙሉ ስም *",
                lblPhone: "ስልክ ቁጥር *",
                lblAge: "እድሜ *",
                lblGender: "ጾታ *",
                lblPlan: "የአባልነት ዓይነት *",
                lblEmergency: "የአደጋ ጊዜ ተጠሪ ስምና ስልክ *",
                submitBtn: "ምዝገባውን ላክ",
                succHeader: "ምዝገባዎ በተሳካ ሁኔታ ተጠናቋል!",
                succSub: "መረጃዎ ቀጥታ ወደ አድሚን ተልኳል።",
                succIdLbl: "የምዝገባ መለያ ID:",
                succNameLbl: "ስም:",
                succProgLbl: "ፕሮግራም:",
                succDoneBtn: "ጨርስ",
                cardRegBtn: "ተመዝገብ",
                cardChooseBtn: "ምረጥ"
            }
        };

        document.addEventListener("DOMContentLoaded", function() {
            renderPageContent();
        });

        function toggleLanguage() {
            currentLang = (currentLang === 'en') ? 'am' : 'en';
            renderPageContent();
        }

        function renderPageContent() {
            const t = translations[currentLang];

            document.getElementById('langBtnText').innerText = t.langBtn;
            document.getElementById('navPrograms').innerText = t.navPrograms;
            document.getElementById('navAbout').innerText = t.navAbout;
            document.getElementById('navPricing').innerText = t.navPricing;
            document.getElementById('navContact').innerText = t.navContact;
            document.getElementById('navJoinBtn').innerText = t.navJoinBtn;

            document.getElementById('heroTitle').innerHTML = t.heroTitle;
            document.getElementById('heroDesc').innerText = t.heroDesc;
            document.getElementById('heroRegBtn').innerText = t.heroRegBtn;
            document.getElementById('heroPriceBtn').innerText = t.heroPriceBtn;

            document.getElementById('programsTitle').innerText = t.programsTitle;
            document.getElementById('pricingTitle').innerText = t.pricingTitle;

            document.getElementById('modalTitle').innerText = t.modalTitle;
            document.getElementById('lblProgram').innerText = t.lblProgram;
            document.getElementById('lblName').innerText = t.lblName;
            document.getElementById('lblPhone').innerText = t.lblPhone;
            document.getElementById('lblAge').innerText = t.lblAge;
            document.getElementById('lblGender').innerText = t.lblGender;
            document.getElementById('lblPlan').innerText = t.lblPlan;
            document.getElementById('lblEmergency').innerText = t.lblEmergency;
            document.getElementById('submitBtn').innerText = t.submitBtn;

            document.getElementById('succHeader').innerText = t.succHeader;
            document.getElementById('succSub').innerText = t.succSub;
            document.getElementById('succIdLbl').innerText = t.succIdLbl;
            document.getElementById('succNameLbl').innerText = t.succNameLbl;
            document.getElementById('succProgLbl').innerText = t.succProgLbl;
            document.getElementById('succDoneBtn').innerText = t.succDoneBtn;

            renderPrograms();
            renderPricing();
            populatePlanOptions();
        }

        function renderPrograms() {
            const t = translations[currentLang];
            document.getElementById('programsContainer').innerHTML = state.programs.map(p => `
                <div class="glass-card rounded overflow-hidden p-4 space-y-3">
                    <img src="${p.img}" class="w-full h-36 object-cover rounded">
                    <h3 class="font-display font-bold text-lg text-white">${currentLang === 'am' ? p.titleAm : p.title}</h3>
                    <p class="text-xs text-gray-400">${currentLang === 'am' ? p.descAm : p.desc}</p>
                    <button onclick="openRegistrationModal('${p.title}')" class="w-full py-2 bg-brand-yellow text-black font-bold text-xs rounded">${t.cardRegBtn}</button>
                </div>
            `).join('');
        }

        function renderPricing() {
            const t = translations[currentLang];
            document.getElementById('pricingContainer').innerHTML = state.pricing.map(p => `
                <div class="glass-card p-6 rounded text-center space-y-3">
                    <h3 class="font-display font-bold text-xl text-white">${currentLang === 'am' ? p.nameAm : p.name}</h3>
                    <div class="text-2xl font-bold text-brand-yellow">${p.price}</div>
                    <button onclick="openRegistrationModal(null, '${p.name}')" class="w-full py-2 bg-brand-red text-white font-bold text-xs rounded">${t.cardChooseBtn}</button>
                </div>
            `).join('');
        }

        function populatePlanOptions() {
            document.getElementById('regPlan').innerHTML = state.pricing.map(p => `
                <option value="${p.name} (${p.price})">${currentLang === 'am' ? p.nameAm : p.name} - ${p.price}</option>
            `).join('');
        }

        function openRegistrationModal(program = null, plan = null) {
            document.getElementById('registrationModal').classList.remove('hidden');
            document.getElementById('registrationFormContainer').classList.remove('hidden');
            document.getElementById('regSuccessScreen').classList.add('hidden');
            if (program) document.getElementById('regProgram').value = program;
        }

        function closeRegistrationModal() {
            document.getElementById('registrationModal').classList.add('hidden');
        }

        async function handleRegistrationSubmit(e) {
            e.preventDefault();

            const submitBtn = document.getElementById('submitBtn');
            submitBtn.innerText = currentLang === 'am' ? "እየላከ ነው..." : "SENDING...";
            submitBtn.disabled = true;

            const regData = {
                id: 'IF-' + Math.floor(1000 + Math.random() * 9000),
                name: document.getElementById('regName').value,
                phone: document.getElementById('regPhone').value,
                age: document.getElementById('regAge').value,
                gender: document.getElementById('regGender').value,
                program: document.getElementById('regProgram').value,
                plan: document.getElementById('regPlan').value,
                emergency: document.getElementById('regEmergency').value,
                date: new Date().toLocaleDateString()
            };

            const success = await sendTelegramNotification(regData);

            submitBtn.innerText = translations[currentLang].submitBtn;
            submitBtn.disabled = false;

            if (success) {
                state.registrations.unshift(regData);

                document.getElementById('registrationFormContainer').classList.add('hidden');
                document.getElementById('regSuccessScreen').classList.remove('hidden');

                document.getElementById('resRegId').innerText = regData.id;
                document.getElementById('resName').innerText = regData.name;
                document.getElementById('resProgram').innerText = `${regData.program} - ${regData.plan}`;
            } else {
                alert(currentLang === 'am' ? "መረጃውን መላክ አልተቻለም። እባክዎን ኢንተርኔትዎን ያረጋግጡ!" : "Failed to send registration. Please check your network connection!");
            }
        }

        async function sendTelegramNotification(data) {
            const botToken = "8752629354:AAEwRCOv5_SR4ynYGFZLgBD_b999E2SEpyA"; 
            const chatId = "-1004466655656";
            
            const message = `🏋️ *አዲስ የጂም ምዝገባ (IRON FORGE)*\n\n` +
                            `🆔 *ID:* ${data.id}\n` +
                            `👤 *ስም:* ${data.name}\n` +
                            `📞 *ስልክ:* ${data.phone}\n` +
                            `🎂 *እድሜ:* ${data.age} | *ጾታ:* ${data.gender}\n` +
                            `🥊 *ፕሮግራም:* ${data.program}\n` +
                            `💳 *የክፍያ ፓኬጅ:* ${data.plan}\n` +
                            `🚨 *የአደጋ ጊዜ ተጠሪ:* ${data.emergency}\n` +
                            `📅 *ቀን:* ${data.date}`;

            try {
                const response = await fetch(`https://api.telegram.org/bot${botToken}/sendMessage`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        chat_id: chatId,
                        text: message,
                        parse_mode: 'Markdown'
                    })
                });

                const resData = await response.json();
                return resData.ok;
            } catch (err) {
                console.error("Error sending to telegram", err);
                return false;
            }
        }

        // ADMIN FUNCTIONS
        function openAdminModal() {
            document.getElementById('adminModal').classList.remove('hidden');
        }

        function closeAdminModal() {
            document.getElementById('adminModal').classList.add('hidden');
        }

        function handleAdminLogin(e) {
            e.preventDefault();
            const pass = document.getElementById('adminPassInput').value;
            if (pass === adminPassword) {
                document.getElementById('adminLoginView').classList.add('hidden');
                document.getElementById('adminMainDashboard').classList.remove('hidden');
                renderAdminView();
            } else {
                alert('የተሳሳተ ፓስወርድ ነው!');
            }
        }

        function renderAdminView() {
            document.getElementById('adminPriceEditorContainer').innerHTML = state.pricing.map((p, i) => `
                <div class="p-3 bg-brand-black border border-brand-border rounded">
                    <label class="block text-[10px] text-brand-yellow font-bold">${p.name}</label>
                    <input type="text" id="adminPriceInput_${i}" value="${p.price}" class="w-full bg-brand-card border border-brand-border px-2 py-1 text-xs text-white rounded mt-1">
                </div>
            `).join('');

            document.getElementById('adminRegsTable').innerHTML = state.registrations.map(r => `
                <tr>
                    <td class="p-2 font-bold text-brand-yellow">${r.id}</td>
                    <td class="p-2 font-bold text-white">${r.name}</td>
                    <td class="p-2">${r.phone}</td>
                    <td class="p-2">${r.program}</td>
                    <td class="p-2">${r.plan}</td>
                    <td class="p-2">${r.date}</td>
                </tr>
            `).join('');
        }

        function saveAdminPrices() {
            state.pricing.forEach((p, i) => {
                const val = document.getElementById(`adminPriceInput_${i}`).value;
                if (val) p.price = val;
            });
            renderPricing();
            populatePlanOptions();
            alert('የጂም አባልነት ክፍያዎች በተሳካ ሁኔታ ተቀይረዋል!');
        }

        function changeAdminPassword() {
            const newPass = document.getElementById('newAdminPass').value;
            if (newPass.trim() !== '') {
                adminPassword = newPass;
                alert('የአድሚን ፓስወርድ በተሳካ ሁኔታ ተቀይሯል!');
                document.getElementById('newAdminPass').value = '';
            }
        }
    </script>
</body>
</html>
