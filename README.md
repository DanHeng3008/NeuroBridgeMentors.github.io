<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NeuroBridge Mentors | Compassionate Tutoring with Unix3</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Lexend (ADHD & Dyslexia friendly) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Lexend:wght@300;400;500;600;700&family=Open+Dyslexic&display=swap" rel="stylesheet">

    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        brand: {
                            bg: 'var(--bg-main)',
                            card: 'var(--bg-card)',
                            teal: '#2E5A5A',
                            tealLight: 'var(--bg-teal-light)',
                            tealHover: '#1E3E3E',
                            mint: '#9CD2C0',
                            paleYellow: '#F9F6C6',
                            slate: '#435B66',
                            slateLight: 'var(--bg-slate-light)',
                            text: 'var(--text-main)',
                            muted: 'var(--text-muted)'
                        }
                    },
                    fontFamily: {
                        sans: ['Lexend', 'sans-serif'],
                        dyslexic: ['OpenDyslexic', 'Lexend', 'sans-serif']
                    }
                }
            }
        }
    </script>

    <style>
        /* CSS Variables mapped to Unix3's muted color palette */
        :root {
            --bg-main: #F4F8F6;
            --bg-card: #FFFFFF;
            --bg-teal-light: #E5F2EE;
            --bg-slate-light: #EBF1F2;
            --bg-yellow-light: #FAF9E4;
            --text-main: #1C2424;
            --text-muted: #4A5B5C;
            --border-color: #D3E2DD;
            --input-bg: #FFFFFF;
            --header-bg: rgba(244, 248, 246, 0.95);
        }

        /* Calm Dim Mode - Non-glare dark slate scheme matching Unix3's background */
        body.calm-mode {
            --bg-main: #121A1A;
            --bg-card: #1A2424;
            --bg-teal-light: #1E3331;
            --bg-slate-light: #202D30;
            --bg-yellow-light: #26291C;
            --text-main: #ECF5F3;
            --text-muted: #A0B5B2;
            --border-color: #2D3E3C;
            --input-bg: #151D1D;
            --header-bg: rgba(18, 26, 26, 0.96);
            background-color: var(--bg-main) !important;
            color: var(--text-main) !important;
        }

        body {
            background-color: var(--bg-main);
            color: var(--text-main);
            line-height: 1.7;
            letter-spacing: 0.015em;
            transition: background-color 0.25s ease, color 0.25s ease;
        }

        /* Dyslexia Mode Spacing */
        .dyslexic-mode {
            letter-spacing: 0.08em !important;
            word-spacing: 0.25em !important;
            line-height: 2.1 !important;
        }

        /* Reading Focus Guide Bar */
        .focus-guide {
            position: fixed;
            pointer-events: none;
            left: 0;
            width: 100%;
            height: 48px;
            background: rgba(156, 210, 192, 0.2);
            border-top: 2px solid rgba(46, 90, 90, 0.5);
            border-bottom: 2px solid rgba(46, 90, 90, 0.5);
            z-index: 9999;
            transform: translateY(-50%);
            display: none;
            transition: top 0.05s ease-out;
        }

        /* Floating animation for Unix3 stickers */
        @keyframes float-gentle {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-6px) rotate(1.5deg); }
        }

        .animate-float {
            animation: float-gentle 4.5s ease-in-out infinite;
        }

        /* Unix3 Crop / Sticker Styles */
        .unix3-crop-main {
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: 80% 12%; /* Focus on top-right Unix3 pose */
        }

        .unix3-sticker-left {
            width: 110px;
            height: 110px;
            object-fit: cover;
            object-position: 12% 10%; /* Focus on top-left Unix3 pose */
            filter: drop-shadow(0px 4px 10px rgba(0,0,0,0.15));
        }

        .unix3-sticker-bottom {
            width: 120px;
            height: 120px;
            object-fit: cover;
            object-position: 48% 90%; /* Focus on bottom Unix3 pose */
            filter: drop-shadow(0px 4px 10px rgba(0,0,0,0.15));
        }

        /* Calm Mode Select Option Fix */
        body.calm-mode select option {
            background-color: #1A2424;
            color: #ECF5F3;
        }
    </style>
</head>
<body class="font-sans antialiased">

    <!-- Reading Focus Guide Ruler -->
    <div id="focusGuide" class="focus-guide"></div>

    <!-- Navigation Bar & Accessibility Toolbar -->
    <header class="sticky top-0 z-50 border-b border-gray-200/50 shadow-xs transition-colors duration-200" style="background-color: var(--header-bg);">
        <!-- Accessibility Quick Toolbar -->
        <div class="border-b border-gray-200/40 px-4 py-1.5 text-xs" style="background-color: var(--bg-slate-light); color: var(--text-muted);">
            <div class="max-w-7xl mx-auto flex flex-wrap justify-between items-center gap-2">
                <div class="flex items-center gap-2 font-medium">
                    <i class="fa-solid fa-universal-access text-brand-teal text-sm"></i>
                    <span>Sensory & Reading Tools:</span>
                </div>
                <div class="flex items-center gap-2.5 flex-wrap">
                    <button id="toggleDyslexia" onclick="toggleDyslexiaFont()" class="px-2.5 py-1 rounded bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-600 font-medium transition flex items-center gap-1.5 shadow-xs">
                        <i class="fa-solid fa-font"></i> <span>Dyslexia Spacing</span>
                    </button>
                    <button id="toggleFocusGuide" onclick="toggleFocusGuideMode()" class="px-2.5 py-1 rounded bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-600 font-medium transition flex items-center gap-1.5 shadow-xs">
                        <i class="fa-solid fa-grip-lines"></i> <span>Reading Ruler</span>
                    </button>
                    <button id="toggleContrast" onclick="toggleCalmMode()" class="px-2.5 py-1 rounded bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-600 font-medium transition flex items-center gap-1.5 shadow-xs">
                        <i class="fa-solid fa-moon"></i> <span>Calm Dim Mode</span>
                    </button>
                    <div class="flex items-center gap-1 bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-600 rounded px-1.5 py-0.5">
                        <span class="text-[11px] font-semibold" style="color: var(--text-muted);">Font:</span>
                        <button onclick="changeFontSize(-1)" class="px-1.5 text-xs font-bold hover:text-brand-teal">A-</button>
                        <button onclick="resetFontSize()" class="px-1 text-[11px] hover:text-brand-teal">Reset</button>
                        <button onclick="changeFontSize(1)" class="px-1.5 text-xs font-bold hover:text-brand-teal">A+</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Main Navigation -->
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-20">
                <!-- Brand Logo & Unix3 Name -->
                <a href="#" class="flex items-center gap-3 group">
                    <div class="w-11 h-11 rounded-2xl bg-brand-teal flex items-center justify-center text-brand-paleYellow text-xl shadow-md group-hover:scale-105 transition-transform">
                        <i class="fa-solid fa-feather-pointed"></i>
                    </div>
                    <div>
                        <span class="text-xl font-bold tracking-tight block" style="color: var(--text-main);">NeuroBridge</span>
                        <span class="text-xs font-medium text-brand-teal block -mt-1 tracking-wider uppercase">Mentors & Learning</span>
                    </div>
                </a>

                <!-- Nav Links -->
                <nav class="hidden md:flex items-center gap-6 font-medium text-sm">
                    <a href="#about" class="hover:text-brand-teal transition" style="color: var(--text-main);">About Us</a>
                    <a href="#mascot" class="hover:text-brand-teal transition" style="color: var(--text-main);">Meet Unix3</a>
                    <a href="#requirements" class="hover:text-brand-teal transition" style="color: var(--text-main);">Volunteer Info</a>
                    <a href="#volunteer-form" class="hover:text-brand-teal transition" style="color: var(--text-main);">Volunteer Now</a>
                    <a href="#student-form" class="hover:text-brand-teal transition" style="color: var(--text-main);">Request Help</a>
                    <a href="#faq" class="hover:text-brand-teal transition" style="color: var(--text-main);">FAQ</a>
                </nav>

                <!-- Action CTA -->
                <div class="flex items-center gap-3">
                    <a href="#student-form" class="hidden sm:inline-flex items-center gap-2 bg-brand-teal hover:bg-brand-tealHover text-white px-4 py-2.5 rounded-xl font-medium text-sm transition shadow-sm">
                        <i class="fa-solid fa-heart"></i> Get Personal Help
                    </a>
                    <button onclick="toggleMobileMenu()" class="md:hidden p-2 rounded-lg hover:bg-gray-100 dark:hover:bg-gray-800" style="color: var(--text-main);">
                        <i class="fa-solid fa-bars text-xl"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Drawer -->
        <div id="mobileMenu" class="hidden md:hidden border-t border-gray-200/50 px-4 pt-3 pb-6 space-y-3" style="background-color: var(--bg-card);">
            <a href="#about" onclick="toggleMobileMenu()" class="block py-2 font-medium" style="color: var(--text-main);">About Us</a>
            <a href="#mascot" onclick="toggleMobileMenu()" class="block py-2 font-medium" style="color: var(--text-main);">Meet Unix3</a>
            <a href="#requirements" onclick="toggleMobileMenu()" class="block py-2 font-medium" style="color: var(--text-main);">Volunteer Guidelines</a>
            <a href="#volunteer-form" onclick="toggleMobileMenu()" class="block py-2 font-medium text-brand-teal"><i class="fa-solid fa-hand-holding-heart mr-2"></i>Volunteer Now</a>
            <a href="#student-form" onclick="toggleMobileMenu()" class="block py-2 font-medium text-brand-slate"><i class="fa-solid fa-child mr-2"></i>Request Personal Tutoring</a>
            <a href="#faq" onclick="toggleMobileMenu()" class="block py-2 font-medium" style="color: var(--text-main);">FAQ</a>
        </div>
    </header>

    <main id="main-content">
        <!-- Hero Section -->
        <section class="relative py-12 md:py-16 overflow-hidden border-b border-gray-200/50" style="background: linear-gradient(180deg, var(--bg-teal-light) 0%, var(--bg-main) 100%);">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 items-center">
                    
                    <!-- Left Hero Text -->
                    <div class="lg:col-span-7 space-y-6 text-center lg:text-left">
                        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full border border-brand-teal/30 text-brand-teal text-xs font-semibold tracking-wide uppercase" style="background-color: var(--bg-yellow-light);">
                            <i class="fa-solid fa-shield-heart text-sm"></i> Safe, Gentle & Patient 1-on-1 Tutoring
                        </div>
                        
                        <h1 class="text-3xl sm:text-4xl md:text-5xl font-extrabold tracking-tight leading-tight" style="color: var(--text-main);">
                            Every mind learns differently. <br class="hidden sm:inline">
                            <span class="text-brand-teal">We make sure no child feels left behind.</span>
                        </h1>

                        <p class="text-base sm:text-lg max-w-2xl mx-auto lg:mx-0 font-normal leading-relaxed" style="color: var(--text-muted);">
                            Helping non-neurotypical children who struggle with schoolwork, social cues, or creative skills through patient personal tutoring tailored specifically to how their mind works.
                        </p>

                        <!-- Hero Action Buttons -->
                        <div class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start pt-2">
                            <a href="#student-form" class="px-6 py-4 rounded-xl bg-brand-teal hover:bg-brand-tealHover text-white font-semibold text-center transition shadow-md flex items-center justify-center gap-2">
                                <i class="fa-solid fa-heart"></i>
                                <span>If You Are In Need Of Our Help</span>
                            </a>
                            <a href="#volunteer-form" class="px-6 py-4 rounded-xl border-2 border-brand-teal/30 font-semibold text-center transition shadow-xs flex items-center justify-center gap-2" style="background-color: var(--bg-card); color: var(--text-main);">
                                <i class="fa-solid fa-hand-holding-heart text-brand-teal"></i>
                                <span>Volunteer Now</span>
                            </a>
                        </div>
                    </div>

                    <!-- Right Hero Spotlight: Main Unix3 Introduction Card (Top-Right Pose) -->
                    <div class="lg:col-span-5" id="mascot">
                        <div class="p-5 rounded-3xl border border-brand-teal/30 shadow-lg text-center relative overflow-hidden" style="background-color: var(--bg-card);">
                            <div class="absolute top-3 right-4 bg-brand-teal text-brand-paleYellow text-[11px] font-bold px-3 py-1 rounded-full shadow-xs">
                                Meet Unix3
                            </div>

                            <div class="relative w-full h-72 rounded-2xl overflow-hidden border border-gray-200/60 bg-black flex items-center justify-center shadow-inner">
                                <!-- Top-Right Drawing Pose as Main Mascot Introduction -->
                                <img src="Unix3.jpg" alt="Unix3 Mascot Sitting Calmly with Wings Spread" class="unix3-crop-main animate-float">
                            </div>

                            <div class="mt-4 text-left">
                                <h3 class="text-lg font-bold flex items-center gap-2" style="color: var(--text-main);">
                                    <i class="fa-solid fa-seedling text-brand-teal"></i> Unix3 - Our Calm Companion
                                </h3>
                                <p class="text-xs leading-relaxed mt-1" style="color: var(--text-muted);">
                                    Unix3 is our gentle mascot, designed with soft pale yellow and cool mint tones to bring a comforting presence to children as they learn at their own pace.
                                </p>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- Mission & Purpose Section -->
        <section id="about" class="py-16 border-b border-gray-200/50" style="background-color: var(--bg-card);">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center max-w-3xl mx-auto mb-12">
                    <span class="text-xs font-bold text-brand-teal uppercase tracking-widest block mb-2">Our Purpose & Focus</span>
                    <h2 class="text-2xl sm:text-3xl font-bold" style="color: var(--text-main);">Why NeuroBridge Mentors Exists</h2>
                    <p class="mt-3 text-sm sm:text-base leading-relaxed" style="color: var(--text-muted);">
                        Neurodivergency is often overlooked in standardized classrooms, leaving bright children feeling isolated. We exist to build a compassionate bridge to learning.
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                    <div class="p-6 rounded-2xl border border-gray-200/80 shadow-xs flex flex-col justify-between" style="background-color: var(--bg-main);">
                        <div>
                            <div class="w-12 h-12 rounded-xl text-brand-teal flex items-center justify-center text-xl font-bold mb-4" style="background-color: var(--bg-teal-light);">
                                <i class="fa-solid fa-brain"></i>
                            </div>
                            <h3 class="text-lg font-bold mb-2" style="color: var(--text-main);">Tailored Academics</h3>
                            <p class="text-xs sm:text-sm leading-relaxed" style="color: var(--text-muted);">
                                Standard school systems rely on speed. We adapt teaching techniques to fit ADHD, Dyslexia, Autism, and individual processing styles.
                            </p>
                        </div>
                        <div class="mt-6 rounded-xl overflow-hidden h-36 border border-gray-200/50">
                            <img src="https://images.unsplash.com/photo-1503676260728-1c00da094a0b?auto=format&fit=crop&w=600&q=80" alt="Child studying peacefully" class="w-full h-full object-cover">
                        </div>
                    </div>

                    <div class="p-6 rounded-2xl border border-gray-200/80 shadow-xs flex flex-col justify-between" style="background-color: var(--bg-main);">
                        <div>
                            <div class="w-12 h-12 rounded-xl text-brand-teal flex items-center justify-center text-xl font-bold mb-4" style="background-color: var(--bg-teal-light);">
                                <i class="fa-solid fa-comments"></i>
                            </div>
                            <h3 class="text-lg font-bold mb-2" style="color: var(--text-main);">Social & Communication</h3>
                            <p class="text-xs sm:text-sm leading-relaxed" style="color: var(--text-muted);">
                                Guidance in understanding social cues, conversation, emotion regulation, and self-advocacy without pressure.
                            </p>
                        </div>
                        <div class="mt-6 rounded-xl overflow-hidden h-36 border border-gray-200/50">
                            <img src="https://images.unsplash.com/photo-1531545514256-b1400bc00f31?auto=format&fit=crop&w=600&q=80" alt="Two kids interacting playfully" class="w-full h-full object-cover">
                        </div>
                    </div>

                    <div class="p-6 rounded-2xl border border-gray-200/80 shadow-xs flex flex-col justify-between" style="background-color: var(--bg-main);">
                        <div>
                            <div class="w-12 h-12 rounded-xl text-brand-teal flex items-center justify-center text-xl font-bold mb-4" style="background-color: var(--bg-teal-light);">
                                <i class="fa-solid fa-palette"></i>
                            </div>
                            <h3 class="text-lg font-bold mb-2" style="color: var(--text-main);">Creative Arts & Hobbies</h3>
                            <p class="text-xs sm:text-sm leading-relaxed" style="color: var(--text-muted);">
                                From liberal arts and drawing to coding or music, we build confidence through topics children naturally love.
                            </p>
                        </div>
                        <div class="mt-6 rounded-xl overflow-hidden h-36 border border-gray-200/50">
                            <img src="https://images.unsplash.com/photo-1513364776144-60967b0f800f?auto=format&fit=crop&w=600&q=80" alt="Child painting with soft colors" class="w-full h-full object-cover">
                        </div>
                    </div>
                </div>

                <!-- Goal Highlight Box -->
                <div class="mt-12 p-6 sm:p-8 rounded-3xl border border-brand-teal/30 flex flex-col sm:flex-row items-center gap-6" style="background: linear-gradient(135deg, var(--bg-teal-light) 0%, var(--bg-yellow-light) 100%);">
                    <div class="w-14 h-14 rounded-2xl bg-white text-brand-teal flex-shrink-0 flex items-center justify-center text-2xl shadow-sm">
                        <i class="fa-solid fa-quote-left"></i>
                    </div>
                    <div>
                        <h4 class="text-base font-bold text-brand-teal mb-1">Our Core Goal</h4>
                        <p class="font-medium text-sm sm:text-base leading-relaxed" style="color: var(--text-main);">
                            "Help non-neurotypical kids who struggle with learning academically and with skills by giving them personal tutoring for a period of time because neurodivergency is a very disregarded topic and many children struggle with fitting in because of this."
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Volunteer Guidelines with Unix3 Top-Left Pose Sticker -->
        <section id="requirements" class="py-16 border-b border-gray-200/50 relative overflow-hidden" style="background-color: var(--bg-main);">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative">
                
                <div class="flex flex-col md:flex-row items-center justify-between gap-6 mb-12">
                    <div class="max-w-2xl">
                        <span class="text-xs font-bold text-brand-teal uppercase tracking-widest block mb-2">Volunteer Portal</span>
                        <h2 class="text-2xl sm:text-3xl font-bold" style="color: var(--text-main);">Volunteer Requirements & Guidelines</h2>
                        <p class="mt-2 text-sm sm:text-base" style="color: var(--text-muted);">We welcome patient, empathetic individuals willing to teach academic, creative, or social skills.</p>
                    </div>

                    <!-- Unix3 Top-Left Sticker Element Floating Next to Guidelines Header -->
                    <div class="flex items-center gap-3 p-3 rounded-2xl border border-brand-teal/30 shadow-sm animate-float" style="background-color: var(--bg-card);">
                        <div class="w-20 h-20 rounded-xl overflow-hidden bg-black flex items-center justify-center border border-gray-200/40">
                            <img src="Unix3.jpg" alt="Unix3 Sticker Waving" class="unix3-sticker-left">
                        </div>
                        <div class="text-xs">
                            <span class="font-bold block text-brand-teal">Unix3 Says:</span>
                            <span style="color: var(--text-muted);">"No experience? <br>That's okay! We guide you."</span>
                        </div>
                    </div>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                    <div class="p-6 rounded-2xl border border-gray-200/80 shadow-xs flex flex-col justify-between" style="background-color: var(--bg-card);">
                        <div>
                            <span class="w-8 h-8 rounded-full text-brand-teal text-xs font-bold flex items-center justify-center mb-4" style="background-color: var(--bg-teal-light);">01</span>
                            <h3 class="font-bold text-base mb-2" style="color: var(--text-main);">Age Requirement (12+)</h3>
                            <p class="text-xs leading-relaxed" style="color: var(--text-muted);">
                                You must be at least <strong>12 years old</strong>. Teens and adults both make wonderful mentors as younger children connect warmly with youth peers.
                            </p>
                        </div>
                    </div>

                    <div class="p-6 rounded-2xl border border-gray-200/80 shadow-xs flex flex-col justify-between" style="background-color: var(--bg-card);">
                        <div>
                            <span class="w-8 h-8 rounded-full text-brand-teal text-xs font-bold flex items-center justify-center mb-4" style="background-color: var(--bg-teal-light);">02</span>
                            <h3 class="font-bold text-base mb-2" style="color: var(--text-main);">Skills Profile or Intro</h3>
                            <p class="text-xs leading-relaxed" style="color: var(--text-muted);">
                                Provide a simple profile or introduction regarding your skills (e.g., artwork gallery for Art mentors, or an experience introduction for social skills).
                            </p>
                        </div>
                    </div>

                    <div class="p-6 rounded-2xl border border-gray-200/80 shadow-xs flex flex-col justify-between" style="background-color: var(--bg-card);">
                        <div>
                            <span class="w-8 h-8 rounded-full text-brand-teal text-xs font-bold flex items-center justify-center mb-4" style="background-color: var(--bg-teal-light);">03</span>
                            <h3 class="font-bold text-base mb-2" style="color: var(--text-main);">Short Interview Test</h3>
                            <p class="text-xs leading-relaxed" style="color: var(--text-muted);">
                                Prior formal teaching experience is <strong>not required</strong>! You will complete a short custom test or interview to demonstrate your area of expertise.
                            </p>
                        </div>
                    </div>

                    <div class="p-6 rounded-2xl border border-gray-200/80 shadow-xs flex flex-col justify-between" style="background-color: var(--bg-card);">
                        <div>
                            <span class="w-8 h-8 rounded-full text-brand-teal text-xs font-bold flex items-center justify-center mb-4" style="background-color: var(--bg-teal-light);">04</span>
                            <h3 class="font-bold text-base mb-2" style="color: var(--text-main);">Patience & Caring</h3>
                            <p class="text-xs leading-relaxed" style="color: var(--text-muted);">
                                You <strong>must</strong> have a basic understanding of neurodivergency and be patient and caring, as neurodivergent kids learn at their own pace.
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Volunteer Application Form Section -->
        <section id="volunteer-form" class="py-16 border-b border-gray-200/50" style="background-color: var(--bg-card);">
            <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="p-6 sm:p-10 rounded-3xl border border-brand-teal/30 shadow-sm" style="background-color: var(--bg-main);">
                    <div class="text-center max-w-2xl mx-auto mb-8">
                        <span class="px-3.5 py-1 rounded-full bg-brand-teal text-white text-xs font-bold tracking-wider uppercase inline-block mb-2">Volunteer Portal</span>
                        <h2 class="text-2xl sm:text-3xl font-bold" style="color: var(--text-main);">Apply to Become a Mentor</h2>
                        <p class="text-xs sm:text-sm mt-1" style="color: var(--text-muted);">Teach academics, art, or social skills to a neurodivergent child who needs gentle support.</p>
                    </div>

                    <form id="volunteerApplicationForm" onsubmit="handleVolunteerSubmit(event)" class="space-y-6">
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label for="vName" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Full Name <span class="text-red-500">*</span></label>
                                <input type="text" id="vName" required placeholder="e.g. Maya Lin" class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);">
                            </div>
                            <div>
                                <label for="vAge" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Your Age <span class="text-red-500">* (Must be 12+)</span></label>
                                <input type="number" id="vAge" min="12" max="99" required placeholder="12 or older" class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);">
                                <span id="vAgeError" class="text-red-500 text-[11px] hidden mt-1 block">You must be at least 12 years old to volunteer.</span>
                            </div>
                        </div>

                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label for="vEmail" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Email Address <span class="text-red-500">*</span></label>
                                <input type="email" id="vEmail" required placeholder="maya@example.com" class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);">
                            </div>
                            <div>
                                <label for="vPhone" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Phone Number (Optional)</label>
                                <input type="tel" id="vPhone" placeholder="(555) 000-0000" class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);">
                            </div>
                        </div>

                        <div>
                            <label for="vExpertise" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Primary Area of Expertise <span class="text-red-500">*</span></label>
                            <select id="vExpertise" required class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);">
                                <option value="">Select your main strength...</option>
                                <option value="Liberal Arts & Reading">Liberal Arts, Reading & Writing</option>
                                <option value="Mathematics & STEM">Mathematics & Science (STEM)</option>
                                <option value="Visual Arts & Drawing">Visual Arts, Drawing & Crafting</option>
                                <option value="Social Skills & Conversation">Social Skills & Friendship Cues</option>
                                <option value="Music & Hobbies">Music, Gaming, or Hobbies</option>
                                <option value="General Academic Homework">General Homework & Organization</option>
                            </select>
                        </div>

                        <div>
                            <label for="vPortfolio" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Profile / Skill Introduction / Portfolio Link <span class="text-red-500">*</span></label>
                            <textarea id="vPortfolio" rows="3" required placeholder="Describe your experience or paste a link to an art gallery, CV, or general background intro..." class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);"></textarea>
                        </div>

                        <div>
                            <label for="vMotivation" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Why do you want to join NeuroBridge? <span class="text-red-500">*</span></label>
                            <textarea id="vMotivation" rows="3" required placeholder="Tell us why you'd like to mentor non-neurotypical youth..." class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);"></textarea>
                        </div>

                        <div>
                            <label class="flex items-start gap-3 cursor-pointer">
                                <input type="checkbox" required class="mt-1 w-4 h-4 text-brand-teal rounded border-gray-300">
                                <span class="text-xs leading-tight" style="color: var(--text-main);">
                                    I confirm that I have a basic understanding of neurodivergency (or am eager to learn), and promise to remain patient, gentle, and caring during tutoring sessions.
                                </span>
                            </label>
                        </div>

                        <button type="submit" class="w-full py-4 rounded-xl bg-brand-teal hover:bg-brand-tealHover text-white font-bold text-center transition shadow-md flex items-center justify-center gap-2">
                            <i class="fa-solid fa-paper-plane"></i> Submit Volunteer Application
                        </button>
                    </form>
                </div>
            </div>
        </section>

        <!-- Student / Family Application Form Section with Unix3 Bottom Sticker -->
        <section id="student-form" class="py-16 border-b border-gray-200/50 relative" style="background-color: var(--bg-main);">
            <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="p-6 sm:p-10 rounded-3xl border border-brand-teal/30 shadow-md relative" style="background-color: var(--bg-card);">
                    
                    <!-- Unix3 Bottom Sticker Cheering at top right of the form -->
                    <div class="absolute -top-10 right-4 sm:right-8 flex items-center gap-2 animate-float">
                        <div class="w-20 h-20 rounded-2xl overflow-hidden bg-black border-2 border-brand-teal/30 shadow-md flex items-center justify-center">
                            <img src="Unix3.jpg" alt="Unix3 Sticker Cheering with wing raised" class="unix3-sticker-bottom">
                        </div>
                    </div>

                    <div class="text-center max-w-2xl mx-auto mb-8 pt-4">
                        <span class="px-3.5 py-1 rounded-full bg-brand-teal text-white text-xs font-bold tracking-wider uppercase inline-block mb-2">If You Are In Need Of Our Help</span>
                        <h2 class="text-2xl sm:text-3xl font-bold" style="color: var(--text-main);">Request Personal Tutoring & Support</h2>
                        <p class="text-xs sm:text-sm mt-1" style="color: var(--text-muted);">Fill out this form if you are a student or parent looking for gentle 1-on-1 learning assistance.</p>
                    </div>

                    <form id="studentApplicationForm" onsubmit="handleStudentSubmit(event)" class="space-y-6">
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label for="sName" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Student's Name <span class="text-red-500">*</span></label>
                                <input type="text" id="sName" required placeholder="Child or Student Name" class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);">
                            </div>
                            <div>
                                <label for="sAge" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Student's Age <span class="text-red-500">*</span></label>
                                <input type="number" id="sAge" min="4" max="25" required placeholder="e.g. 10" class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);">
                            </div>
                        </div>

                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label for="sGuardian" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Parent / Guardian Name <span class="text-red-500">*</span></label>
                                <input type="text" id="sGuardian" required placeholder="Parent or Guardian Name" class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);">
                            </div>
                            <div>
                                <label for="sContact" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Email or Phone <span class="text-red-500">*</span></label>
                                <input type="text" id="sContact" required placeholder="How should we contact you?" class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);">
                            </div>
                        </div>

                        <div>
                            <label for="sDiagnosis" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">Neurodivergent Diagnosis Status <span class="text-red-500">*</span></label>
                            <select id="sDiagnosis" required class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);">
                                <option value="">Select status...</option>
                                <option value="Official Medical Diagnosis">Official Diagnosis (ADHD, Autism, Dyslexia, Dyscalculia, etc.)</option>
                                <option value="In Progress / Self-Identified">In Process / Self-Identified (No formal papers required)</option>
                                <option value="Undiagnosed - Need Consultation">Undiagnosed - Request free initial test / professional consultation</option>
                            </select>
                            <p class="text-[11px] mt-1" style="color: var(--text-muted);">
                                <i class="fa-solid fa-circle-info mr-1"></i> Official diagnosis is <strong>not required</strong>. Undiagnosed children can consult with our team before matching.
                            </p>
                        </div>

                        <div>
                            <label for="sStruggles" class="block text-xs font-semibold mb-1" style="color: var(--text-main);">What specific subjects or skills are you looking to get help on? <span class="text-red-500">*</span></label>
                            <textarea id="sStruggles" rows="4" required placeholder="Describe specific subjects (e.g. math, reading, social cues, art) and learning struggles (e.g. gets sensory overload, struggles with dense text, needs extra breaks)..." class="w-full px-4 py-3 rounded-xl border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-brand-teal text-sm transition" style="background-color: var(--input-bg); color: var(--text-main);"></textarea>
                        </div>

                        <button type="submit" class="w-full py-4 rounded-xl bg-brand-teal hover:bg-brand-tealHover text-white font-bold text-center transition shadow-md flex items-center justify-center gap-2">
                            <i class="fa-solid fa-heart"></i> Submit Request for Tutoring
                        </button>
                    </form>
                </div>
            </div>
        </section>

        <!-- FAQ Accordion Section -->
        <section id="faq" class="py-16 border-b border-gray-200/50" style="background-color: var(--bg-card);">
            <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center max-w-2xl mx-auto mb-10">
                    <span class="text-xs font-bold text-brand-teal uppercase tracking-widest block mb-2">Got Questions?</span>
                    <h2 class="text-2xl sm:text-3xl font-bold" style="color: var(--text-main);">Frequently Asked Questions</h2>
                </div>

                <div class="space-y-4">
                    <div class="border border-gray-200/70 rounded-2xl overflow-hidden transition" style="background-color: var(--bg-main);">
                        <button onclick="toggleFaq(1)" class="w-full px-6 py-4 text-left font-semibold flex justify-between items-center gap-4 transition" style="color: var(--text-main);">
                            <span>Is tutoring completely free for families?</span>
                            <i id="faq-icon-1" class="fa-solid fa-chevron-down text-brand-teal transition-transform"></i>
                        </button>
                        <div id="faq-answer-1" class="hidden px-6 pb-4 text-sm leading-relaxed border-t border-gray-100/50 pt-3" style="color: var(--text-muted);">
                            Yes! NeuroBridge Mentors is a non-profit volunteer platform. All individual personal tutoring sessions are 100% free of charge for students and their families.
                        </div>
                    </div>

                    <div class="border border-gray-200/70 rounded-2xl overflow-hidden transition" style="background-color: var(--bg-main);">
                        <button onclick="toggleFaq(2)" class="w-full px-6 py-4 text-left font-semibold flex justify-between items-center gap-4 transition" style="color: var(--text-main);">
                            <span>What if my child does not have a formal diagnosis?</span>
                            <i id="faq-icon-2" class="fa-solid fa-chevron-down text-brand-teal transition-transform"></i>
                        </button>
                        <div id="faq-answer-2" class="hidden px-6 pb-4 text-sm leading-relaxed border-t border-gray-100/50 pt-3" style="color: var(--text-muted);">
                            A formal medical diagnosis is not mandatory. If your child struggles with learning or social cues, they can complete a short test or consultation with our team before being verified and matched.
                        </div>
                    </div>

                    <div class="border border-gray-200/70 rounded-2xl overflow-hidden transition" style="background-color: var(--bg-main);">
                        <button onclick="toggleFaq(3)" class="w-full px-6 py-4 text-left font-semibold flex justify-between items-center gap-4 transition" style="color: var(--text-main);">
                            <span>How are mentors assigned to children?</span>
                            <i id="faq-icon-3" class="fa-solid fa-chevron-down text-brand-teal transition-transform"></i>
                        </button>
                        <div id="faq-answer-3" class="hidden px-6 pb-4 text-sm leading-relaxed border-t border-gray-100/50 pt-3" style="color: var(--text-muted);">
                            We pair kids with volunteers based on specific subject needs (e.g., Art, Reading, Math, Social Skills), personality traits, sensory preferences, and shared hobbies.
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer class="bg-brand-teal text-white py-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div>
                    <div class="flex items-center gap-3 mb-3">
                        <div class="w-9 h-9 rounded-xl bg-brand-paleYellow text-brand-teal flex items-center justify-center text-lg">
                            <i class="fa-solid fa-feather-pointed"></i>
                        </div>
                        <span class="text-xl font-bold tracking-tight">NeuroBridge Mentors</span>
                    </div>
                    <p class="text-xs text-emerald-100 leading-relaxed max-w-sm">
                        Empowering non-neurotypical children with empathetic 1-on-1 personal tutoring that respects their individual learning pace alongside Unix3.
                    </p>
                </div>

                <div>
                    <h4 class="text-xs font-bold uppercase tracking-wider text-emerald-200 mb-3">Navigation Links</h4>
                    <ul class="space-y-2 text-xs text-emerald-100">
                        <li><a href="#about" class="hover:underline">About Our Goal</a></li>
                        <li><a href="#mascot" class="hover:underline">Meet Unix3</a></li>
                        <li><a href="#requirements" class="hover:underline">Volunteer Requirements</a></li>
                        <li><a href="#volunteer-form" class="hover:underline">Volunteer Portal</a></li>
                        <li><a href="#student-form" class="hover:underline">Request Tutoring</a></li>
                    </ul>
                </div>

                <div>
                    <h4 class="text-xs font-bold uppercase tracking-wider text-emerald-200 mb-3">Sensory & Accessibility</h4>
                    <p class="text-xs text-emerald-100 leading-relaxed mb-3">
                        Designed using soft cold-color palettes, Unix3 mascot accents, reading guide rulers, Dyslexia letter-spacing tools, and dim contrast options.
                    </p>
                    <span class="text-[11px] text-emerald-300 block">© 2026 NeuroBridge Mentors. All rights reserved.</span>
                </div>
            </div>
        </div>
    </footer>

    <!-- Modal Dialog -->
    <div id="successModal" class="fixed inset-0 bg-black/60 backdrop-blur-xs flex items-center justify-center z-50 hidden p-4">
        <div class="rounded-3xl max-w-md w-full p-6 text-center space-y-4 border border-gray-200/80 shadow-2xl" style="background-color: var(--bg-card);">
            <div class="w-14 h-14 rounded-full text-brand-teal mx-auto flex items-center justify-center text-3xl" style="background-color: var(--bg-teal-light);">
                <i class="fa-solid fa-circle-check"></i>
            </div>
            <h3 id="modalTitle" class="text-xl font-bold" style="color: var(--text-main);">Application Received!</h3>
            <p id="modalMessage" class="text-xs leading-relaxed" style="color: var(--text-muted);">
                Thank you for reaching out to NeuroBridge Mentors. We will review your submission and contact you within 2 business days.
            </p>
            <button onclick="closeModal()" class="w-full py-3 rounded-xl bg-brand-teal text-white font-bold text-xs uppercase tracking-wider hover:bg-brand-tealHover transition">
                Close
            </button>
        </div>
    </div>

    <!-- JavaScript Handlers -->
    <script>
        let isDyslexiaFont = false;
        let isFocusGuide = false;
        let isCalmMode = false;
        let fontSizeDelta = 0;

        function toggleDyslexiaFont() {
            isDyslexiaFont = !isDyslexiaFont;
            document.body.classList.toggle('dyslexic-mode', isDyslexiaFont);
            const btn = document.getElementById('toggleDyslexia');
            btn.classList.toggle('bg-brand-teal', isDyslexiaFont);
            btn.classList.toggle('text-white', isDyslexiaFont);
        }

        function toggleFocusGuideMode() {
            isFocusGuide = !isFocusGuide;
            const guide = document.getElementById('focusGuide');
            const btn = document.getElementById('toggleFocusGuide');
            guide.style.display = isFocusGuide ? 'block' : 'none';
            btn.classList.toggle('bg-brand-teal', isFocusGuide);
            btn.classList.toggle('text-white', isFocusGuide);
        }

        document.addEventListener('mousemove', function(e) {
            if (isFocusGuide) {
                const guide = document.getElementById('focusGuide');
                guide.style.top = `${e.clientY}px`;
            }
        });

        function toggleCalmMode() {
            isCalmMode = !isCalmMode;
            document.body.classList.toggle('calm-mode', isCalmMode);
            const btn = document.getElementById('toggleContrast');
            btn.classList.toggle('bg-brand-teal', isCalmMode);
            btn.classList.toggle('text-white', isCalmMode);
        }

        function changeFontSize(delta) {
            fontSizeDelta += delta;
            if (fontSizeDelta < -2) fontSizeDelta = -2;
            if (fontSizeDelta > 4) fontSizeDelta = 4;
            document.documentElement.style.fontSize = `${16 + fontSizeDelta}px`;
        }

        function resetFontSize() {
            fontSizeDelta = 0;
            document.documentElement.style.fontSize = '16px';
        }

        function toggleMobileMenu() {
            const menu = document.getElementById('mobileMenu');
            menu.classList.toggle('hidden');
        }

        function toggleFaq(index) {
            const answer = document.getElementById(`faq-answer-${index}`);
            const icon = document.getElementById(`faq-icon-${index}`);
            const isHidden = answer.classList.contains('hidden');
            
            for (let i = 1; i <= 3; i++) {
                document.getElementById(`faq-answer-${i}`)?.classList.add('hidden');
                document.getElementById(`faq-icon-${i}`)?.classList.remove('rotate-180');
            }

            if (isHidden) {
                answer.classList.remove('hidden');
                icon.classList.add('rotate-180');
            }
        }

        function handleVolunteerSubmit(e) {
            e.preventDefault();
            const ageInput = document.getElementById('vAge');
            const ageError = document.getElementById('vAgeError');

            if (parseInt(ageInput.value) < 12) {
                ageError.classList.remove('hidden');
                ageInput.focus();
                return;
            } else {
                ageError.classList.add('hidden');
            }

            const name = document.getElementById('vName').value;
            showModal(
                "Volunteer Application Received!",
                `Thank you ${name}! Your application has been logged. Our coordinator will contact you to schedule your custom skill interview.`
            );
            document.getElementById('volunteerApplicationForm').reset();
        }

        function handleStudentSubmit(e) {
            e.preventDefault();
            const sName = document.getElementById('sName').value;
            const sGuardian = document.getElementById('sGuardian').value;

            showModal(
                "Tutoring Request Submitted!",
                `Thank you ${sGuardian}. We have received the learning assistance request for ${sName}. A coordinator will review the needs and contact you within 2 business days.`
            );
            document.getElementById('studentApplicationForm').reset();
        }

        function showModal(title, text) {
            document.getElementById('modalTitle').textContent = title;
            document.getElementById('modalMessage').textContent = text;
            document.getElementById('successModal').classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('successModal').classList.add('hidden');
        }
    </script>
</body>
</html>
