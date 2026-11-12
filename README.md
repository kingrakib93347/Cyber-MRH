```html
<!DOCTYPE html>
<html lang="bn" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cyber MRH | Md. Rakib Hasan - Private Portfolio</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Inter & Hind Siliguri for clean Bengali & English typography -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@300;400;500;600;700&family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <!-- Font Awesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <!-- Tone.js for subtle lamp click & unlock sound effects -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/tone/14.8.49/Tone.js"></script>

    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'Hind Siliguri', 'sans-serif'],
                        bengali: ['Hind Siliguri', 'sans-serif'],
                    },
                    colors: {
                        cyber: {
                            bg: '#090b10',
                            card: '#111622',
                            border: '#1e2638',
                            accent: '#38bdf8',
                            gold: '#fbbf24'
                        }
                    }
                }
            }
        }
    </script>

    <style>
        /* Custom Atmospheric Styling & Lamp Physics Animations */
        body {
            background-color: #07090e;
            color: #f8fafc;
            font-family: 'Inter', 'Hind Siliguri', sans-serif;
            overflow-x: hidden;
            user-select: none;
        }

        /* Warm Light Cone Glow Effect */
        .lamp-light-cone {
            background: radial-gradient(ellipse at 50% 0%, rgba(251, 191, 36, 0.35) 0%, rgba(245, 158, 11, 0.12) 45%, rgba(7, 9, 14, 0) 78%);
            clip-path: polygon(44% 0%, 56% 0%, 95% 100%, 5% 100%);
            transition: opacity 0.5s cubic-bezier(0.4, 0, 0.2, 1), transform 0.6s ease;
            pointer-events: none;
        }

        .lamp-bulb-glow {
            box-shadow: 0 0 35px 12px rgba(251, 191, 36, 0.8), 0 0 80px 30px rgba(245, 158, 11, 0.45);
        }

        /* Glassmorphism Login Card */
        .glass-login {
            background: rgba(17, 22, 34, 0.68);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(251, 191, 36, 0.25);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.7), 0 0 30px rgba(251, 191, 36, 0.08);
        }

        /* Profile Card Glass & Cyber Border */
        .cyber-card {
            background: linear-gradient(145deg, rgba(17, 22, 34, 0.9), rgba(11, 15, 25, 0.95));
            border: 1px solid rgba(56, 189, 248, 0.15);
            transition: transform 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
        }
        .cyber-card:hover {
            transform: translateY(-3px);
            border-color: rgba(56, 189, 248, 0.45);
            box-shadow: 0 12px 30px -10px rgba(56, 189, 248, 0.15);
        }

        /* Shake animation on wrong passcode */
        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            20%, 60% { transform: translateX(-8px); }
            40%, 80% { transform: translateX(8px); }
        }
        .animate-shake {
            animation: shake 0.4s ease-in-out;
        }

        /* Gentle ambient float for hint */
        @keyframes floatSlow {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-5px); }
        }
        .animate-float {
            animation: floatSlow 2.5s ease-in-out infinite;
        }

        /* Page Transition Animation */
        @keyframes fadeSlideUp {
            from {
                opacity: 0;
                transform: translateY(14px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        .page-enter {
            animation: fadeSlideUp 0.4s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        /* Blinking Terminal Cursor */
        @keyframes blinkCursor {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }
        .cursor-blink {
            animation: blinkCursor 1s infinite;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #07090e;
        }
        ::-webkit-scrollbar-thumb {
            background: #1e293b;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #38bdf8;
        }
    </style>
</head>
<body class="min-h-screen antialiased selection:bg-sky-500 selection:text-white">

    <!-- ===================================================================== -->
    <!-- SECTION 2: UNLOCKED PRIVATE PROFILE DASHBOARD (MULTI-PAGE SPA)        -->
    <!-- ===================================================================== -->
    <div id="profile-dashboard" class="hidden opacity-0 transition-opacity duration-700 min-h-screen flex flex-col justify-between bg-[#080b12]">
        
        <!-- Top Navigation & Three-Dot Menu Header -->
        <header class="sticky top-0 z-40 backdrop-blur-md bg-[#080b12]/90 border-b border-slate-800/80">
            <div class="max-w-5xl mx-auto px-4 sm:px-6 py-3.5 flex items-center justify-between gap-3">
                <!-- Brand Logo (Clicking goes to Home Page) -->
                <button type="button" onclick="switchPage('home')" class="flex items-center gap-3 text-left group cursor-pointer">
                    <div class="w-9 h-9 rounded-xl bg-gradient-to-br from-sky-400 to-indigo-600 flex items-center justify-center text-slate-950 font-extrabold text-sm shadow-md shadow-sky-500/20 group-hover:scale-105 transition-transform">
                        MRH
                    </div>
                    <div>
                        <div class="flex items-center gap-2">
                            <span class="font-bold text-white text-base tracking-tight group-hover:text-sky-400 transition-colors">Cyber MRH</span>
                            <span id="access-badge" class="px-2 py-0.5 text-[10px] font-semibold uppercase tracking-wider rounded-full bg-emerald-500/15 text-emerald-400 border border-emerald-500/30">
                                <i class="fa-solid fa-eye text-[9px] mr-1"></i>Visitor View
                            </span>
                        </div>
                        <p class="text-[11px] text-slate-400">Creator: MD Rakib Hasan</p>
                    </div>
                </button>

                <!-- Right Controls: Active Page Pill + Three-Dot Menu + Lock Button -->
                <div class="flex items-center gap-2 sm:gap-3 relative">
                    <!-- Current Page Indicator (Desktop/Tablet) -->
                    <span id="current-page-label" class="hidden sm:inline-flex items-center gap-1.5 px-3 py-1.5 rounded-xl bg-slate-900/90 border border-slate-800 text-xs font-medium text-sky-400">
                        <i class="fa-solid fa-terminal text-[10px]"></i>
                        <span>হোম (Cyber Front)</span>
                    </span>

                    <!-- Three-Dot Navigation Menu Button -->
                    <div class="relative" id="nav-menu-container">
                        <button id="three-dot-btn" type="button" aria-label="পেজ মেনু খুলুন" class="w-10 h-10 rounded-xl bg-slate-900 hover:bg-slate-800 text-slate-200 hover:text-sky-400 border border-slate-700/80 hover:border-sky-500/40 flex items-center justify-center transition-all cursor-pointer shadow-sm">
                            <i class="fa-solid fa-ellipsis-vertical text-base"></i>
                        </button>

                        <!-- Dropdown Page Navigation Menu -->
                        <div id="three-dot-dropdown" class="hidden absolute right-0 mt-2.5 w-60 rounded-2xl bg-[#0e1320]/95 backdrop-blur-xl border border-slate-700/80 shadow-2xl shadow-black/80 py-2 z-50 origin-top-right">
                            <div class="px-3.5 py-1.5 border-b border-slate-800/80 text-[10px] font-semibold uppercase tracking-wider text-slate-500">
                                সেকশন নির্বাচন করুন (Pages)
                            </div>
                            <button type="button" onclick="switchPage('home')" data-nav="home" class="nav-item w-full px-4 py-2.5 text-left text-xs sm:text-sm text-sky-400 bg-sky-500/10 font-semibold flex items-center gap-3 transition-colors cursor-pointer">
                                <i class="fa-solid fa-terminal w-4 text-center"></i>
                                <span>হোম (Cyber Front)</span>
                            </button>
                            <button type="button" onclick="switchPage('identity')" data-nav="identity" class="nav-item w-full px-4 py-2.5 text-left text-xs sm:text-sm text-slate-300 hover:bg-slate-800/80 hover:text-white flex items-center gap-3 transition-colors cursor-pointer">
                                <i class="fa-solid fa-id-card w-4 text-center text-sky-400"></i>
                                <span>পরিচয় (Identity)</span>
                            </button>
                            <button type="button" onclick="switchPage('academics')" data-nav="academics" class="nav-item w-full px-4 py-2.5 text-left text-xs sm:text-sm text-slate-300 hover:bg-slate-800/80 hover:text-white flex items-center gap-3 transition-colors cursor-pointer">
                                <i class="fa-solid fa-graduation-cap w-4 text-center text-amber-400"></i>
                                <span>একাডেমিকস (Academics)</span>
                            </button>
                            <button type="button" onclick="switchPage('skills')" data-nav="skills" class="nav-item w-full px-4 py-2.5 text-left text-xs sm:text-sm text-slate-300 hover:bg-slate-800/80 hover:text-white flex items-center gap-3 transition-colors cursor-pointer">
                                <i class="fa-solid fa-code w-4 text-center text-emerald-400"></i>
                                <span>দক্ষতা (Skills)</span>
                            </button>
                            <button type="button" onclick="switchPage('hobbies')" data-nav="hobbies" class="nav-item w-full px-4 py-2.5 text-left text-xs sm:text-sm text-slate-300 hover:bg-slate-800/80 hover:text-white flex items-center gap-3 transition-colors cursor-pointer">
                                <i class="fa-solid fa-feather-pointed w-4 text-center text-purple-400"></i>
                                <span>হবি ও ইচ্ছা (Hobbies)</span>
                            </button>
                            <button type="button" onclick="switchPage('contact')" data-nav="contact" class="nav-item w-full px-4 py-2.5 text-left text-xs sm:text-sm text-slate-300 hover:bg-slate-800/80 hover:text-white flex items-center gap-3 transition-colors cursor-pointer">
                                <i class="fa-solid fa-address-book w-4 text-center text-rose-400"></i>
                                <span>কন্টাক্ট (Contact)</span>
                            </button>
                        </div>
                    </div>

                    <!-- Lock Vault Button -->
                    <button id="lock-btn" type="button" class="px-3 sm:px-3.5 py-2.5 rounded-xl bg-slate-900 hover:bg-rose-500/15 text-slate-300 hover:text-rose-400 border border-slate-700/80 hover:border-rose-500/40 text-xs font-semibold transition-all flex items-center gap-2 cursor-pointer" title="ল্যাম্প নিভিয়ে লক করুন">
                        <i class="fa-solid fa-power-off"></i>
                        <span class="hidden md:inline">লক (Lock)</span>
                    </button>
                </div>
            </div>
        </header>

        <!-- Main Separate Page Container -->
        <main class="max-w-5xl w-full mx-auto px-4 sm:px-6 py-8 sm:py-12 flex-1 flex flex-col justify-center">

            <!-- =============================================================== -->
            <!-- PAGE 1: CYBER / HACKER WORLD FRONT PAGE (DEFAULT HOME)          -->
            <!-- =============================================================== -->
            <section id="page-home" class="page-section page-enter space-y-6">
                <div class="cyber-card rounded-3xl p-6 sm:p-10 lg:p-12 relative overflow-hidden border border-sky-500/25">
                    <!-- Cyber Matrix Grid & Ambient Glow -->
                    <div class="absolute inset-0 bg-[radial-gradient(#38bdf8_1px,transparent_1px)] [background-size:24px_24px] opacity-[0.07] pointer-events-none"></div>
                    <div class="absolute -top-24 -right-24 w-80 h-80 bg-sky-500/15 rounded-full blur-3xl pointer-events-none"></div>
                    <div class="absolute -bottom-24 -left-24 w-80 h-80 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>

                    <!-- Simulated Cyber Terminal Top Bar -->
                    <div class="relative z-10 flex items-center justify-between px-4 py-2.5 mb-8 rounded-2xl bg-slate-950/90 border border-slate-800/90 font-mono text-xs">
                        <div class="flex items-center gap-2">
                            <span class="w-2.5 h-2.5 rounded-full bg-rose-500"></span>
                            <span class="w-2.5 h-2.5 rounded-full bg-amber-400"></span>
                            <span class="w-2.5 h-2.5 rounded-full bg-emerald-500"></span>
                            <span class="ml-2 text-slate-400 hidden sm:inline">root@cyber-mrh:~# ./init_portfolio.sh</span>
                        </div>
                        <span class="text-emerald-400 flex items-center gap-1.5">
                            <span class="w-2 h-2 rounded-full bg-emerald-400 animate-ping"></span>
                            SYSTEM ONLINE
                        </span>
                    </div>

                    <!-- Hero Split: Portrait + Captivating Cyber Description -->
                    <div class="relative z-10 flex flex-col md:flex-row items-center gap-8 sm:gap-10">
                        <!-- Profile Portrait -->
                        <div class="flex flex-col items-center shrink-0">
                            <div class="relative group">
                                <div class="w-36 h-36 sm:w-44 sm:h-44 rounded-3xl p-1.5 bg-gradient-to-tr from-sky-400 via-emerald-400 to-indigo-500 shadow-xl shadow-sky-500/20">
                                    <img 
                                        id="main-profile-photo" 
                                        src="https://placehold.co/400x400/0f172a/38bdf8?text=Md.+Rakib+Hasan" 
                                        onerror="this.src='https://placehold.co/400x400/0f172a/38bdf8?text=MRH'"
                                        alt="Md. Rakib Hasan (Cyber MRH)" 
                                        class="w-full h-full object-cover rounded-2xl bg-slate-900"
                                    >
                                </div>
                                <!-- Admin-Only Photo Change Button -->
                                <label id="admin-photo-btn" for="photo-upload-input" class="hidden absolute -bottom-2 -right-2 px-3 py-1.5 rounded-xl bg-amber-400 hover:bg-amber-300 text-slate-950 font-bold text-xs shadow-lg cursor-pointer items-center gap-1.5 transition-transform active:scale-95" title="শুধুমাত্র অ্যাডমিন ছবি পরিবর্তন করতে পারবেন">
                                    <i class="fa-solid fa-camera"></i>
                                    <span>ছবি বদলান</span>
                                </label>
                                <input type="file" id="photo-upload-input" accept="image/*" class="hidden">
                            </div>
                            <span id="admin-photo-hint" class="hidden text-[11px] text-amber-400/80 mt-3">অ্যাডমিন মোড: ছবি আপডেট সক্রিয়</span>
                        </div>

                        <!-- Name & Captivating Hacker/Tech Narrative -->
                        <div class="flex-1 text-center md:text-left space-y-4">
                            <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-sky-500/10 border border-sky-500/30 text-sky-400 text-xs font-mono">
                                <i class="fa-solid fa-user-secret"></i>
                                <span>CYBER EXPLORER // WEB ARCHITECT</span>
                            </div>

                            <div>
                                <h1 class="text-3xl sm:text-4xl lg:text-5xl font-extrabold text-white tracking-tight">
                                    Md. Rakib Hasan<span class="text-sky-400 cursor-blink">_</span>
                                </h1>
                                <p class="text-lg sm:text-xl font-semibold text-emerald-400 mt-1 font-bengali">
                                    মোঃ রাকিব হাসান • Cyber MRH
                                </p>
                            </div>

                            <p class="text-slate-300 text-sm sm:text-base leading-relaxed">
                                কোডের প্রতিটি লাইনে লুকিয়ে থাকে নতুন সম্ভাবনা, আর সাইবার জগতের অদৃশ্য গোলকধাঁধায় লুকিয়ে থাকে জ্ঞান ও নিরাপত্তার রহস্য। প্রযুক্তির এই বিশাল দুনিয়ায় আমি একজন <strong class="text-sky-400">Web Developer</strong>, <strong class="text-emerald-400">White-Hat Security Researcher</strong> এবং <strong class="text-amber-300">Freelancer</strong>—যেখানে যুক্তি, সৃজনশীলতা আর কৌতূহল মিলেমিশে তৈরি করে নতুন কিছু।
                            </p>

                            <!-- Quick Page Jump Pills -->
                            <div class="pt-3 flex flex-wrap items-center justify-center md:justify-start gap-2.5">
                                <button type="button" onclick="switchPage('identity')" class="px-4 py-2.5 rounded-xl bg-sky-500 hover:bg-sky-400 text-slate-950 font-bold text-xs sm:text-sm transition-all flex items-center gap-2 shadow-lg shadow-sky-500/20 cursor-pointer">
                                    <i class="fa-solid fa-id-card"></i>
                                    <span>পরিচয় জানুন</span>
                                </button>
                                <button type="button" onclick="switchPage('academics')" class="px-4 py-2.5 rounded-xl bg-slate-900 hover:bg-slate-800 text-slate-200 border border-slate-700 text-xs sm:text-sm font-medium transition-all flex items-center gap-2 cursor-pointer">
                                    <i class="fa-solid fa-graduation-cap text-amber-400"></i>
                                    <span>একাডেমিকস</span>
                                </button>
                                <button type="button" onclick="switchPage('contact')" class="px-4 py-2.5 rounded-xl bg-slate-900 hover:bg-slate-800 text-slate-200 border border-slate-700 text-xs sm:text-sm font-medium transition-all flex items-center gap-2 cursor-pointer">
                                    <i class="fa-solid fa-paper-plane text-rose-400"></i>
                                    <span>কন্টাক্ট</span>
                                </button>
                            </div>
                        </div>
                    </div>

                    <!-- Bottom Helper Note for Three-Dot Menu -->
                    <div class="relative z-10 mt-8 pt-4 border-t border-slate-800/80 flex items-center justify-between text-xs text-slate-400">
                        <span><i class="fa-solid fa-circle-info text-sky-400 mr-1.5"></i>উপরের ডানপাশে থাকা <strong class="text-white">থ্রি-ডট (⋮)</strong> আইকনে ক্লিক করে প্রতিটি পেজ আলাদাভাবে দেখুন।</span>
                        <span class="font-mono text-slate-500 hidden sm:inline">v2.6 // SECURE</span>
                    </div>
                </div>
            </section>

            <!-- =============================================================== -->
            <!-- PAGE 2: IDENTITY PAGE (পরিচয়)                                   -->
            <!-- =============================================================== -->
            <section id="page-identity" class="page-section hidden space-y-6">
                <div class="cyber-card rounded-3xl p-6 sm:p-10 space-y-6">
                    <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                        <div class="flex items-center gap-3.5">
                            <div class="w-12 h-12 rounded-2xl bg-sky-500/15 text-sky-400 flex items-center justify-center text-xl">
                                <i class="fa-solid fa-id-card"></i>
                            </div>
                            <div>
                                <h2 class="text-2xl font-bold text-white">পরিচয় ও ঠিকানা</h2>
                                <p class="text-xs text-slate-400">Personal Identity & Location</p>
                            </div>
                        </div>
                        <button type="button" onclick="switchPage('home')" class="px-3 py-1.5 rounded-xl bg-slate-900 hover:bg-slate-800 text-xs text-slate-300 border border-slate-700 cursor-pointer">
                            <i class="fa-solid fa-arrow-left mr-1"></i> হোম
                        </button>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                        <div class="p-4 rounded-2xl bg-slate-900/80 border border-slate-800 space-y-1">
                            <span class="text-xs text-slate-400">পূর্ণ নাম (Full Name)</span>
                            <p class="text-base font-bold text-white">Md. Rakib Hasan (মোঃ রাকিব হাসান)</p>
                        </div>
                        <div class="p-4 rounded-2xl bg-slate-900/80 border border-slate-800 space-y-1">
                            <span class="text-xs text-slate-400">অন্য নামে পরিচিত (Known As)</span>
                            <p class="text-base font-bold text-sky-400">Cyber MRH</p>
                        </div>
                        <div class="p-4 rounded-2xl bg-slate-900/80 border border-slate-800 space-y-1">
                            <span class="text-xs text-slate-400">বর্তমান ঠিকানা (Area)</span>
                            <p class="text-base font-semibold text-slate-200">পাটকেলঘাটা (Patkelghata)</p>
                        </div>
                        <div class="p-4 rounded-2xl bg-slate-900/80 border border-slate-800 space-y-1">
                            <span class="text-xs text-slate-400">জেলা, বিভাগ ও দেশ</span>
                            <p class="text-base font-semibold text-slate-200">সাতক্ষীরা জেলা, খুলনা বিভাগ, বাংলাদেশ</p>
                        </div>
                    </div>

                    <div class="p-5 rounded-2xl bg-slate-900/60 border border-slate-800/90 space-y-2">
                        <h3 class="text-sm font-bold text-sky-400 uppercase tracking-wider">সংক্ষিপ্ত পরিচিতি (About Me)</h3>
                        <p class="text-sm sm:text-base text-slate-300 leading-relaxed">
                            আমি মোঃ রাকিব হাসান (Cyber MRH)। প্রযুক্তির প্রতি গভীর ভালোবাসা থেকে ওয়েব ডেভেলপমেন্ট, সাইবার সিকিউরিটি ও হোয়াইট-হ্যাট হ্যাকিং, লোগো ডিজাইন এবং আন্তর্জাতিক মার্কেটপ্লেস Upwork-এ ফ্রিল্যান্সিংয়ের সাথে যুক্ত আছি। প্রযুক্তির পাশাপাশি বাংলা ও বিশ্বসাহিত্য পাঠ, কবিতা লেখা এবং বিভিন্ন ভাষা শেখার প্রতি আমার বিশেষ আগ্রহ রয়েছে।
                        </p>
                    </div>
                </div>
            </section>

            <!-- =============================================================== -->
            <!-- PAGE 3: ACADEMICS PAGE (শিক্ষাগত যোগ্যতা)                       -->
            <!-- =============================================================== -->
            <section id="page-academics" class="page-section hidden space-y-6">
                <div class="cyber-card rounded-3xl p-6 sm:p-10 space-y-6">
                    <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                        <div class="flex items-center gap-3.5">
                            <div class="w-12 h-12 rounded-2xl bg-amber-500/15 text-amber-400 flex items-center justify-center text-xl">
                                <i class="fa-solid fa-graduation-cap"></i>
                            </div>
                            <div>
                                <h2 class="text-2xl font-bold text-white">শিক্ষাগত যোগ্যতা (Academics)</h2>
                                <p class="text-xs text-slate-400">Academic Records, Board Rolls & Registrations</p>
                            </div>
                        </div>
                        <button type="button" onclick="switchPage('home')" class="px-3 py-1.5 rounded-xl bg-slate-900 hover:bg-slate-800 text-xs text-slate-300 border border-slate-700 cursor-pointer">
                            <i class="fa-solid fa-arrow-left mr-1"></i> হোম
                        </button>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                        <!-- HSC -->
                        <div class="p-5 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-2.5">
                            <div class="flex flex-wrap justify-between items-center gap-1">
                                <span class="font-bold text-base text-amber-300">HSC (বিজ্ঞান বিভাগ / Science)</span>
                                <span class="text-xs px-2.5 py-0.5 rounded-full bg-emerald-500/15 text-emerald-400 font-bold border border-emerald-500/30">GPA: 3.42</span>
                            </div>
                            <p class="text-slate-200 font-medium">পাটকেলঘাটা হারুন-অর-রশিদ ডিগ্রি কলেজ</p>
                            <p class="text-xs text-slate-400">EIIN: ১১৯১০৪ (119104) • পাসের সন: ২০২৬</p>
                            <div class="pt-2.5 border-t border-slate-800 flex flex-wrap gap-4 text-xs text-slate-300 font-mono">
                                <span>রোল (Roll): <strong class="text-amber-300">520505</strong></span>
                                <span>রেজিস্ট্রেশন (Reg): <strong class="text-amber-300">2993306765</strong></span>
                            </div>
                        </div>

                        <!-- SSC -->
                        <div class="p-5 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-2.5">
                            <div class="flex flex-wrap justify-between items-center gap-1">
                                <span class="font-bold text-base text-sky-300">SSC (মাধ্যমিক)</span>
                                <span class="text-xs px-2.5 py-0.5 rounded-full bg-emerald-500/15 text-emerald-400 font-bold border border-emerald-500/30">GPA: 4.67</span>
                            </div>
                            <p class="text-slate-200 font-medium">নগরঘাটা কবি নজরুল বিদ্যাপীঠ</p>
                            <p class="text-xs text-slate-400">পাসের সন: ২০২৪</p>
                            <div class="pt-2.5 border-t border-slate-800 flex flex-wrap gap-4 text-xs text-slate-300 font-mono">
                                <span>রোল (Roll): <strong class="text-sky-300">137815</strong></span>
                                <span>রেজিস্ট্রেশন (Reg): <strong class="text-sky-300">2993306765</strong></span>
                            </div>
                        </div>

                        <!-- Computer Course -->
                        <div class="p-5 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-2.5">
                            <div class="flex flex-wrap justify-between items-center gap-1">
                                <span class="font-bold text-base text-cyan-300">৭৬ কম্পিউটার অফিস অ্যাপ্লিকেশন</span>
                                <span class="text-xs px-2.5 py-0.5 rounded-full bg-slate-800 text-slate-300 font-mono">জুলাই - ডিসেম্বর ২০২৫</span>
                            </div>
                            <p class="text-slate-200 font-medium">ইউনাইটেড কম্পিউটার ট্রেনিং ইনস্টিটিউট (কোড: ৩৪১৪২)</p>
                            <p class="text-xs text-slate-400">পোস্ট অফিস: বারিপুরা-০০০০, উপজেলা: তালা, জেলা: সাতক্ষীরা</p>
                            <div class="pt-2.5 border-t border-slate-800 flex flex-wrap gap-4 text-xs text-slate-300 font-mono">
                                <span>সার্টিফিকেট রেজিস্ট্রেশন (Reg): <strong class="text-cyan-300">2025210827</strong></span>
                            </div>
                        </div>

                        <!-- PSC -->
                        <div class="p-5 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-2.5">
                            <div class="flex flex-wrap justify-between items-center gap-1">
                                <span class="font-bold text-base text-purple-300">PSC (প্রাথমিক)</span>
                                <span class="text-xs px-2.5 py-0.5 rounded-full bg-emerald-500/15 text-emerald-400 font-bold border border-emerald-500/30">GPA: 3.58</span>
                            </div>
                            <p class="text-slate-200 font-medium">১৭৩ নং মিঠাবাড়ী উত্তর সরকারি প্রাথমিক বিদ্যালয়</p>
                            <p class="text-xs text-slate-400">প্রাথমিক শিক্ষা সমাপনী</p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- =============================================================== -->
            <!-- PAGE 4: SKILLS & FREELANCING PAGE (দক্ষতা)                      -->
            <!-- =============================================================== -->
            <section id="page-skills" class="page-section hidden space-y-6">
                <div class="cyber-card rounded-3xl p-6 sm:p-10 space-y-6">
                    <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                        <div class="flex items-center gap-3.5">
                            <div class="w-12 h-12 rounded-2xl bg-emerald-500/15 text-emerald-400 flex items-center justify-center text-xl">
                                <i class="fa-solid fa-code"></i>
                            </div>
                            <div>
                                <h2 class="text-2xl font-bold text-white">দক্ষতা ও ফ্রিল্যান্সিং (Skills)</h2>
                                <p class="text-xs text-slate-400">Web Development, Cyber Security, Design & Freelancing</p>
                            </div>
                        </div>
                        <button type="button" onclick="switchPage('home')" class="px-3 py-1.5 rounded-xl bg-slate-900 hover:bg-slate-800 text-xs text-slate-300 border border-slate-700 cursor-pointer">
                            <i class="fa-solid fa-arrow-left mr-1"></i> হোম
                        </button>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
                        <div class="p-4 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-1.5">
                            <div class="text-sky-400 text-lg"><i class="fa-solid fa-laptop-code"></i></div>
                            <h3 class="font-bold text-white text-sm">Web Development</h3>
                            <p class="text-xs text-slate-400">HTML5, CSS3, Tailwind CSS এবং JavaScript দিয়ে রেসপন্সিভ ও আধুনিক ওয়েবসাইট নির্মাণ।</p>
                        </div>
                        <div class="p-4 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-1.5">
                            <div class="text-emerald-400 text-lg"><i class="fa-solid fa-user-secret"></i></div>
                            <h3 class="font-bold text-white text-sm">White-Hat Hacking</h3>
                            <p class="text-xs text-slate-400">সাইবার সিকিউরিটি, সিস্টেম প্রোটেকশন এবং এথিক্যাল সিকিউরিটি রিসার্চ।</p>
                        </div>
                        <div class="p-4 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-1.5">
                            <div class="text-indigo-400 text-lg"><i class="fa-solid fa-briefcase"></i></div>
                            <h3 class="font-bold text-white text-sm">Upwork Freelancing</h3>
                            <p class="text-xs text-slate-400">আন্তর্জাতিক ক্লায়েন্টদের জন্য ডিজিটাল প্রজেক্ট এবং ফ্রিল্যান্স সার্ভিস পরিচালনা।</p>
                        </div>
                        <div class="p-4 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-1.5">
                            <div class="text-pink-400 text-lg"><i class="fa-solid fa-pen-nib"></i></div>
                            <h3 class="font-bold text-white text-sm">Logo & Brand Design</h3>
                            <p class="text-xs text-slate-400">ক্রিয়েটিভ লোগো ডিজাইন এবং ব্র্যান্ড আইডেন্টিটি তৈরি।</p>
                        </div>
                        <div class="p-4 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-1.5">
                            <div class="text-amber-400 text-lg"><i class="fa-solid fa-envelope-circle-check"></i></div>
                            <h3 class="font-bold text-white text-sm">Gmail & Account Setup</h3>
                            <p class="text-xs text-slate-400">প্রফেশনাল জিমেইল অ্যাকাউন্ট ক্রিয়েশন, রিকভারি এবং সিকিউরিটি কনফিগারেশন।</p>
                        </div>
                        <div class="p-4 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-1.5">
                            <div class="text-cyan-400 text-lg"><i class="fa-solid fa-file-word"></i></div>
                            <h3 class="font-bold text-white text-sm">Computer Office Application</h3>
                            <p class="text-xs text-slate-400">এমএস ওয়ার্ড, এক্সেল, পাওয়ারপয়েন্ট এবং অফিস ম্যানেজমেন্ট দক্ষতা।</p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- =============================================================== -->
            <!-- PAGE 5: HOBBIES & ASPIRATIONS PAGE (হবি ও ইচ্ছা)                 -->
            <!-- =============================================================== -->
            <section id="page-hobbies" class="page-section hidden space-y-6">
                <div class="cyber-card rounded-3xl p-6 sm:p-10 space-y-6">
                    <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                        <div class="flex items-center gap-3.5">
                            <div class="w-12 h-12 rounded-2xl bg-purple-500/15 text-purple-400 flex items-center justify-center text-xl">
                                <i class="fa-solid fa-feather-pointed"></i>
                            </div>
                            <div>
                                <h2 class="text-2xl font-bold text-white">হবি, সাহিত্য ও ইচ্ছা (Hobbies & Interests)</h2>
                                <p class="text-xs text-slate-400">Literature, Ghazals, Languages & Personal Passions</p>
                            </div>
                        </div>
                        <button type="button" onclick="switchPage('home')" class="px-3 py-1.5 rounded-xl bg-slate-900 hover:bg-slate-800 text-xs text-slate-300 border border-slate-700 cursor-pointer">
                            <i class="fa-solid fa-arrow-left mr-1"></i> হোম
                        </button>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                        <div class="p-5 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-2">
                            <h3 class="font-bold text-purple-300 flex items-center gap-2">
                                <i class="fa-solid fa-book-open"></i> কবিতা, বই ও সাহিত্য রিসার্চ
                            </h3>
                            <p class="text-slate-300 leading-relaxed">
                                নিজে কবিতা ও বই লেখা, বিভিন্ন বিষয়ে গভীর গবেষণা (Research) করা এবং রবীন্দ্রনাথ ঠাকুর ও কাজী নজরুল ইসলামের সাহিত্যপাঠ আমার অন্যতম প্রিয় শখ।
                            </p>
                        </div>

                        <div class="p-5 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-2">
                            <h3 class="font-bold text-amber-300 flex items-center gap-2">
                                <i class="fa-solid fa-music"></i> উর্দু ও ফার্সি গজল
                            </h3>
                            <p class="text-slate-300 leading-relaxed">
                                ক্লাসিক্যাল উর্দু (Urdu) এবং ফার্সি (Persian) গজল শোনা ও এর কাব্যিক অর্থ অনুধাবন করা।
                            </p>
                        </div>

                        <div class="p-5 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-2">
                            <h3 class="font-bold text-sky-300 flex items-center gap-2">
                                <i class="fa-solid fa-language"></i> বহুভাষা শিক্ষা ও চর্চা
                            </h3>
                            <p class="text-slate-300 leading-relaxed">
                                বাংলা ও ইংরেজির পাশাপাশি জাপানিজ (Japanese), চাইনিজ (Chinese), হিন্দি (Hindi), উর্দু এবং ফার্সি ভাষা শেখা ও জানার প্রতি প্রবল ইচ্ছা রয়েছে।
                            </p>
                        </div>

                        <div class="p-5 rounded-2xl bg-slate-900/85 border border-slate-800 space-y-2">
                            <h3 class="font-bold text-emerald-300 flex items-center gap-2">
                                <i class="fa-solid fa-futbol"></i> খেলাধুলা ও ভবিষ্যৎ লক্ষ্য
                            </h3>
                            <p class="text-slate-300 leading-relaxed">
                                ফুটবল খেলা দেখতে ভালোবাসি (Argentina Supporter 🇦🇷)। ভবিষ্যতে সাইবার সিকিউরিটি ও সফটওয়্যার ডেভেলপমেন্টে নিজেকে আরও দক্ষ করে তোলাই আমার মূল লক্ষ্য।
                            </p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- =============================================================== -->
            <!-- PAGE 6: CONTACT PAGE (কন্টাক্ট)                                 -->
            <!-- =============================================================== -->
            <section id="page-contact" class="page-section hidden space-y-6">
                <div class="cyber-card rounded-3xl p-6 sm:p-10 space-y-6">
                    <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                        <div class="flex items-center gap-3.5">
                            <div class="w-12 h-12 rounded-2xl bg-rose-500/15 text-rose-400 flex items-center justify-center text-xl">
                                <i class="fa-solid fa-address-book"></i>
                            </div>
                            <div>
                                <h2 class="text-2xl font-bold text-white">সরাসরি যোগাযোগ (Contact)</h2>
                                <p class="text-xs text-slate-400">Phone Numbers, Email & Direct Message</p>
                            </div>
                        </div>
                        <button type="button" onclick="switchPage('home')" class="px-3 py-1.5 rounded-xl bg-slate-900 hover:bg-slate-800 text-xs text-slate-300 border border-slate-700 cursor-pointer">
                            <i class="fa-solid fa-arrow-left mr-1"></i> হোম
                        </button>
                    </div>

                    <p class="text-sm text-slate-300">
                        যেকোনো ওয়েব ডেভেলপমেন্ট প্রজেক্ট, ফ্রিল্যান্সিং কাজ অথবা ব্যক্তিগত প্রয়োজনে নিচের মাধ্যমগুলোতে সরাসরি যোগাযোগ করতে পারেন। কার্ডে ক্লিক করলে নম্বর বা ইমেইল কপি হয়ে যাবে।
                    </p>

                    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                        <!-- Email -->
                        <button type="button" onclick="copyText('rakibsatkhira999@gmail.com', 'ইমেইল ঠিকানা কপি হয়েছে!')" class="p-5 rounded-2xl bg-slate-900/90 hover:bg-slate-800 border border-slate-700/80 hover:border-sky-500/40 text-left transition group cursor-pointer space-y-2">
                            <div class="flex items-center justify-between text-sky-400">
                                <i class="fa-solid fa-envelope text-lg"></i>
                                <i class="fa-regular fa-copy text-slate-400 group-hover:text-sky-400"></i>
                            </div>
                            <div class="text-xs text-slate-400">Email Address</div>
                            <div class="text-xs sm:text-sm font-semibold text-white break-all">rakibsatkhira999@gmail.com</div>
                        </button>

                        <!-- Primary Phone -->
                        <button type="button" onclick="copyText('01402142276', 'প্রাইমারি নম্বর কপি হয়েছে!')" class="p-5 rounded-2xl bg-slate-900/90 hover:bg-slate-800 border border-slate-700/80 hover:border-emerald-500/40 text-left transition group cursor-pointer space-y-2">
                            <div class="flex items-center justify-between text-emerald-400">
                                <i class="fa-solid fa-phone text-lg"></i>
                                <i class="fa-regular fa-copy text-slate-400 group-hover:text-emerald-400"></i>
                            </div>
                            <div class="text-xs text-slate-400">Phone (Primary)</div>
                            <div class="text-base font-bold text-emerald-400 font-mono">01402142276</div>
                        </button>

                        <!-- Secondary Phone -->
                        <button type="button" onclick="copyText('01572930960', 'সেকেন্ডারি নম্বর কপি হয়েছে!')" class="p-5 rounded-2xl bg-slate-900/90 hover:bg-slate-800 border border-slate-700/80 hover:border-amber-500/40 text-left transition group cursor-pointer space-y-2">
                            <div class="flex items-center justify-between text-amber-400">
                                <i class="fa-solid fa-mobile-screen text-lg"></i>
                                <i class="fa-regular fa-copy text-slate-400 group-hover:text-amber-400"></i>
                            </div>
                            <div class="text-xs text-slate-400">Phone (Secondary)</div>
                            <div class="text-base font-bold text-amber-400 font-mono">01572930960</div>
                        </button>
                    </div>

                    <div class="pt-2 flex flex-wrap gap-3">
                        <a href="mailto:rakibsatkhira999@gmail.com" class="px-5 py-3 rounded-xl bg-sky-500 hover:bg-sky-400 text-slate-950 font-bold text-xs sm:text-sm transition-all inline-flex items-center gap-2 shadow-lg shadow-sky-500/20">
                            <i class="fa-solid fa-paper-plane"></i>
                            <span>সরাসরি ইমেইল পাঠান (Send Email)</span>
                        </a>
                        <a href="tel:+8801402142276" class="px-5 py-3 rounded-xl bg-emerald-500/15 hover:bg-emerald-500/25 text-emerald-300 border border-emerald-500/30 font-bold text-xs sm:text-sm transition-all inline-flex items-center gap-2">
                            <i class="fa-solid fa-phone-volume"></i>
                            <span>সরাসরি কল করুন</span>
                        </a>
                    </div>
                </div>
            </section>

        </main>

        <!-- Custom Authorship Footer (Strictly formatted as requested) -->
        <footer class="border-t border-slate-800/80 bg-[#06080d] py-6 px-4 mt-12">
            <div class="max-w-6xl mx-auto flex flex-col sm:flex-row items-center justify-between gap-4 text-xs text-slate-400">
                <div class="flex flex-wrap items-center justify-center sm:justify-start gap-3 font-medium">
                    <span class="px-2.5 py-1 rounded bg-slate-900 border border-slate-800 text-sky-400">Creator: MD Rakib Hasan</span>
                    <span class="px-2.5 py-1 rounded bg-slate-900 border border-slate-800 text-slate-300">Writer: MD Rakib Hasan | Editor: MD Rakib Hasan</span>
                </div>
                <div class="text-slate-500">
                    &copy; 2026 <span class="text-slate-300 font-semibold">Cyber MRH</span>. All Rights Reserved.
                </div>
            </div>
        </footer>
    </div>

    <!-- Forgot Passcode & Phone OTP Modal -->
    <div id="forgot-modal" class="hidden fixed inset-0 z-50 bg-slate-950/80 backdrop-blur-md flex items-center justify-center p-4">
        <div class="glass-login rounded-2xl max-w-md w-full p-6 sm:p-7 relative space-y-5">
            <button type="button" id="close-forgot-modal" class="absolute top-4 right-4 w-8 h-8 rounded-lg bg-slate-900/80 text-slate-400 hover:text-white flex items-center justify-center cursor-pointer">
                <i class="fa-solid fa-xmark"></i>
            </button>

            <div class="text-center space-y-1">
                <div class="w-12 h-12 rounded-2xl bg-amber-500/15 text-amber-400 border border-amber-400/30 flex items-center justify-center text-xl mx-auto mb-2">
                    <i class="fa-solid fa-mobile-screen-button"></i>
                </div>
                <h3 class="text-lg font-bold text-white">ফোন নম্বর ভেরিফিকেশন (OTP Access)</h3>
                <p class="text-xs text-slate-400">আপনার ফোন নম্বর দিন। আপনার নম্বরে একটি ভেরিফিকেশন OTP যাবে এবং নম্বরটি অ্যাডমিন প্যানেলে সংরক্ষিত হবে।</p>
            </div>

            <!-- Step 1: Enter Phone Number -->
            <div id="otp-step-phone" class="space-y-4">
                <div>
                    <label for="visitor-phone-input" class="block text-xs font-medium text-slate-300 mb-1.5">আপনার মোবাইল নম্বর (Phone Number)</label>
                    <input 
                        type="tel" 
                        id="visitor-phone-input" 
                        placeholder="01XXXXXXXXX" 
                        class="w-full px-4 py-3 bg-slate-950/80 border border-slate-700 rounded-xl text-white placeholder-slate-500 text-sm font-mono focus:outline-none focus:border-amber-400"
                    >
                </div>
                <button type="button" id="send-otp-btn" class="w-full py-3 rounded-xl bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold text-sm transition-all cursor-pointer">
                    OTP কোড পাঠান (Send OTP)
                </button>
            </div>

            <!-- Step 2: Simulated SMS Notification + Enter OTP -->
            <div id="otp-step-verify" class="hidden space-y-4">
                <!-- Virtual SMS Banner showing OTP on the user's screen -->
                <div class="p-3 rounded-xl bg-emerald-500/10 border border-emerald-500/30 text-xs text-emerald-300 space-y-1">
                    <div class="flex items-center justify-between font-bold">
                        <span><i class="fa-solid fa-comment-sms mr-1"></i> SMS পাঠানো হয়েছে (<span id="display-target-phone"></span>)</span>
                        <span class="text-[10px] uppercase bg-emerald-500/20 px-1.5 py-0.5 rounded">Just Now</span>
                    </div>
                    <p>আপনার Cyber MRH ভেরিফিকেশন OTP কোড: <strong id="generated-otp-display" class="text-base font-mono text-amber-300 tracking-widest"></strong></p>
                </div>

                <div>
                    <label for="visitor-otp-input" class="block text-xs font-medium text-slate-300 mb-1.5">প্রাপ্ত ৬-সংখ্যার OTP কোডটি লিখুন</label>
                    <input 
                        type="text" 
                        id="visitor-otp-input" 
                        maxlength="6"
                        placeholder="6-Digit OTP" 
                        class="w-full px-4 py-3 bg-slate-950/80 border border-slate-700 rounded-xl text-white text-center tracking-[0.4em] font-mono text-base focus:outline-none focus:border-amber-400"
                    >
                </div>
                <button type="button" id="verify-otp-btn" class="w-full py-3 rounded-xl bg-emerald-500 hover:bg-emerald-400 text-slate-950 font-bold text-sm transition-all cursor-pointer">
                    OTP যাচাই করে প্রবেশ করুন (Verify & Enter)
                </button>
            </div>
        </div>
    </div>

    <!-- Custom Toast Notification Box (Replaces browser alert) -->
    <div id="toast-box" class="fixed bottom-5 right-5 z-50 transform translate-y-20 opacity-0 transition-all duration-300 pointer-events-none">
        <div class="px-4 py-3 rounded-xl bg-slate-900 border border-sky-500/40 text-white text-xs sm:text-sm font-medium shadow-2xl flex items-center gap-2.5">
            <i class="fa-solid fa-circle-check text-emerald-400"></i>
            <span id="toast-message">কপি সম্পন্ন হয়েছে!</span>
        </div>
    </div>

    <!-- ===================================================================== -->
    <!-- JAVASCRIPT: LAMP PHYSICS, AUDIO FEEDBACK, SECURITY & PROFILE LOGIC    -->
    <!-- ===================================================================== -->
    <script>
        // --- Configuration: Separate Visitor Passcodes vs Admin Master Passcode ---
        const VISITOR_PASSCODES = ['MRH2026', 'CYBERMRH', 'RAKIB26'];
        const ADMIN_PASSCODE = 'MRHADMIN999'; // শুধুমাত্র আপনি এই কোড দিলে ছবি এডিট অপশন পাবেন

        // --- DOM Elements ---
        const lampGate = document.getElementById('lamp-gate');
        const profileDashboard = document.getElementById('profile-dashboard');
        const cordHandle = document.getElementById('cord-handle');
        const cordLine = document.getElementById('cord-line');
        const cordKnob = document.getElementById('cord-knob');
        const cordPulse = document.getElementById('cord-pulse');
        const lampBulb = document.getElementById('lamp-bulb');
        const lightCone = document.getElementById('light-cone');
        const pullHint = document.getElementById('pull-hint');
        const loginCardWrapper = document.getElementById('login-card-wrapper');
        const loginCard = document.getElementById('login-card');
        const unlockForm = document.getElementById('unlock-form');
        const passcodeInput = document.getElementById('passcode-input');
        const togglePassVis = document.getElementById('toggle-pass-vis');
        const errorMsg = document.getElementById('error-msg');
        const lockBtn = document.getElementById('lock-btn');
        const photoUploadInput = document.getElementById('photo-upload-input');
        const mainProfilePhoto = document.getElementById('main-profile-photo');
        const defaultStyledAvatar = document.getElementById('default-styled-avatar');
        const adminPhotoBtn = document.getElementById('admin-photo-btn');
        const adminPhotoHint = document.getElementById('admin-photo-hint');
        const adminLogsPanel = document.getElementById('admin-logs-panel');
        const visitorLogsContainer = document.getElementById('visitor-logs-container');
        const accessBadge = document.getElementById('access-badge');
        const threeDotBtn = document.getElementById('three-dot-btn');
        const threeDotDropdown = document.getElementById('three-dot-dropdown');
        const navMenuContainer = document.getElementById('nav-menu-container');
        const currentPageLabel = document.getElementById('current-page-label');
        let isLampOn = false;
        let isDragging = false;
        let startY = 0;
        let currentPull = 0;
        const baseCordY = 205;
        const maxPullDistance = 65;
        const triggerThreshold = 32;

        // --- Multi-Page Navigation & Three-Dot Dropdown Logic ---
        const PAGE_META = {
            home: { title: 'হোম (Cyber Front)', icon: 'fa-terminal' },
            identity: { title: 'পরিচয় (Identity)', icon: 'fa-id-card' },
            academics: { title: 'একাডেমিকস (Academics)', icon: 'fa-graduation-cap' },
            skills: { title: 'দক্ষতা (Skills)', icon: 'fa-code' },
            hobbies: { title: 'হবি ও ইচ্ছা (Hobbies)', icon: 'fa-feather-pointed' },
            contact: { title: 'কন্টাক্ট (Contact)', icon: 'fa-address-book' }
        };

        threeDotBtn.addEventListener('click', (e) => {
            e.stopPropagation();
            threeDotDropdown.classList.toggle('hidden');
        });

        // Close dropdown when clicking outside
        document.addEventListener('click', (e) => {
            if (!navMenuContainer.contains(e.target)) {
                threeDotDropdown.classList.add('hidden');
            }
        });

        window.switchPage = function(pageKey) {
            // Hide all pages
            document.querySelectorAll('.page-section').forEach(sec => {
                sec.classList.add('hidden');
                sec.classList.remove('page-enter');
            });

            // Show target page with animation
            const targetPage = document.getElementById(`page-${pageKey}`);
            if (targetPage) {
                targetPage.classList.remove('hidden');
                void targetPage.offsetWidth;
                targetPage.classList.add('page-enter');
            }

            // Update active state in three-dot menu
            document.querySelectorAll('.nav-item').forEach(btn => {
                if (btn.dataset.nav === pageKey) {
                    btn.classList.add('text-sky-400', 'bg-sky-500/10', 'font-semibold');
                    btn.classList.remove('text-slate-300');
                } else {
                    btn.classList.remove('text-sky-400', 'bg-sky-500/10', 'font-semibold');
                    btn.classList.add('text-slate-300');
                }
            });

            // Update top bar current page pill
            const meta = PAGE_META[pageKey] || PAGE_META.home;
            currentPageLabel.innerHTML = `<i class="fa-solid ${meta.icon} text-[10px]"></i><span>${meta.title}</span>`;

            // Close dropdown & scroll top
            threeDotDropdown.classList.add('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        };

        // --- Sound Effects using Tone.js (Synthesized, no external MP3 needed) ---
        function playSwitchSound(turnOn) {
            try {
                if (typeof Tone !== 'undefined') {
                    if (Tone.context.state !== 'running') {
                        Tone.start();
                    }
                    const synth = new Tone.MembraneSynth({
                        pitchDecay: 0.01,
                        octaves: 2,
                        envelope: { attack: 0.001, decay: 0.08, sustain: 0 }
                    }).toDestination();
                    synth.volume.value = -12;
                    synth.triggerAttackRelease(turnOn ? 'G4' : 'C4', '32n');
                }
            } catch (e) {
                // Ignore audio errors if blocked by browser autoplay policy
            }
        }

        function playUnlockChime() {
            try {
                if (typeof Tone !== 'undefined') {
                    const synth = new Tone.PolySynth(Tone.Synth).toDestination();
                    synth.volume.value = -14;
                    const now = Tone.now();
                    synth.triggerAttackRelease('C5', '16n', now);
                    synth.triggerAttackRelease('E5', '16n', now + 0.08);
                    synth.triggerAttackRelease('G5', '8n', now + 0.16);
                }
            } catch (e) {}
        }

        // --- Toggle Lamp Light & Login Card ---
        function setLampState(state) {
            isLampOn = state;
            playSwitchSound(isLampOn);

            if (isLampOn) {
                // Turn ON Bulb & Warm Light Cone
                lampBulb.setAttribute('fill', 'url(#bulbOnGrad)');
                lampBulb.setAttribute('stroke', '#fde047');
                lampBulb.style.filter = 'drop-shadow(0 0 18px rgba(251, 191, 36, 0.95))';
                
                lightCone.classList.remove('opacity-0', 'scale-y-90');
                lightCone.classList.add('opacity-100', 'scale-y-100');
                // Smooth transition to Unlocked Profile Dashboard
                lampGate.classList.add('opacity-0', 'scale-95');
                setTimeout(() => {
                    lampGate.classList.add('hidden');
                    profileDashboard.classList.remove('hidden');
                    switchPage('home');
                    void profileDashboard.offsetWidth;
                    profileDashboard.classList.remove('opacity-0');
                    window.scrollTo({ top: 0, behavior: 'smooth' });
                }, 500);
            } else {
                // Turn OFF Bulb & Light Cone
                lampBulb.setAttribute('fill', '#1e293b');
                lampBulb.setAttribute('stroke', '#334155');
                lampBulb.style.filter = 'none';

                lightCone.classList.add('opacity-0', 'scale-y-90');
                lightCone.classList.remove('opacity-100', 'scale-y-100');

                // Show hint again
                pullHint.classList.remove('opacity-0');
                cordPulse.style.display = 'block';

                // Hide Login Form
                loginCardWrapper.classList.add('opacity-0', 'translate-y-8', 'pointer-events-none');
                loginCardWrapper.classList.remove('opacity-100', 'translate-y-0', 'pointer-events-auto');
            }
        }

        // --- Spring Return Animation for Cord ---
        function springCordBack() {
            const startPull = currentPull;
            const duration = 350;
            const startTime = performance.now();

            function animateSpring(time) {
                const elapsed = time - startTime;
                const progress = Math.min(elapsed / duration, 1);
                // Elastic ease-out formula
                const easeOutElastic = progress === 1 ? 1 : 1 - Math.pow(2, -10 * progress) * Math.cos((progress * 10 - 0.75) * ((2 * Math.PI) / 3));
                
                const currentOffset = startPull * (1 - easeOutElastic);
                updateCordVisual(currentOffset);

                if (progress < 1) {
                    requestAnimationFrame(animateSpring);
                } else {
                    currentPull = 0;
                    updateCordVisual(0);
                }
            }
            requestAnimationFrame(animateSpring);
        }

        function updateCordVisual(pullY) {
            const newY = baseCordY + pullY;
            cordLine.setAttribute('y2', newY);
            cordKnob.setAttribute('transform', `translate(204, ${newY})`);
        }

        // --- Pointer Events (Supports Mouse Drag, Touch Pull, and Direct Click) ---
        let pointerDownTime = 0;
        let hasMovedSignificantly = false;

        cordHandle.addEventListener('pointerdown', (e) => {
            isDragging = true;
            hasMovedSignificantly = false;
            startY = e.clientY;
            pointerDownTime = Date.now();
            cordHandle.setPointerCapture(e.pointerId);
        });

        window.addEventListener('pointermove', (e) => {
            if (!isDragging) return;
            const deltaY = e.clientY - startY;
            if (Math.abs(deltaY) > 5) {
                hasMovedSignificantly = true;
            }
            // Clamp pull distance between 0 and maxPullDistance
            currentPull = Math.max(0, Math.min(deltaY * 0.85, maxPullDistance));
            updateCordVisual(currentPull);
        });

        window.addEventListener('pointerup', (e) => {
            if (!isDragging) return;
            isDragging = false;

            const clickDuration = Date.now() - pointerDownTime;

            // Trigger lamp toggle if dragged past threshold OR clicked quickly
            if (currentPull >= triggerThreshold || (!hasMovedSignificantly && clickDuration < 300)) {
                // Visual quick dip if it was just a tap/click
                if (currentPull < 15) {
                    currentPull = 26;
                    updateCordVisual(currentPull);
                }
                setLampState(!isLampOn);
            }
            
            springCordBack();
        });

        window.addEventListener('pointercancel', () => {
            if (isDragging) {
                isDragging = false;
                springCordBack();
            }
        });

        // --- Toggle Password Visibility ---
        togglePassVis.addEventListener('click', () => {
            const isPassword = passcodeInput.type === 'password';
            passcodeInput.type = isPassword ? 'text' : 'password';
            togglePassVis.innerHTML = isPassword 
                ? '<i class="fa-solid fa-eye-slash text-sm"></i>' 
                : '<i class="fa-solid fa-eye text-sm"></i>';
        });

        // --- Form Submission & Unlock Transition (Visitor vs Admin Access Control) ---
        unlockForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const enteredCode = passcodeInput.value.trim().toUpperCase();
            const isAdmin = enteredCode === ADMIN_PASSCODE;
            const isVisitor = VISITOR_PASSCODES.includes(enteredCode);

            if (isAdmin || isVisitor) {
                errorMsg.classList.add('hidden');
                unlockDashboard(isAdmin);
            } else {
                // Show error & shake card
                errorMsg.classList.remove('hidden');
                loginCard.classList.remove('animate-shake');
                void loginCard.offsetWidth;
                loginCard.classList.add('animate-shake');
            }
        });

        // --- Lock Profile Again ---
        lockBtn.addEventListener('click', () => {
            profileDashboard.classList.add('opacity-0');
            setTimeout(() => {
                profileDashboard.classList.add('hidden');
                lampGate.classList.remove('hidden', 'scale-95');
                void lampGate.offsetWidth;
                lampGate.classList.remove('opacity-0');
                
                // Reset passcode input, hide admin controls, and turn off lamp
                passcodeInput.value = '';
                errorMsg.classList.add('hidden');
                adminPhotoBtn.classList.add('hidden');
                adminPhotoBtn.classList.remove('flex');
                adminPhotoHint.classList.add('hidden');
                adminLogsPanel.classList.add('hidden');
                setLampState(false);
            }, 500);
        });

        // --- Live Profile Photo Upload Preview & Local Save (Admin Only) ---
        photoUploadInput.addEventListener('change', (e) => {
            const file = e.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = function(event) {
                const dataUrl = event.target.result;
                mainProfilePhoto.src = dataUrl;
                mainProfilePhoto.classList.remove('hidden');
                defaultStyledAvatar.classList.add('hidden');
                try {
                    localStorage.setItem('cyber_mrh_profile_photo', dataUrl);
                } catch (err) {}
                showToast('নতুন প্রোফাইল ছবি সেট ও সংরক্ষণ করা হয়েছে!');
            };
            reader.readAsDataURL(file);
        });

        // --- Copy to Clipboard Utility (Using execCommand for iFrame compatibility) ---
        window.copyText = function(text, message) {
            const tempInput = document.createElement('textarea');
            tempInput.value = text;
            document.body.appendChild(tempInput);
            tempInput.select();
            try {
                document.execCommand('copy');
                showToast(message || 'কপি করা হয়েছে!');
            } catch (err) {
                showToast('কপি করা সম্ভব হয়নি');
            }
            document.body.removeChild(tempInput);
        };

        // --- Custom Toast Message Function ---
        let toastTimeout;
        function showToast(msg) {
            const toastBox = document.getElementById('toast-box');
            const toastMessage = document.getElementById('toast-message');
            toastMessage.textContent = msg;
            
            toastBox.classList.remove('translate-y-20', 'opacity-0');
            clearTimeout(toastTimeout);
            toastTimeout = setTimeout(() => {
                toastBox.classList.add('translate-y-20', 'opacity-0');
            }, 2800);
        }
    </script>
</body>
</html>
```
