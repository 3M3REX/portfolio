<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>EMEREX | Motion & Graphic Design</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Plus Jakarta Sans', 'sans-serif'],
                    },
                    colors: {
                        bgDark: '#030303',
                        cardDark: '#0a0a0a',
                        cardLight: '#111111',
                        primary: '#ff1a1a', 
                        primaryHover: '#cc0000',
                    },
                    boxShadow: {
                        'neon': '0 0 40px rgba(255, 26, 26, 0.3)',
                        'card': 'inset 0 1px 0 0 rgba(255, 255, 255, 0.05)',
                    }
                }
            }
        }
    </script>
    <style>
        body {
            background-color: #030303;
            color: #ffffff;
            overflow-x: hidden;
            width: 100%;
            /* ЗАПРЕТ ВЫДЕЛЕНИЯ ТЕКСТА */
            -webkit-user-select: none;
            -ms-user-select: none;
            user-select: none;
        }
        
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #030303; }
        ::-webkit-scrollbar-thumb { background: #222; border-radius: 10px; }
        ::-webkit-scrollbar-thumb:hover { background: #ff1a1a; }

        .text-outline {
            color: transparent;
            -webkit-text-stroke: 1px rgba(255, 255, 255, 0.5);
        }

        .text-gradient-red {
            background: linear-gradient(135deg, #ff4d4d, #990000);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .bento-card {
            background: linear-gradient(180deg, rgba(20,20,20,0.8) 0%, rgba(10,10,10,0.9) 100%);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 24px;
            box-shadow: inset 0 1px 0 0 rgba(255, 255, 255, 0.05);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            overflow: hidden;
            position: relative;
        }

        .bento-card:hover {
            border-color: rgba(255, 26, 26, 0.4);
            transform: translateY(-2px);
            box-shadow: 0 10px 40px -10px rgba(255, 26, 26, 0.15), inset 0 1px 0 0 rgba(255, 255, 255, 0.1);
        }

        @keyframes pulseGlow {
            0% { transform: scale(1); opacity: 0.7; }
            50% { transform: scale(1.05); opacity: 1; }
            100% { transform: scale(1); opacity: 0.7; }
        }

        /* КРАСНЫЕ СФЕРЫ */
        .ambient-glow {
            position: absolute;
            width: 800px;
            height: 800px;
            background: radial-gradient(circle, rgba(255,26,26,0.15) 0%, rgba(3,3,3,0) 70%);
            z-index: -1;
            pointer-events: none;
            animation: pulseGlow 8s ease-in-out infinite;
        }

        .nav-link {
            position: relative;
            z-index: 10;
        }

        .portfolio-item {
            transition: opacity 0.3s ease, transform 0.3s ease;
        }

        /* Animation for the graph line in modal */
        .path-anim {
            stroke-dasharray: 400;
            stroke-dashoffset: 400;
            transition: stroke-dashoffset 2s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .path-anim.draw {
            stroke-dashoffset: 0;
        }

        /* СУПЕР МЕДЛЕННАЯ БЕГУЩАЯ СТРОКА (80 сек) */
        @keyframes scroll {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }
        .animate-scroll {
            animation: scroll 80s linear infinite;
            display: flex;
            width: max-content;
        }

        /* Interactive Stars */
        .star-rating i {
            cursor: pointer;
            transition: all 0.2s;
        }
        .star-rating i:hover {
            transform: scale(1.2);
        }

        /* КАСТОМНЫЙ КУРСОР (только для компов) */
        @media (pointer: fine) {
            body, a, button, input, textarea, .cursor-pointer, .portfolio-img {
                cursor: none !important;
            }
            
            #cursor-dot {
                position: fixed;
                top: 0; left: 0;
                width: 8px; height: 8px;
                background-color: #ff1a1a;
                border-radius: 50%;
                transform: translate(-50%, -50%);
                pointer-events: none;
                z-index: 9999;
                transition: width 0.2s, height 0.2s, background-color 0.2s, box-shadow 0.2s;
                box-shadow: 0 0 12px 2px #ff1a1a; 
            }

            #cursor-ring {
                position: fixed;
                top: 0; left: 0;
                width: 36px; height: 36px;
                border: 2px solid rgba(255, 26, 26, 0.6);
                border-radius: 50%;
                transform: translate(-50%, -50%);
                pointer-events: none;
                z-index: 9998;
                transition: width 0.2s, height 0.2s, border-color 0.2s, background-color 0.2s, box-shadow 0.2s;
                box-shadow: 0 0 15px rgba(255, 26, 26, 0.4), inset 0 0 10px rgba(255, 26, 26, 0.2); 
            }

            body.cursor-hover #cursor-dot {
                width: 5px; height: 5px;
                background-color: #ffffff;
                box-shadow: 0 0 15px 3px #ffffff;
            }
            body.cursor-hover #cursor-ring {
                width: 50px; height: 50px;
                border-color: rgba(255, 255, 255, 0.8);
                background-color: rgba(255, 255, 255, 0.05);
                box-shadow: 0 0 25px rgba(255, 255, 255, 0.3), inset 0 0 15px rgba(255, 255, 255, 0.2);
            }
        }
        
        @media (pointer: coarse) {
            #cursor-dot, #cursor-ring { display: none !important; }
        }
    </style>
</head>
<body class="antialiased">

    <!-- КАСТОМНЫЙ КУРСОР ЭЛЕМЕНТЫ -->
    <div id="cursor-dot"></div>
    <div id="cursor-ring"></div>

    <!-- ЧАСТИЦЫ НА ФОНЕ (ИСКРЫ) -->
    <canvas id="particles-bg" class="fixed inset-0 w-full h-full z-[-2] pointer-events-none"></canvas>

    <!-- VIDEO PLAYER MODAL -->
    <div id="video-modal" class="fixed inset-0 z-[150] bg-black/95 hidden flex justify-center items-center backdrop-blur-md opacity-0 transition-opacity duration-300 p-4">
        <button id="video-close" class="absolute top-4 right-4 md:top-8 md:right-8 w-12 h-12 bg-white/10 hover:bg-white/20 rounded-full flex items-center justify-center text-white transition z-50">
            <i class="fa-solid fa-xmark text-xl"></i>
        </button>
        <div id="video-container" class="w-full relative rounded-2xl overflow-hidden shadow-[0_0_50px_rgba(255,26,26,0.3)] transition-all duration-300 transform scale-95 flex items-center justify-center bg-black">
            <!-- iframe будет вставляться сюда через JS -->
            <iframe id="youtube-iframe" class="absolute top-0 left-0 w-full h-full" src="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        </div>
    </div>

    <!-- MEGA Retention Graph Modal Overlay -->
    <div id="retention-modal" class="fixed inset-0 z-[100] bg-black/90 hidden flex justify-center items-center backdrop-blur-sm opacity-0 transition-opacity duration-300 px-4">
        <div class="relative w-full max-w-4xl bento-card p-6 md:p-10 transform scale-95 transition-transform duration-300" id="retention-modal-content">
            <button id="retention-close" class="absolute top-4 right-4 w-10 h-10 bg-white/5 hover:bg-white/10 rounded-full flex items-center justify-center text-white/50 hover:text-white transition z-50">
                <i class="fa-solid fa-xmark"></i>
            </button>
            
            <div class="flex flex-col md:flex-row md:items-end justify-between mb-8 gap-6">
                <div>
                    <h3 class="text-3xl md:text-4xl font-bold text-white mb-2 flex items-center gap-3" data-i18n="modal_retention_title">
                        Views Growth <i class="fa-solid fa-fire text-primary text-2xl"></i>
                    </h3>
                    <p class="text-gray-400 text-sm md:text-base leading-relaxed max-w-md" data-i18n="modal_retention_desc">
                        Stop getting 0 views. With high-end editing and dynamic pacing, your content will hook the audience and trigger the algorithm.
                    </p>
                </div>
                <div class="flex flex-wrap gap-3">
                    <div class="bg-black/50 border border-white/10 rounded-lg px-4 py-2 text-left min-w-[120px]">
                        <span class="block text-[10px] text-gray-500 uppercase tracking-wider mb-1">Avg. View Duration</span>
                        <span class="text-xl font-bold text-white">03:45 <span class="text-green-500 text-sm align-top"><i class="fa-solid fa-arrow-trend-up"></i></span></span>
                    </div>
                    <div class="bg-black/50 border border-white/10 rounded-lg px-4 py-2 text-left min-w-[120px]">
                        <span class="block text-[10px] text-gray-500 uppercase tracking-wider mb-1">Click-Through Rate</span>
                        <span class="text-xl font-bold text-primary">14.2% <span class="text-primary text-sm align-top"><i class="fa-solid fa-arrow-trend-up"></i></span></span>
                    </div>
                </div>
            </div>
            
            <!-- Animated Graph Container -->
            <div class="w-full h-64 md:h-80 bg-black/40 border border-white/5 rounded-xl relative overflow-hidden flex flex-col p-4 md:p-6">
                
                <div class="absolute left-2 md:left-4 top-6 bottom-12 w-10 flex flex-col justify-between text-[10px] md:text-xs text-gray-500 font-mono z-10">
                    <span>1M+</span>
                    <span>500K</span>
                    <span>100K</span>
                    <span>10K</span>
                    <span>0</span>
                </div>

                <div class="absolute left-14 md:left-16 right-4 md:right-6 bottom-4 h-6 flex justify-between items-end text-[10px] md:text-xs text-gray-500 font-mono z-10">
                    <span>#1</span>
                    <span>#2</span>
                    <span>#3</span>
                    <span>#4</span>
                    <span class="text-primary font-bold">Viral 🚀</span>
                </div>

                <div class="absolute left-14 md:left-16 right-4 md:right-6 top-6 bottom-12 z-0">
                    <div class="absolute inset-0 flex flex-col justify-between opacity-10 z-0 pointer-events-none">
                        <div class="border-b border-dashed border-white w-full h-0"></div>
                        <div class="border-b border-dashed border-white w-full h-0"></div>
                        <div class="border-b border-dashed border-white w-full h-0"></div>
                        <div class="border-b border-dashed border-white w-full h-0"></div>
                        <div class="border-b border-dashed border-white w-full h-0"></div>
                    </div>
                    <div class="absolute inset-0 flex justify-between opacity-10 z-0 pointer-events-none">
                        <div class="border-l border-dashed border-white h-full w-0"></div>
                        <div class="border-l border-dashed border-white h-full w-0"></div>
                        <div class="border-l border-dashed border-white h-full w-0"></div>
                        <div class="border-l border-dashed border-white h-full w-0"></div>
                        <div class="border-l border-dashed border-white h-full w-0"></div>
                    </div>
                    
                    <div class="absolute top-[5%] right-[2%] md:right-[5%] bg-primary/20 border border-primary/40 backdrop-blur-md px-3 py-1.5 rounded-lg text-white text-xs font-bold flex items-center gap-2 shadow-[0_0_15px_rgba(255,26,26,0.3)] animate-pulse z-20 opacity-0 transition-opacity duration-500" id="graph-tooltip">
                        <i class="fa-solid fa-crown text-[#ffd700]"></i> Algorithm Boost
                    </div>
                    
                    <svg class="w-full h-full absolute inset-0 z-10 overflow-visible" preserveAspectRatio="none" viewBox="0 0 100 100">
                        <defs>
                            <linearGradient id="grad" x1="0" y1="0" x2="0" y2="1">
                                <stop offset="0%" stop-color="#ff1a1a" stop-opacity="0.5"/>
                                <stop offset="100%" stop-color="#ff1a1a" stop-opacity="0.0"/>
                            </linearGradient>
                        </defs>
                        <path id="graph-fill" d="M0,100 L0,95 C40,95 60,85 75,60 C85,40 95,15 100,5 L100,100 Z" fill="url(#grad)" class="opacity-0 transition-opacity duration-1000 delay-300"/>
                        <path id="graph-line" d="M0,95 C40,95 60,85 75,60 C85,40 95,15 100,5" fill="none" stroke="#ff1a1a" stroke-width="3" class="path-anim drop-shadow-[0_0_8px_rgba(255,26,26,0.8)]"/>
                    </svg>
                    
                    <div class="absolute top-[5%] right-[0%] w-4 h-4 bg-white rounded-full shadow-[0_0_20px_#ff1a1a] border-[3px] border-primary animate-bounce opacity-0 transition-opacity duration-500 z-20" id="graph-dot" style="transform: translate(50%, -50%);"></div>
                </div>
            </div>
            
            <button id="retention-contact-btn" class="w-full mt-8 bg-primary hover:bg-primaryHover text-white px-6 py-4 rounded-xl font-bold transition-all text-sm md:text-base flex items-center justify-center gap-2 shadow-[0_0_20px_rgba(255,26,26,0.4)] hover:shadow-[0_0_30px_rgba(255,26,26,0.6)] group">
                <i class="fa-brands fa-telegram text-xl group-hover:scale-110 transition-transform"></i> <span data-i18n="btn_start_boost">Start a Project & Boost Views</span>
            </button>
        </div>
    </div>

    <!-- Header / Navbar -->
    <header class="fixed top-4 md:top-6 inset-x-0 w-full z-50 px-4 md:px-6 pointer-events-none">
        <div class="max-w-7xl mx-auto flex justify-between items-center pointer-events-auto gap-1 md:gap-2">
            <!-- Logo -->
            <a href="#" class="flex items-center gap-1.5 md:gap-2 text-base md:text-xl font-bold tracking-tight bg-black/50 backdrop-blur-md px-3 py-1.5 md:px-4 md:py-2 rounded-full border border-white/10 shrink-0">
                <div class="w-2 h-2 md:w-3 md:h-3 rounded-full bg-primary animate-pulse"></div>
                EMEREX
            </a>
            
            <!-- Center Nav Pill -->
            <nav id="main-nav" class="hidden lg:flex items-center gap-1 bg-[#111]/80 backdrop-blur-md px-2 py-1.5 rounded-full border border-white/10 relative">
                <div id="nav-slider" class="absolute top-1.5 bottom-1.5 bg-primary rounded-full transition-all duration-300 ease-out z-0 shadow-[0_0_15px_rgba(255,26,26,0.5)]"></div>
                
                <a href="#home" class="nav-link px-5 py-2 text-white text-sm font-medium transition active-tab" data-i18n="nav_home">Home</a>
                <a href="#portfolio" class="nav-link px-5 py-2 text-gray-400 hover:text-white text-sm font-medium transition" data-i18n="nav_works">Works</a>
                <a href="#about" class="nav-link px-5 py-2 text-gray-400 hover:text-white text-sm font-medium transition" data-i18n="nav_about">About</a>
                <a href="#testimonials" class="nav-link px-5 py-2 text-gray-400 hover:text-white text-sm font-medium transition" data-i18n="nav_reviews">Reviews</a>
            </nav>

            <!-- Language Switcher & Contact -->
            <div class="flex items-center gap-1.5 md:gap-2 shrink-0">
                <!-- Lang Toggle -->
                <div class="flex bg-black/50 backdrop-blur-md rounded-full border border-white/10 p-0.5 shrink-0">
                    <button class="lang-btn px-2 py-1 text-[10px] md:text-xs font-bold rounded-full text-white bg-white/10 transition" data-lang="en">EN</button>
                    <button class="lang-btn px-2 py-1 text-[10px] md:text-xs font-bold rounded-full text-gray-500 hover:text-white transition" data-lang="ru">RU</button>
                    <button class="lang-btn px-2 py-1 text-[10px] md:text-xs font-bold rounded-full text-gray-500 hover:text-white transition" data-lang="uk">UA</button>
                </div>

                <a href="https://t.me/em3rex" target="_blank" class="flex items-center gap-1.5 md:gap-2 bg-[#111]/80 hover:bg-primary backdrop-blur-md px-3 py-1.5 md:px-5 md:py-2 rounded-full border border-white/10 text-[10px] md:text-sm font-medium transition-all group shrink-0">
                    <span data-i18n="nav_contact">Contact</span> <i class="fa-brands fa-telegram text-gray-400 group-hover:text-white transition text-[12px] md:text-base"></i>
                </a>
            </div>
        </div>
    </header>

    <!-- HERO SECTION -->
    <section id="home" class="pt-28 md:pt-32 pb-10 px-4 md:px-6 relative w-full overflow-hidden">
        <!-- КРАСНАЯ СФЕРА -->
        <div class="ambient-glow -top-[200px] -left-[200px]"></div>
        <div class="max-w-7xl mx-auto">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-4 h-auto lg:h-[600px]">
                
                <!-- Main Title Block (Left) -->
                <div class="bento-card lg:col-span-8 p-6 md:p-12 flex flex-col justify-between relative group overflow-hidden">
                    <div class="absolute top-0 left-0 w-full h-1 bg-gradient-to-r from-primary to-transparent opacity-50"></div>
                    
                    <div class="absolute right-10 top-1/4 w-40 h-40 bg-primary/20 rounded-full blur-[60px] z-0 pointer-events-none"></div>

                    <!-- YouTube Interface Mockup -->
                    <div class="absolute right-[-8%] top-[10%] w-[55%] h-[110%] rotate-[-3deg] border border-white/15 rounded-3xl bg-[#090909] p-5 hidden md:flex flex-col gap-4 shadow-[0_20px_50px_rgba(0,0,0,0.9)] z-0 opacity-35 transition-all duration-700 group-hover:opacity-65 group-hover:scale-[1.02] pointer-events-none select-none">
                        <div class="flex items-center gap-3 border-b border-white/5 pb-3">
                            <i class="fa-brands fa-youtube text-primary text-2xl"></i>
                            <div class="w-24 h-5 rounded-full bg-white/10"></div>
                            <div class="ml-auto flex gap-2">
                                <div class="w-6 h-6 rounded-full bg-white/10"></div>
                                <div class="w-6 h-6 rounded-full bg-white/10"></div>
                            </div>
                        </div>
                        <div class="grid grid-cols-2 gap-3 flex-1">
                            <div class="bg-white/[0.02] border border-white/5 rounded-xl p-2.5 flex flex-col gap-2.5 transition duration-300 group-hover:border-primary/20">
                                <div class="aspect-video bg-gradient-to-br from-primary/30 to-black rounded-lg relative overflow-hidden flex items-center justify-center border border-white/5">
                                    <div class="w-8 h-8 rounded-full bg-primary/80 flex items-center justify-center shadow-lg"><i class="fa-solid fa-play text-white text-[10px] ml-0.5"></i></div>
                                </div>
                                <div class="h-3 bg-white/20 rounded-full w-5/6"></div>
                                <div class="h-2 bg-white/5 rounded-full w-1/2"></div>
                            </div>
                            <div class="bg-white/[0.02] border border-white/5 rounded-xl p-2.5 flex flex-col gap-2.5 transition duration-300 group-hover:border-primary/20">
                                <div class="aspect-video bg-gradient-to-br from-[#222] to-black rounded-lg relative overflow-hidden flex items-center justify-center border border-white/5">
                                    <div class="w-8 h-8 rounded-full bg-white/10 flex items-center justify-center"><i class="fa-solid fa-play text-white/40 text-[10px] ml-0.5"></i></div>
                                </div>
                                <div class="h-3 bg-white/20 rounded-full w-4/5"></div>
                                <div class="h-2 bg-white/5 rounded-full w-1/3"></div>
                            </div>
                            <div class="bg-white/[0.02] border border-white/5 rounded-xl p-2.5 flex flex-col gap-2.5 transition duration-300 group-hover:border-primary/20">
                                <div class="aspect-video bg-gradient-to-br from-violet-900/20 to-black rounded-lg relative overflow-hidden flex items-center justify-center border border-white/5">
                                    <div class="w-8 h-8 rounded-full bg-white/10 flex items-center justify-center"><i class="fa-solid fa-play text-white/40 text-[10px] ml-0.5"></i></div>
                                </div>
                                <div class="h-3 bg-white/20 rounded-full w-11/12"></div>
                                <div class="h-2 bg-white/5 rounded-full w-1/2"></div>
                            </div>
                            <div class="bg-white/[0.02] border border-white/5 rounded-xl p-2.5 flex flex-col gap-2.5 transition duration-300 group-hover:border-primary/20">
                                <div class="aspect-video bg-gradient-to-br from-[#1a1a1a] to-[#050505] rounded-lg relative overflow-hidden flex items-center justify-center border border-white/5">
                                    <div class="w-8 h-8 rounded-full bg-white/10 flex items-center justify-center"><i class="fa-solid fa-play text-white/40 text-[10px] ml-0.5"></i></div>
                                </div>
                                <div class="h-3 bg-white/20 rounded-full w-3/4"></div>
                                <div class="h-2 bg-white/5 rounded-full w-1/3"></div>
                            </div>
                        </div>
                    </div>

                    <div class="absolute inset-y-0 right-[42%] left-0 bg-gradient-to-r from-[#030303] via-[#030303]/80 to-transparent z-0 pointer-events-none"></div>
                    <div class="absolute inset-0 bg-gradient-to-t from-[#030303] via-transparent to-transparent z-0 pointer-events-none"></div>
                    <div class="absolute inset-0 backdrop-blur-[1.5px] z-0 pointer-events-none"></div>

                    <!-- Main Hero Text Content -->
                    <div class="relative z-10 flex flex-col justify-between h-full w-full">
                        <div>
                            <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-white/10 bg-white/5 text-[10px] md:text-xs font-medium text-gray-400 mb-4 md:mb-6" data-i18n="hero_badge">
                                <i class="fa-solid fa-bolt text-primary"></i> Available for worldwide projects
                            </div>
                            <h1 class="text-4xl sm:text-5xl md:text-7xl font-bold tracking-tighter leading-[1.1] mb-4" data-i18n="hero_title">
                                Your Visuals <br>
                                <span class="text-gradient-red">On Demand</span>
                            </h1>
                            <p class="text-gray-400 max-w-md text-sm md:text-lg leading-relaxed mb-6 md:mb-8" data-i18n="hero_desc">
                                From discovery to deployment, I craft motion graphics and design experiences that audiences actually love.
                            </p>
                        </div>
                        <div class="flex flex-wrap gap-3 md:gap-4">
                            <a href="#portfolio" class="bg-primary hover:bg-primaryHover text-white px-6 md:px-8 py-3 md:py-3.5 rounded-full font-semibold transition-colors text-xs md:text-sm" data-i18n="btn_works">
                                Explore Works
                            </a>
                            <a href="https://t.me/em3rex" class="bg-transparent border border-white/20 hover:border-white text-white px-6 md:px-8 py-3 md:py-3.5 rounded-full font-semibold transition-all text-xs md:text-sm" data-i18n="btn_start">
                                Start a Project
                            </a>
                        </div>
                    </div>
                </div>

                <!-- Right Info Grid -->
                <div class="lg:col-span-4 flex flex-col gap-4">
                    <div class="grid grid-cols-2 gap-4 flex-1">
                        <div class="bento-card p-4 md:p-6 flex flex-col justify-center items-center text-center">
                            <span class="text-3xl md:text-5xl font-bold text-white mb-1">40+</span>
                            <span class="text-[9px] md:text-[10px] text-gray-500 uppercase tracking-widest font-bold" data-i18n="stat_clients">Clients</span>
                        </div>
                        <div class="bento-card p-4 md:p-6 flex flex-col justify-center items-center text-center">
                            <!-- ИЗМЕНЕНО: 3M+ -->
                            <span class="text-3xl md:text-5xl font-bold text-white mb-1">3M<span class="text-primary">+</span></span>
                            <span class="text-[9px] md:text-[10px] text-gray-500 uppercase tracking-widest font-bold" data-i18n="stat_views">Views Gen.</span>
                        </div>
                    </div>

                    <div id="retention-card" class="bento-card p-4 md:p-6 flex items-center justify-between group h-24 md:h-32 cursor-pointer border-transparent hover:border-primary/40 relative overflow-hidden">
                        <div class="absolute inset-0 bg-primary/5 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                        <div class="relative z-10">
                            <h4 class="text-lg md:text-xl font-bold text-white mb-1 group-hover:text-primary transition-colors" data-i18n="stat_retention_title">High Retention</h4>
                            <p class="text-[10px] md:text-xs text-gray-400 group-hover:text-white transition-colors" data-i18n="stat_retention_desc">Algorithm-friendly pacing</p>
                        </div>
                        <div class="relative z-10 w-10 h-10 md:w-14 md:h-14 rounded-full bg-primary/10 border border-primary/20 flex items-center justify-center text-primary group-hover:scale-110 group-hover:bg-primary group-hover:text-white group-hover:shadow-[0_0_20px_rgba(255,26,26,0.5)] transition-all duration-300">
                            <i class="fa-solid fa-chart-line text-lg md:text-xl"></i>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 gap-4 h-24 md:h-32">
                        <div class="bento-card p-4 md:p-6 flex flex-col justify-center items-center text-center">
                            <span class="text-2xl md:text-3xl font-bold text-white mb-1">4+</span>
                            <span class="text-[9px] md:text-[10px] text-gray-500 uppercase tracking-widest font-bold" data-i18n="stat_exp">Years Exp</span>
                        </div>
                        <div class="bento-card p-4 md:p-6 flex flex-col justify-center items-center text-center">
                            <span class="text-2xl md:text-3xl font-bold text-white mb-1">100+</span>
                            <span class="text-[9px] md:text-[10px] text-gray-500 uppercase tracking-widest font-bold" data-i18n="stat_proj">Projects</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Skills Banner (Бегущая строка) -->
            <div class="mt-4 bento-card py-4 md:py-6 overflow-hidden flex relative group w-full">
                <div class="animate-scroll group-hover:[animation-play-state:paused]">
                    <!-- Block 1 -->
                    <div class="flex gap-6 md:gap-12 px-3 md:px-6 text-gray-500 font-medium uppercase tracking-widest text-[10px] md:text-sm opacity-70 items-center shrink-0 whitespace-nowrap flex-nowrap">
                        <span>After Effects</span><span class="text-primary">•</span>
                        <span>Premiere Pro</span><span class="text-primary">•</span>
                        <span>Photoshop</span><span class="text-primary">•</span>
                        <span>Blender 3D</span><span class="text-primary">•</span>
                        <span data-i18n="skill_motion">Motion Design</span><span class="text-primary">•</span>
                        <span data-i18n="skill_graphic">Graphic Art</span><span class="text-primary">•</span>
                        <span data-i18n="skill_yt">YouTube Turnkey</span><span class="text-primary">•</span>
                    </div>
                    <!-- Block 2 -->
                    <div class="flex gap-6 md:gap-12 px-3 md:px-6 text-gray-500 font-medium uppercase tracking-widest text-[10px] md:text-sm opacity-70 items-center shrink-0 whitespace-nowrap flex-nowrap">
                        <span>After Effects</span><span class="text-primary">•</span>
                        <span>Premiere Pro</span><span class="text-primary">•</span>
                        <span>Photoshop</span><span class="text-primary">•</span>
                        <span>Blender 3D</span><span class="text-primary">•</span>
                        <span data-i18n="skill_motion">Motion Design</span><span class="text-primary">•</span>
                        <span data-i18n="skill_graphic">Graphic Art</span><span class="text-primary">•</span>
                        <span data-i18n="skill_yt">YouTube Turnkey</span><span class="text-primary">•</span>
                    </div>
                    <!-- Block 3 -->
                    <div class="flex gap-6 md:gap-12 px-3 md:px-6 text-gray-500 font-medium uppercase tracking-widest text-[10px] md:text-sm opacity-70 items-center shrink-0 whitespace-nowrap flex-nowrap">
                        <span>After Effects</span><span class="text-primary">•</span>
                        <span>Premiere Pro</span><span class="text-primary">•</span>
                        <span>Photoshop</span><span class="text-primary">•</span>
                        <span>Blender 3D</span><span class="text-primary">•</span>
                        <span data-i18n="skill_motion">Motion Design</span><span class="text-primary">•</span>
                        <span data-i18n="skill_graphic">Graphic Art</span><span class="text-primary">•</span>
                        <span data-i18n="skill_yt">YouTube Turnkey</span><span class="text-primary">•</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- PORTFOLIO SECTION -->
    <section id="portfolio" class="py-16 md:py-20 px-4 md:px-6 relative overflow-hidden">
        <!-- КРАСНАЯ СФЕРА -->
        <div class="ambient-glow top-[10%] -right-[300px]" style="animation-delay: -2s;"></div>
        <div class="max-w-7xl mx-auto">
            <div class="mb-8 md:mb-10 flex flex-col md:flex-row justify-between items-start md:items-end gap-4">
                <div>
                    <div class="text-primary text-xs md:text-sm font-bold uppercase tracking-widest mb-2 flex items-center gap-2">
                        <div class="w-1.5 h-1.5 bg-primary rounded-full"></div> <span data-i18n="sect_works">Works</span>
                    </div>
                    <h2 class="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight" data-i18n="title_works">Selected Projects</h2>
                </div>
                <p class="text-gray-500 max-w-sm text-xs md:text-sm" data-i18n="desc_works">A curated showcase of recent motion graphics, branding, and digital design. Click to enlarge.</p>
            </div>

            <!-- Portfolio Filters -->
            <div class="flex flex-wrap gap-2 mb-6 md:mb-8" id="portfolio-filters">
                <button class="filter-btn px-4 md:px-5 py-1.5 md:py-2 rounded-full border border-white/10 bg-white/10 text-white text-xs md:text-sm font-medium transition" data-filter="all" data-i18n="filt_all">All</button>
                <button class="filter-btn px-4 md:px-5 py-1.5 md:py-2 rounded-full border border-white/10 bg-transparent text-gray-400 hover:text-white hover:bg-white/5 text-xs md:text-sm font-medium transition" data-filter="podcasts" data-i18n="filt_podcasts">Podcasts</button>
                <button class="filter-btn px-4 md:px-5 py-1.5 md:py-2 rounded-full border border-white/10 bg-transparent text-gray-400 hover:text-white hover:bg-white/5 text-xs md:text-sm font-medium transition" data-filter="gaming" data-i18n="filt_gaming">YouTube Gaming</button>
                <button class="filter-btn px-4 md:px-5 py-1.5 md:py-2 rounded-full border border-white/10 bg-transparent text-gray-400 hover:text-white hover:bg-white/5 text-xs md:text-sm font-medium transition" data-filter="vlogs" data-i18n="filt_vlogs">Vlogs</button>
                <button class="filter-btn px-4 md:px-5 py-1.5 md:py-2 rounded-full border border-white/10 bg-transparent text-gray-400 hover:text-white hover:bg-white/5 text-xs md:text-sm font-medium transition" data-filter="reels" data-i18n="filt_reels">Reels / TikToks</button>
                <button class="filter-btn px-4 md:px-5 py-1.5 md:py-2 rounded-full border border-white/10 bg-transparent text-gray-400 hover:text-white hover:bg-white/5 text-xs md:text-sm font-medium transition" data-filter="creatives" data-i18n="filt_creatives">Creatives</button>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 md:gap-6" id="portfolio-grid">
                
                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="creatives">
                    <img src="https://i.ytimg.com/vi/07aWIxoeLdU/maxresdefault.jpg" alt="Gaming Montage" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="07aWIxoeLdU" data-video-type="video">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-primary/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-primary border border-primary/20 w-max mb-2 md:mb-3">YouTube Gaming</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_game_t">Insane Gaming Montage</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_game_d">High-energy edit with crazy pacing and sound design.</p>
                    </div>
                </div>

                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="creatives">
                    <img src="https://i.ytimg.com/vi/4XXQMko7xss/maxresdefault.jpg" alt="Opium Style" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="4XXQMko7xss" data-video-type="video">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-purple-500/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-purple-400 border border-purple-500/20 w-max mb-2 md:mb-3">Opium Style</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_opium_t">Opium Style Promo</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_opium_d">Trendy, dark aesthetics with heavy sync.</p>
                    </div>
                </div>

                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="vlogs">
                    <img src="https://i.ytimg.com/vi/gjepoikhITE/maxresdefault.jpg" alt="Vlog 1" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="gjepoikhITE" data-video-type="video">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-blue-500/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-blue-400 border border-blue-500/20 w-max mb-2 md:mb-3">Vlogs</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_vlog1_t">Cinematic Vlog</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_vlog1_d">Smooth storytelling and color grading.</p>
                    </div>
                </div>

                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="vlogs">
                    <img src="https://i.ytimg.com/vi/MrrY-i7PZsU/maxresdefault.jpg" alt="Vlog 2" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="MrrY-i7PZsU" data-video-type="video">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-blue-500/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-blue-400 border border-blue-500/20 w-max mb-2 md:mb-3">Vlogs</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_vlog2_t">Dynamic Lifestyle Vlog</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_vlog2_d">Engaging pacing designed for high retention.</p>
                    </div>
                </div>

                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="podcasts">
                    <img src="https://i.ytimg.com/vi/WFtc-Y69iTk/maxresdefault.jpg" alt="Podcast" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="WFtc-Y69iTk" data-video-type="video">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-yellow-500/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-yellow-400 border border-yellow-500/20 w-max mb-2 md:mb-3">Podcast</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_podcast_t">Podcast Edit</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_podcast_d">Clean cuts, multi-camera sync, and dynamic pop-ups.</p>
                    </div>
                </div>

                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="gaming">
                    <img src="https://i.ytimg.com/vi/U0Gc_b1hM24/maxresdefault.jpg" alt="Gaming Video" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="U0Gc_b1hM24" data-video-type="video">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-primary/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-primary border border-primary/20 w-max mb-2 md:mb-3">YouTube Gaming</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_game_new_t">New Gaming Highlights</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_game_new_d">Fresh gameplay edit with epic moments.</p>
                    </div>
                </div>

                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="vlogs">
                    <img src="https://i.ytimg.com/vi/GJGc4qb1Gjs/maxresdefault.jpg" alt="Vlog Video" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="GJGc4qb1Gjs" data-video-type="video">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-blue-500/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-blue-400 border border-blue-500/20 w-max mb-2 md:mb-3">Vlogs</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_vlog_new_t">Latest Cinematic Vlog</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_vlog_new_d">New journey, new vibes, new edit.</p>
                    </div>
                </div>

                <!-- 8. ИИ контент (Шортс) -->
                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="reels">
                    <img src="https://i.ytimg.com/vi/q1D_bIHMk2k/maxresdefault.jpg" onerror="this.onerror=null; this.src='https://i.ytimg.com/vi/q1D_bIHMk2k/hqdefault.jpg';" alt="AI Content" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="q1D_bIHMk2k" data-video-type="shorts">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-green-500/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-green-400 border border-green-500/20 w-max mb-2 md:mb-3">Reels / TikToks</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_short_ai_t">AI Content Edit</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_short_ai_d">Dynamic captions and visual effects for AI-generated content.</p>
                    </div>
                </div>

                <!-- 9. Тик Ток -->
                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="reels">
                    <img src="https://i.ytimg.com/vi/ayJDMgnbArw/maxresdefault.jpg" onerror="this.onerror=null; this.src='https://i.ytimg.com/vi/ayJDMgnbArw/hqdefault.jpg';" alt="TikTok" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="ayJDMgnbArw" data-video-type="shorts">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-pink-500/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-pink-400 border border-pink-500/20 w-max mb-2 md:mb-3">Reels / TikToks</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_short_tiktok_t">Viral TikTok</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_short_tiktok_d">High-retention short form video with trendy edits.</p>
                    </div>
                </div>

                <!-- 10. Анимация логотипа -->
                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="creatives">
                    <img src="https://i.ytimg.com/vi/UizwjagZfGY/maxresdefault.jpg" onerror="this.onerror=null; this.src='https://i.ytimg.com/vi/UizwjagZfGY/hqdefault.jpg';" alt="Logo Animation" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="UizwjagZfGY" data-video-type="shorts">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-indigo-500/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-indigo-400 border border-indigo-500/20 w-max mb-2 md:mb-3">Creatives</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_creative_logo_t">Logo Animation</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_creative_logo_d">Clean and professional logo reveal animation.</p>
                    </div>
                </div>

                <!-- 11. Стерильный монтаж 1 -->
                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="reels">
                    <img src="https://i.ytimg.com/vi/NG_s0QorcrA/maxresdefault.jpg" onerror="this.onerror=null; this.src='https://i.ytimg.com/vi/NG_s0QorcrA/hqdefault.jpg';" alt="Clean Edit" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="NG_s0QorcrA" data-video-type="shorts">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-gray-500/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-gray-300 border border-gray-500/20 w-max mb-2 md:mb-3">Reels / TikToks</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_short_sterile1_t">Clean Short Edit</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_short_sterile1_d">Minimalistic and clean edit for professional shorts.</p>
                    </div>
                </div>

                <!-- 12. Стерильный монтаж 2 -->
                <div class="bento-card group h-[250px] sm:h-[350px] md:h-[400px] portfolio-item relative overflow-hidden" data-category="reels">
                    <img src="https://i.ytimg.com/vi/AYeK9PE7-w4/maxresdefault.jpg" onerror="this.onerror=null; this.src='https://i.ytimg.com/vi/AYeK9PE7-w4/hqdefault.jpg';" alt="Expert Edit" class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-500">
                    <div class="video-trigger absolute inset-0 flex items-center justify-center z-20 cursor-pointer" data-video-id="AYeK9PE7-w4" data-video-type="shorts">
                        <div class="w-16 h-16 md:w-20 md:h-20 bg-primary/90 rounded-full flex items-center justify-center transform transition-transform group-hover:scale-110 shadow-[0_0_30px_rgba(255,26,26,0.6)]">
                            <i class="fa-solid fa-play text-white text-2xl md:text-3xl ml-1"></i>
                        </div>
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/30 to-transparent p-5 md:p-8 flex flex-col justify-end pointer-events-none z-10">
                        <span class="px-3 py-1 bg-gray-500/20 backdrop-blur-md rounded-full text-[10px] md:text-xs font-semibold text-gray-300 border border-gray-500/20 w-max mb-2 md:mb-3">Reels / TikToks</span>
                        <h3 class="text-lg md:text-2xl font-bold mb-1 md:mb-2" data-i18n="port_short_sterile2_t">Expert Short Form</h3>
                        <p class="text-gray-400 text-xs md:text-sm line-clamp-2" data-i18n="port_short_sterile2_d">Sterile video editing focused on clear delivery.</p>
                    </div>
                </div>

            </div>

            <!-- КНОПКА ПОКАЗАТЬ ЕЩЕ -->
            <div class="flex justify-center mt-8 md:mt-12 hidden" id="load-more-container">
                <button id="load-more-btn" class="flex flex-col items-center gap-2 text-gray-400 hover:text-white transition group">
                    <span class="text-xs md:text-sm font-bold uppercase tracking-widest" data-i18n="btn_show_more">Show More</span>
                    <div class="w-10 h-10 rounded-full border border-white/10 flex items-center justify-center bg-white/5 group-hover:bg-primary group-hover:border-primary group-hover:shadow-[0_0_15px_rgba(255,26,26,0.5)] transition-all">
                        <i class="fa-solid fa-chevron-down group-hover:translate-y-0.5 transition-transform" id="load-more-icon"></i>
                    </div>
                </button>
            </div>

        </div>
    </section>

    <!-- ABOUT / SERVICES -->
    <section id="about" class="py-16 md:py-20 px-4 md:px-6 relative overflow-hidden">
        <!-- КРАСНАЯ СФЕРА -->
        <div class="ambient-glow top-[30%] -left-[300px]" style="animation-delay: -4s;"></div>
        <div class="max-w-7xl mx-auto">
            
            <div class="text-primary text-sm font-bold uppercase tracking-widest mb-2 flex items-center gap-2">
                <div class="w-1.5 h-1.5 bg-primary rounded-full"></div> <span data-i18n="sect_about">Experience & Services</span>
            </div>
            <h2 class="text-4xl md:text-5xl font-bold tracking-tight mb-10" data-i18n="title_about">My Journey</h2>

            <div class="grid lg:grid-cols-12 gap-4">
                
                <div class="lg:col-span-12 grid grid-cols-1 lg:grid-cols-12 gap-4 mb-4">
                    <div class="bento-card lg:col-span-5 h-[400px] md:h-[500px] lg:h-auto lg:min-h-[600px] relative group overflow-hidden">
                        <img src="photo_5287599852780985588_y.jpg" alt="EMEREX" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700" style="object-position: center 95%;">
                        <div class="absolute inset-0 bg-gradient-to-t from-black via-black/20 to-transparent p-6 md:p-8 flex flex-col justify-end">
                            <h3 class="text-4xl md:text-5xl font-bold text-white mb-2" data-i18n="profile_name">EMEREX</h3>
                            <p class="text-primary font-bold text-xs md:text-sm tracking-widest uppercase mb-4" data-i18n="profile_role">Motion & Graphic Designer</p>
                            <div class="flex items-center gap-3 text-gray-400 text-xs md:text-sm">
                                <i class="fa-solid fa-briefcase"></i> <span data-i18n="exp_since">In industry since 2022</span>
                            </div>
                        </div>
                    </div>

                    <div class="lg:col-span-7 relative pl-12 md:pl-20 py-6 md:py-10 flex flex-col justify-center">
                        <div class="absolute left-[20px] md:left-[32px] top-10 bottom-10 w-[2px] bg-white/5"></div>

                        <div class="relative mb-8 md:mb-10 group">
                            <div class="absolute -left-[40px] md:-left-[56px] top-1 w-10 h-10 md:w-12 md:h-12 rounded-xl bg-cardDark border border-white/10 flex items-center justify-center text-gray-500 group-hover:border-primary group-hover:text-primary group-hover:shadow-[0_0_15px_rgba(255,26,26,0.3)] transition-all z-10">
                                <i class="fa-solid fa-fire text-sm md:text-base"></i>
                            </div>
                            <div class="bento-card p-5 md:p-6 border-white/5 group-hover:border-primary/30">
                                <div class="inline-flex items-center gap-2 px-3 py-1 bg-primary/10 border border-primary/20 rounded-full text-[10px] md:text-xs text-primary mb-3 font-semibold">
                                    <span data-i18n="exp_3_time">2025 — 2026</span> <div class="w-1.5 h-1.5 bg-primary rounded-full animate-pulse"></div>
                                </div>
                                <h4 class="text-lg md:text-xl font-bold text-white mb-2" data-i18n="exp_3_title">Creatives Production — EuroAFF</h4>
                                <p class="text-xs md:text-sm text-gray-400" data-i18n="exp_3_desc">Producing high-converting creative assets and ad videos. Managing visual concepts from scratch to final render.</p>
                            </div>
                        </div>

                        <div class="relative mb-8 md:mb-10 group">
                            <div class="absolute -left-[40px] md:-left-[56px] top-1 w-10 h-10 md:w-12 md:h-12 rounded-xl bg-cardDark border border-white/10 flex items-center justify-center text-gray-500 group-hover:border-primary group-hover:text-primary group-hover:shadow-[0_0_15px_rgba(255,26,26,0.3)] transition-all z-10">
                                <i class="fa-solid fa-heart-pulse text-sm md:text-base"></i>
                            </div>
                            <div class="bento-card p-5 md:p-6 border-white/5 group-hover:border-primary/30">
                                <div class="inline-block px-3 py-1 bg-white/5 border border-white/10 rounded-full text-[10px] md:text-xs text-gray-300 mb-3 font-semibold" data-i18n="exp_2_time">2024 — 2025</div>
                                <h4 class="text-lg md:text-xl font-bold text-white mb-2" data-i18n="exp_2_title">Motion Designer — Medical Edition</h4>
                                <p class="text-xs md:text-sm text-gray-400" data-i18n="exp_2_desc">Created premium motion graphics and visual identity for medical projects. Focused on clean, trustworthy design.</p>
                            </div>
                        </div>

                        <div class="relative group">
                            <div class="absolute -left-[40px] md:-left-[56px] top-1 w-10 h-10 md:w-12 md:h-12 rounded-xl bg-cardDark border border-white/10 flex items-center justify-center text-gray-500 group-hover:border-primary group-hover:text-primary group-hover:shadow-[0_0_15px_rgba(255,26,26,0.3)] transition-all z-10">
                                <i class="fa-solid fa-gamepad text-sm md:text-base"></i>
                            </div>
                            <div class="bento-card p-5 md:p-6 border-white/5 group-hover:border-primary/30">
                                <div class="inline-block px-3 py-1 bg-white/5 border border-white/10 rounded-full text-[10px] md:text-xs text-gray-300 mb-3 font-semibold" data-i18n="exp_1_time">2022 — 2024</div>
                                <h4 class="text-lg md:text-xl font-bold text-white mb-2" data-i18n="exp_1_title">Gaming Content Editing</h4>
                                <p class="text-xs md:text-sm text-gray-400" data-i18n="exp_1_desc">Edited high-retention content for gaming channels. Mastered dynamic pacing, sound design, and viral storytelling.</p>
                            </div>
                        </div>

                    </div>
                </div>

                <div class="bento-card p-6 md:p-8 lg:col-span-4 bg-gradient-to-br from-[#1a0505] to-[#0a0a0a] border-primary/20 relative group overflow-hidden flex flex-col justify-between">
                    <div class="absolute -right-8 -top-8 text-[120px] text-primary/5 group-hover:text-primary/10 transition-colors pointer-events-none">
                        <i class="fa-brands fa-youtube"></i>
                    </div>
                    <div class="relative z-10">
                        <div class="flex items-center gap-3 mb-4">
                            <div class="w-10 h-10 rounded-full bg-primary/20 flex items-center justify-center text-primary">
                                <i class="fa-solid fa-play"></i>
                            </div>
                            <h3 class="text-xl font-bold" data-i18n="yt_title">YouTube & Socials Turnkey</h3>
                        </div>
                        <p class="text-gray-300 text-sm leading-relaxed mb-6" data-i18n="yt_desc">
                            Full production packaging: from high-energy gaming edits to trendy 'Opium' style. I create high-CTR thumbnails and edit dynamic projects designed to hack the algorithm.
                        </p>
                    </div>
                    <div class="flex flex-wrap gap-2 mt-auto relative z-10">
                        <span class="px-3 py-1 bg-black/50 border border-white/5 rounded-md text-[10px] text-gray-400">#Turnkey</span>
                        <span class="px-3 py-1 bg-black/50 border border-white/5 rounded-md text-[10px] text-gray-400">#Thumbnails</span>
                        <span class="px-3 py-1 bg-primary/10 border border-primary/20 text-primary rounded-md text-[10px]">#OpiumStyle</span>
                    </div>
                </div>

                <div class="bento-card p-6 md:p-8 lg:col-span-4 bg-gradient-to-br from-[#120303] to-[#0a0a0a] border-primary/20 relative group overflow-hidden flex flex-col justify-between">
                    <div class="absolute -right-8 -top-8 text-[120px] text-primary/5 group-hover:text-primary/10 transition-colors pointer-events-none">
                        <i class="fa-brands fa-tiktok"></i>
                    </div>
                    <div class="relative z-10">
                        <div class="flex items-center gap-3 mb-4">
                            <div class="w-10 h-10 rounded-full bg-primary/20 flex items-center justify-center text-primary">
                                <i class="fa-solid fa-mobile-screen"></i>
                            </div>
                            <h3 class="text-xl font-bold" data-i18n="shorts_title">Viral Shorts & TikToks</h3>
                        </div>
                        <p class="text-gray-300 text-sm leading-relaxed mb-6" data-i18n="shorts_desc">
                            High-energy pacing, viral sound design, and interactive captions built to skyrocket your social media presence on Reels, Shorts, and TikTok.
                        </p>
                    </div>
                    <div class="flex flex-wrap gap-2 mt-auto relative z-10">
                        <span class="px-3 py-1 bg-black/50 border border-white/5 rounded-md text-[10px] text-gray-400">#Reels</span>
                        <span class="px-3 py-1 bg-black/50 border border-white/5 rounded-md text-[10px] text-gray-400">#TikTok</span>
                        <span class="px-3 py-1 bg-primary/10 border border-primary/20 text-primary rounded-md text-[10px]">#ViralPacing</span>
                    </div>
                </div>

                <div class="bento-card p-6 md:p-8 lg:col-span-4 bg-gradient-to-br from-[#0d0303] to-[#0a0a0a] border-primary/20 relative group overflow-hidden flex flex-col justify-between">
                    <div class="absolute -right-8 -top-8 text-[120px] text-primary/5 group-hover:text-primary/10 transition-colors pointer-events-none">
                        <i class="fa-solid fa-rectangle-ad"></i>
                    </div>
                    <div class="relative z-10">
                        <div class="flex items-center gap-3 mb-4">
                            <div class="w-10 h-10 rounded-full bg-primary/20 flex items-center justify-center text-primary">
                                <i class="fa-solid fa-bullhorn"></i>
                            </div>
                            <h3 class="text-xl font-bold" data-i18n="creatives_title">Ad Creatives</h3>
                        </div>
                        <p class="text-gray-300 text-sm leading-relaxed mb-6" data-i18n="creatives_desc">
                            Stunning promotional creatives designed to convert. Custom concepts made specifically to scale your SaaS, e-commerce, or affiliate marketing offers.
                        </p>
                    </div>
                    <div class="flex flex-wrap gap-2 mt-auto relative z-10">
                        <span class="px-3 py-1 bg-black/50 border border-white/5 rounded-md text-[10px] text-gray-400">#AdCreatives</span>
                        <span class="px-3 py-1 bg-black/50 border border-white/5 rounded-md text-[10px] text-gray-400">#EuroAFF</span>
                        <span class="px-3 py-1 bg-primary/10 border border-primary/20 text-primary rounded-md text-[10px]">#ROI-Focused</span>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- TESTIMONIALS -->
    <section id="testimonials" class="py-16 md:py-20 px-4 md:px-6 relative overflow-hidden">
        <!-- КРАСНАЯ СФЕРА -->
        <div class="ambient-glow -bottom-[200px] -right-[200px]" style="animation-delay: -6s;"></div>
        <div class="max-w-7xl mx-auto">
            <div class="mb-10 flex flex-col md:flex-row justify-between items-center gap-4">
                <div class="text-center md:text-left">
                    <div class="text-primary text-xs md:text-sm font-bold uppercase tracking-widest mb-2 flex items-center justify-center md:justify-start gap-2">
                        <i class="fa-solid fa-star"></i> <span data-i18n="sect_reviews">Reviews</span> <i class="fa-solid fa-star"></i>
                    </div>
                    <h2 class="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight" data-i18n="title_reviews">Client Feedback</h2>
                </div>
                <a href="https://t.me/+GYFDVUDuTxs0YmEy" target="_blank" class="bg-primary/10 hover:bg-primary border border-primary/20 hover:border-primary text-primary hover:text-white px-6 py-3 rounded-full font-bold transition-all text-xs md:text-sm flex items-center gap-2 group">
                    <span data-i18n="btn_more_reviews">More in Telegram</span> <i class="fa-brands fa-telegram text-lg group-hover:scale-110 transition-transform"></i>
                </a>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-4" id="reviews-grid">
                
                <!-- 1. Опиум стайл (5 звезд) -->
                <div class="bento-card p-6 md:p-8 relative">
                    <div class="text-primary text-xs md:text-sm mb-4"><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i></div>
                    <p class="text-gray-300 text-xs md:text-sm mb-6 italic" data-i18n="rev1_text">"Броу смог помочь с сочнейшим опиумным стилем, немного от приступа флексии глаза болели, но такому дрипсу позавидывал бы даже карти"</p>
                    <div class="flex items-center gap-3 mt-auto">
                        <div class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center text-xs font-bold">DN</div>
                        <div>
                            <h4 class="text-sm font-bold text-white">Dan N.</h4>
                            <p class="text-[10px] md:text-xs text-gray-500">Music Artist</p>
                        </div>
                    </div>
                </div>

                <!-- 2. Вставки и детали (4 звезды) -->
                <div class="bento-card p-6 md:p-8 relative">
                    <div class="text-primary text-xs md:text-sm mb-4"><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i></div>
                    <p class="text-gray-300 text-xs md:text-sm mb-6 italic" data-i18n="rev2_text">"Вставки очень хорошо выглядят, очень хорошее внимание к деталям, так что могу смело рекомендовать"</p>
                    <div class="flex items-center gap-3 mt-auto">
                        <div class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center text-xs font-bold">AR</div>
                        <div>
                            <h4 class="text-sm font-bold text-white">Anton R.</h4>
                            <p class="text-[10px] md:text-xs text-gray-500">YouTuber</p>
                        </div>
                    </div>
                </div>

                <!-- 3. Свежо и вовремя (5 звезд) -->
                <div class="bento-card p-6 md:p-8 relative">
                    <div class="text-primary text-xs md:text-sm mb-4"><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i></div>
                    <p class="text-gray-300 text-xs md:text-sm mb-6 italic" data-i18n="rev3_text">"Все вовремя, качество хорошее и визуал выглядит свежо"</p>
                    <div class="flex items-center gap-3 mt-auto">
                        <div class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center text-xs font-bold">VS</div>
                        <div>
                            <h4 class="text-sm font-bold text-white">Vlad S.</h4>
                            <p class="text-[10px] md:text-xs text-gray-500">Entrepreneur</p>
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="py-8 border-t border-white/5 text-center text-xs md:text-sm text-gray-600">
        <p><span data-i18n="footer_text">© 2026 EMEREX. All rights reserved.</span></p>
    </footer>

    <!-- Interactive Scripts -->
    <script>
        // === 1. DICTIONARY FOR i18n (МУЛЬТИЯЗЫЧНОСТЬ) ===
        const translations = {
            en: {
                nav_home: "Home", nav_works: "Works", nav_about: "About", nav_reviews: "Reviews", nav_contact: "Contact",
                hero_badge: "<i class='fa-solid fa-bolt text-primary'></i> Available for worldwide projects",
                hero_title: "Your Visuals <br><span class='text-gradient-red'>On Demand</span>",
                hero_desc: "From discovery to deployment, I craft motion graphics and design experiences that audiences actually love.",
                btn_works: "Explore Works", btn_start: "Start a Project",
                profile_name: "EMEREX", profile_role: "Motion & Graphic Designer", profile_loc: "Crafting high-end digital art and edits.", 
                stat_exp: "Years Exp", stat_proj: "Projects", stat_clients: "Clients", stat_views: "Views Gen.", stat_retention_title: "Explosive Growth", stat_retention_desc: "From 0 to Millions",
                skill_motion: "Motion Design", skill_graphic: "Graphic Art", skill_yt: "YouTube Turnkey",
                filt_all: "All", filt_podcasts: "Podcasts", filt_gaming: "YouTube Gaming", filt_vlogs: "Vlogs", filt_reels: "Reels / TikToks", filt_creatives: "Creatives",
                sect_works: "Works", title_works: "Selected Projects", desc_works: "A curated showcase of recent motion graphics, branding, and digital design. Click to enlarge.",
                port_game_t: "Insane Gaming Montage", port_game_d: "High-energy edit with crazy pacing and sound design.",
                port_opium_t: "Opium Style Promo", port_opium_d: "Trendy, dark aesthetics with heavy sync.",
                port_vlog1_t: "Cinematic Vlog", port_vlog1_d: "Smooth storytelling and color grading.",
                port_vlog2_t: "Dynamic Lifestyle Vlog", port_vlog2_d: "Engaging pacing designed for high retention.",
                port_podcast_t: "Podcast Edit", port_podcast_d: "Clean cuts, multi-camera sync, and dynamic pop-ups.",
                port_game_new_t: "New Gaming Highlights", port_game_new_d: "Fresh gameplay edit with epic moments.",
                port_vlog_new_t: "Latest Cinematic Vlog", port_vlog_new_d: "New journey, new vibes, new edit.",
                port_short_ai_t: "AI Content Edit", port_short_ai_d: "Dynamic captions and visual effects for AI-generated content.",
                port_short_tiktok_t: "Viral TikTok", port_short_tiktok_d: "High-retention short form video with trendy edits.",
                port_creative_logo_t: "Logo Animation", port_creative_logo_d: "Clean and professional logo reveal animation.",
                port_short_sterile1_t: "Clean Short Edit", port_short_sterile1_d: "Minimalistic and clean edit for professional shorts.",
                port_short_sterile2_t: "Expert Short Form", port_short_sterile2_d: "Sterile video editing focused on clear delivery.",
                sect_about: "Experience & Services", title_about: "My Journey",
                exp_since: "In industry since 2022",
                exp_3_time: "2025 — 2026", exp_3_title: "Creatives Production — EuroAFF", exp_3_desc: "Producing high-converting creative assets and ad videos. Managing visual concepts from scratch to final render.",
                exp_2_time: "2024 — 2025", exp_2_title: "Motion Designer — Medical Edition", exp_2_desc: "Created premium motion graphics and visual identity for medical projects. Focused on clean, trustworthy design.",
                exp_1_time: "2022 — 2024", exp_1_title: "Gaming Content Editing", exp_1_desc: "Edited high-retention content for gaming channels. Mastered dynamic pacing, sound design, and viral storytelling.",
                yt_title: "YouTube & Socials Turnkey", yt_desc: "Full production packaging: from high-energy gaming edits to trendy 'Opium' style. I create high-CTR thumbnails and edit dynamic projects designed to hack the algorithm.",
                shorts_title: "Viral Shorts & TikToks", shorts_desc: "High-energy pacing, viral sound design, and interactive captions built to skyrocket your social media presence on Reels, Shorts, and TikTok.",
                creatives_title: "Ad Creatives", creatives_desc: "Stunning promotional creatives designed to convert. Custom concepts made specifically to scale your SaaS, e-commerce, or affiliate marketing offers.",
                sect_reviews: "Reviews", title_reviews: "Client Feedback",
                rev1_text: `"Bro helped with the juiciest Opium style edit. My eyes hurt a bit from the flex, but even Carti would be jealous of this drip."`,
                rev2_text: `"The overlays look really good, great attention to detail, so I can definitely recommend."`,
                rev3_text: `"Delivered on time, good quality of work, and the visuals look very fresh."`,
                footer_text: "© 2026 EMEREX. All rights reserved.",
                modal_retention_title: "Views Growth",
                modal_retention_desc: "Stop getting 0 views. With high-end editing and dynamic pacing, your content will hook the audience and trigger the algorithm.",
                btn_start_boost: "Start a Project & Boost Views",
                btn_more_reviews: "More in Telegram",
                btn_show_more: "Show More", btn_show_less: "Show Less"
            },
            ru: {
                nav_home: "Главная", nav_works: "Работы", nav_about: "Обо мне", nav_reviews: "Отзывы", nav_contact: "Связаться",
                hero_badge: "<i class='fa-solid fa-bolt text-primary'></i> Открыт к проектам по всему миру",
                hero_title: "Твой Визуал <br><span class='text-gradient-red'>Под Ключ</span>",
                hero_desc: "Создаю моушн-дизайн и графику, которые цепляют с первых секунд. От идеи до финального рендера.",
                btn_works: "Смотреть Работы", btn_start: "Начать Проект",
                profile_name: "EMEREX", profile_role: "Моушн и Графический Дизайнер", profile_loc: "Делаю премиальный диджитал-арт и монтаж.", 
                stat_exp: "Года Опыта", stat_proj: "Проектов", stat_clients: "Клиентов", stat_views: "Просмотров", stat_retention_title: "Взрывные охваты", stat_retention_desc: "От 0 до миллионов",
                skill_motion: "Моушн Дизайн", skill_graphic: "Графика", skill_yt: "YouTube Под Ключ",
                filt_all: "Все", filt_podcasts: "Подкасты", filt_gaming: "Ютуб Гейминг", filt_vlogs: "Влоги", filt_reels: "Рилсы / ТикТоки", filt_creatives: "Креативы",
                sect_works: "Портфолио", title_works: "Избранные Работы", desc_works: "Примеры моушн-дизайна, брендинга и монтажа. Кликни, чтобы увеличить.",
                port_game_t: "Игровой монтаж", port_game_d: "Максимальная динамика, саунд-дизайн и плотный экшен.",
                port_opium_t: "Opium Style", port_opium_d: "Трендовый темный стиль с мощной синхронизацией под бит.",
                port_vlog1_t: "Кинематографичный Влог", port_vlog1_d: "Плавный сторителлинг, цветокоррекция и атмосферные переходы.",
                port_vlog2_t: "Динамичный Влог", port_vlog2_d: "Монтаж под высокое удержание зрителя. Никакой воды.",
                port_podcast_t: "Монтаж Подкаста", port_podcast_d: "Чистые склейки, мультикамера и стильные поп-апы.",
                port_game_new_t: "Игровой монтаж (New)", port_game_new_d: "Свежий геймплей с максимальной отдачей и сочным звуком.",
                port_vlog_new_t: "Свежий Влог", port_vlog_new_d: "Новая поездка, крутой вайб и удержание внимания.",
                port_short_ai_t: "ИИ Контент", port_short_ai_d: "Динамичные субтитры и эффекты для контента, сгенерированного ИИ.",
                port_short_tiktok_t: "Вирусный TikTok", port_short_tiktok_d: "Монтаж с высоким удержанием и трендовыми фишками.",
                port_creative_logo_t: "Анимация Логотипа", port_creative_logo_d: "Стильное и профессиональное появление логотипа.",
                port_short_sterile1_t: "Стерильный Shorts", port_short_sterile1_d: "Минималистичный монтаж для экспертного контента.",
                port_short_sterile2_t: "Экспертный Монтаж", port_short_sterile2_d: "Строгий монтаж с фокусом на четкую подачу без лишней мишуры.",
                sect_about: "Опыт и Услуги", title_about: "Мой Путь",
                exp_since: "В индустрии с 2022 года",
                exp_3_time: "2025 — 2026", exp_3_title: "Создание креативов — EuroAFF", exp_3_desc: "Производство креативов и рекламных видео с высокой конверсией. Полное ведение визуала от идеи до рендера.",
                exp_2_time: "2024 — 2025", exp_2_title: "Моушн-дизайнер — Medical Edition", exp_2_desc: "Создавал премиум моушн-графику и айдентику для медицинских проектов. Упор на строгий и чистый дизайн.",
                exp_1_time: "2022 — 2024", exp_1_title: "Монтаж игрового контента", exp_1_desc: "Монтаж роликов с высоким удержанием для YouTube. Динамика, саунд-дизайн и вирусный сторителлинг.",
                yt_title: "YouTube & Соцсети Под Ключ", yt_desc: "Полная упаковка вашего YouTube-канала: от сочного монтажа до создания кликабельных превью с высоким CTR для разгона алгоритм.",
                shorts_title: "Вирусные Shorts & TikTok", shorts_desc: "Динамичный темп, трендовый звук и цепляющие субтитры для максимального удержания аудитории и быстрого залета ваших коротких видео в рекомендации.",
                creatives_title: "Рекламные Креативы", creatives_desc: "Сногсшибательные и продающие промо-ролики под ключ. Идеально для масштабирования SaaS, товарки, e-commerce или арбитража трафика.",
                sect_reviews: "Отзывы", title_reviews: "Что говорят клиенты",
                rev1_text: `"Броу смог помочь с сочнейшим опиумным стилем, немного от приступа флексии глаза болели, но такому дрипсу позавидывал бы даже карти"`,
                rev2_text: `"Вставки очень хорошо выглядят, очень хорошее внимание к деталям, так что могу рекомендовать"`,
                rev3_text: `"Все вовремя, качество хорошее и визуал выглядит свежо"`,
                footer_text: "© 2026 EMEREX. Все права защищены.",
                modal_retention_title: "Рост просмотров",
                modal_retention_desc: "Хватит сидеть с нулями. Сочный монтаж и правильная динамика заставят алгоритмы продвигать твои видео в рекомендации.",
                btn_start_boost: "Заказать монтаж и бустануть просмотры",
                btn_more_reviews: "Остальные отзывы",
                btn_show_more: "Показать еще", btn_show_less: "Свернуть"
            },
            uk: {
                nav_home: "Головна", nav_works: "Роботи", nav_about: "Про мене", nav_reviews: "Відгуки", nav_contact: "Зв'язок",
                hero_badge: "<i class='fa-solid fa-bolt text-primary'></i> Відкритий до проектів з усього світу",
                hero_title: "Твій Візуал <br><span class='text-gradient-red'>Під Ключ</span>",
                hero_desc: "Створюю моушн-дизайн та графіку, які привертають увагу з перших секунд. Від ідеї до фінального рендеру.",
                btn_works: "Дивитись Роботи", btn_start: "Почати Проект",
                profile_name: "EMEREX", profile_role: "Motion & Graphic Designer", profile_loc: "Створюю преміальний діджитал-арт та монтаж.", 
                stat_exp: "Роки Досвіду", stat_proj: "Проектів", stat_clients: "Клієнтів", stat_views: "Переглядів", stat_retention_title: "Вибухові охоплення", stat_retention_desc: "Від 0 до мільйонів",
                skill_motion: "Motion Design", skill_graphic: "Graphic Art", skill_yt: "YouTube Под Ключ",
                filt_all: "Всі", filt_podcasts: "Подкасти", filt_gaming: "Ютуб Геймінг", filt_vlogs: "Влоги", filt_reels: "Рілси / ТікТоки", filt_creatives: "Креативи",
                sect_works: "Портфоліо", title_works: "Обрані Роботи", desc_works: "Приклади моушн-дизайну, брендингу та монтажу. Клікни, щоб збільшити.",
                port_game_t: "Ігровий монтаж", port_game_d: "Максимальна динаміка, саунд-дизайн та щільний екшен.",
                port_opium_t: "Opium Style", port_opium_d: "Трендовий темний стиль із потужною синхронізацією під біт.",
                port_vlog1_t: "Кінематографічний Влог", port_vlog1_d: "Плавний сторітелінг, кольорокорекція та атмосферні переходи.",
                port_vlog2_t: "Динамічний Влог", port_vlog2_d: "Монтаж під високе утримання глядача. Ніякої води.",
                port_podcast_t: "Монтаж Подкасту", port_podcast_d: "Чисті склейки, мультикамера та стильні поп-апи.",
                port_game_new_t: "Ігровий монтаж (New)", port_game_new_d: "Свіжий геймплей із максимальною віддачею та звуком.",
                port_vlog_new_t: "Свіжий Влог", port_vlog_new_d: "Нова поїздка, крутий вайб та утримання уваги.",
                port_short_ai_t: "ШІ Контент", port_short_ai_d: "Динамічні субтитри та ефекти для контенту, згенерованого ШІ.",
                port_short_tiktok_t: "Вірусний TikTok", port_short_tiktok_d: "Монтаж із високим утриманням та трендовими фішками.",
                port_creative_logo_t: "Анімація Логотипа", port_creative_logo_d: "Стильна та професійна анімація появи логотипа.",
                port_short_sterile1_t: "Стерильний Shorts", port_short_sterile1_d: "Мінімалістичний монтаж для експертного контенту.",
                port_short_sterile2_t: "Експертний Монтаж", port_short_sterile2_d: "Строгий монтаж із фокусом на чітку подачу без зайвого.",
                sect_about: "Досвід та Послуги", title_about: "Мій Шлях",
                exp_since: "В індустрії з 2022 року",
                exp_3_time: "2025 — 2026", exp_3_title: "Створення креативів — EuroAFF", exp_3_desc: "Виробництво креативів та рекламних відео з високою конверсією. Повне ведення візуалу від ідеї до рендеру.",
                exp_2_time: "2024 — 2025", exp_2_title: "Motion Designer — Medical Edition", exp_2_desc: "Створював преміум моушн-графіку та айдентику для медичних проектів. Упор на строгий та чистий дизайн.",
                exp_1_time: "2022 — 2024", exp_1_title: "Монтаж ігрового контенту", exp_1_desc: "Монтаж роликів з високим утриманням для YouTube. Динаміка, саунд-дизайн та вірусний сторітелінг.",
                yt_title: "YouTube та Соцмережі Під Ключ", yt_desc: "Повна упаковка вашого YouTube-канала: від соковитого монтажу до створення клікабельних прев'ю з високим CTR для розгону алгоритмів.",
                shorts_title: "Вірусні Shorts & TikTok", shorts_desc: "Динамічний темп, трендові звуки та чіпкі субтитри для максимального утримання аудиторії та швидкого зальоту ваших коротких відео в рекомендації.",
                creatives_title: "Рекламные Креативы", creatives_desc: "Приголомшливі промо-ролики під ключ. Ідеально для масштабування SaaS, товарки, e-commerce або арбітражу трафіку.",
                sect_reviews: "Відгуки", title_reviews: "Що кажуть клієнти",
                rev1_text: `"Броу зміг допомогти з найсоковитішим опіумним стилем, трохи від нападу флексії очі боліли, але такому дріпсу позаздрив би навіть Карті."`,
                rev2_text: `"Вставки дуже добре виглядають, дуже хороша увага до деталей, так що можу рекомендувати."`,
                rev3_text: `"Все вчасно, якість хороша і візуал виглядає свіжо."`,
                footer_text: "© 2026 EMEREX. Всі права захищені.",
                modal_retention_title: "Ріст переглядів",
                modal_retention_desc: "Досить сидіти з нулем. Соковитий монтаж та правильна динаміка змусять алгоритми просувати твої відео в рекомендації.",
                btn_start_boost: "Замовити монтаж та бустанути перегляди",
                btn_more_reviews: "Більше відгуків",
                btn_show_more: "Показати ще", btn_show_less: "Згорнути"
            }
        };

        const langBtns = document.querySelectorAll('.lang-btn');
        langBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                langBtns.forEach(b => {
                    b.classList.remove('bg-white/10', 'text-white');
                    b.classList.add('text-gray-500');
                });
                btn.classList.remove('text-gray-500');
                btn.classList.add('bg-white/10', 'text-white');

                const lang = btn.getAttribute('data-lang');
                document.querySelectorAll('[data-i18n]').forEach(el => {
                    const key = el.getAttribute('data-i18n');
                    if(translations[lang][key]) {
                        el.innerHTML = translations[lang][key];
                    }
                });

                const activeLink = document.querySelector('.nav-link.text-white');
                if(activeLink) updateSlider(activeLink);
                
                // Перевод кнопки Show More
                if (document.getElementById('load-more-btn')) {
                    const loadMoreText = document.querySelector('#load-more-btn span');
                    if (loadMoreText) {
                        const isExpanded = document.getElementById('load-more-icon').classList.contains('fa-chevron-up');
                        loadMoreText.innerHTML = isExpanded ? translations[lang]['btn_show_less'] : translations[lang]['btn_show_more'];
                    }
                }
            });
        });

        const nav = document.getElementById('main-nav');
        const slider = document.getElementById('nav-slider');
        const links = document.querySelectorAll('.nav-link');

        function updateSlider(linkElement) {
            links.forEach(l => {
                l.classList.remove('text-white');
                l.classList.add('text-gray-400');
            });
            linkElement.classList.remove('text-gray-400');
            linkElement.classList.add('text-white');

            const navRect = nav.getBoundingClientRect();
            const linkRect = linkElement.getBoundingClientRect();
            
            slider.style.width = `${linkRect.width}px`;
            slider.style.left = `${linkRect.left - navRect.left}px`;
        }

        window.addEventListener('load', () => {
            const activeLink = document.querySelector('.nav-link.active-tab');
            if(activeLink) updateSlider(activeLink);
        });

        links.forEach(link => {
            link.addEventListener('click', function(e) {
                updateSlider(this);
            });
        });

        const filterBtns = document.querySelectorAll('.filter-btn');
        const portfolioItems = document.querySelectorAll('.portfolio-item');
        const loadMoreContainer = document.getElementById('load-more-container');
        const loadMoreBtn = document.getElementById('load-more-btn');
        const loadMoreText = loadMoreBtn ? loadMoreBtn.querySelector('span') : null;
        const loadMoreIcon = document.getElementById('load-more-icon');
        
        let currentFilter = 'all';
        let isExpanded = false;
        const INITIAL_ITEMS = 4;

        function updateGrid() {
            let matchCount = 0;
            let visibleCount = 0;

            portfolioItems.forEach(item => {
                const itemCategory = item.getAttribute('data-category');
                const matches = currentFilter === 'all' || currentFilter === itemCategory;
                
                if (matches) {
                    matchCount++;
                    if (isExpanded || visibleCount < INITIAL_ITEMS) {
                        item.style.display = 'block';
                        setTimeout(() => {
                            item.style.opacity = '1';
                            item.style.transform = 'scale(1)';
                        }, 50);
                        visibleCount++;
                    } else {
                        item.style.opacity = '0';
                        item.style.transform = 'scale(0.95)';
                        setTimeout(() => { item.style.display = 'none'; }, 300);
                    }
                } else {
                    item.style.opacity = '0';
                    item.style.transform = 'scale(0.95)';
                    setTimeout(() => { item.style.display = 'none'; }, 300);
                }
            });

            if (loadMoreContainer && loadMoreText && loadMoreIcon) {
                if (matchCount > INITIAL_ITEMS) {
                    loadMoreContainer.classList.remove('hidden');
                    
                    let currentLang = 'en';
                    document.querySelectorAll('.lang-btn').forEach(btn => {
                        if(btn.classList.contains('text-white')) currentLang = btn.getAttribute('data-lang');
                    });

                    if (isExpanded) {
                        loadMoreText.innerHTML = translations[currentLang]['btn_show_less'] || 'Show Less';
                        loadMoreIcon.className = 'fa-solid fa-chevron-up group-hover:-translate-y-0.5 transition-transform';
                    } else {
                        loadMoreText.innerHTML = translations[currentLang]['btn_show_more'] || 'Show More';
                        loadMoreIcon.className = 'fa-solid fa-chevron-down group-hover:translate-y-0.5 transition-transform';
                    }
                } else {
                    loadMoreContainer.classList.add('hidden');
                }
            }
        }

        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                filterBtns.forEach(b => {
                    b.classList.remove('bg-white/10', 'text-white');
                    b.classList.add('bg-transparent', 'text-gray-400');
                });
                btn.classList.remove('bg-transparent', 'text-gray-400');
                btn.classList.add('bg-white/10', 'text-white');

                currentFilter = btn.getAttribute('data-filter');
                isExpanded = false; 
                updateGrid();
            });
        });

        if (loadMoreBtn) {
            loadMoreBtn.addEventListener('click', () => {
                isExpanded = !isExpanded;
                updateGrid();
                if (!isExpanded) {
                    document.getElementById('portfolio-filters').scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            });
        }

        // Вызываем сразу для скрытия лишних
        updateGrid();

        // ЛОГИКА ВИДЕО ПЛЕЕРА (МОДАЛКА)
        const videoModal = document.getElementById('video-modal');
        const videoClose = document.getElementById('video-close');
        const youtubeIframe = document.getElementById('youtube-iframe');
        const videoContainer = document.getElementById('video-container');

        document.querySelectorAll('.video-trigger').forEach(trigger => {
            trigger.addEventListener('click', () => {
                const videoId = trigger.getAttribute('data-video-id');
                const videoType = trigger.getAttribute('data-video-type');

                // Подстраиваем размеры плеера под формат (шортс или обычное видео)
                if (videoType === 'shorts') {
                    videoContainer.style.width = '100%';
                    videoContainer.style.maxWidth = '400px';
                    videoContainer.style.aspectRatio = '9/16';
                } else {
                    videoContainer.style.width = '100%';
                    videoContainer.style.maxWidth = '1000px';
                    videoContainer.style.aspectRatio = '16/9';
                }

                // Загружаем видео с автоплеем
                youtubeIframe.src = `https://www.youtube.com/embed/${videoId}?autoplay=1&rel=0`;
                
                videoModal.classList.remove('hidden');
                setTimeout(() => {
                    videoModal.classList.remove('opacity-0');
                    videoContainer.classList.remove('scale-95');
                    videoContainer.classList.add('scale-100');
                }, 10);
            });
        });

        function closeVideoModal() {
            videoModal.classList.add('opacity-0');
            videoContainer.classList.remove('scale-100');
            videoContainer.classList.add('scale-95');
            setTimeout(() => {
                videoModal.classList.add('hidden');
                youtubeIframe.src = ''; // Останавливаем воспроизведение при закрытии
            }, 300);
        }

        videoClose.addEventListener('click', closeVideoModal);
        videoModal.addEventListener('click', (e) => {
            if(e.target === videoModal) closeVideoModal();
        });


        const retentionCard = document.getElementById('retention-card');
        const retentionModal = document.getElementById('retention-modal');
        const retentionClose = document.getElementById('retention-close');
        const retentionContent = document.getElementById('retention-modal-content');
        const retentionBtn = document.getElementById('retention-contact-btn');
        const graphLine = document.getElementById('graph-line');
        const graphFill = document.getElementById('graph-fill');
        const graphDot = document.getElementById('graph-dot');
        const graphTooltip = document.getElementById('graph-tooltip');

        let animationTimeouts = [];

        function openRetentionModal() {
            retentionModal.classList.remove('hidden');
            setTimeout(() => {
                retentionModal.classList.remove('opacity-0');
                retentionContent.classList.remove('scale-95');
                retentionContent.classList.add('scale-100');
                
                animationTimeouts.push(setTimeout(() => graphLine.classList.add('draw'), 100)); 
                animationTimeouts.push(setTimeout(() => graphFill.classList.remove('opacity-0'), 500)); 
                animationTimeouts.push(setTimeout(() => graphTooltip.classList.remove('opacity-0'), 1200)); 
                animationTimeouts.push(setTimeout(() => graphDot.classList.remove('opacity-0'), 1500)); 
            }, 10);
        }

        function closeRetentionModal() {
            retentionModal.classList.add('opacity-0');
            retentionContent.classList.remove('scale-100');
            retentionContent.classList.add('scale-95');
            
            animationTimeouts.forEach(clearTimeout);
            animationTimeouts = [];
            graphLine.classList.remove('draw');
            graphFill.classList.add('opacity-0');
            graphTooltip.classList.add('opacity-0');
            graphDot.classList.add('opacity-0');

            setTimeout(() => {
                retentionModal.classList.add('hidden');
            }, 300);
        }

        retentionCard.addEventListener('click', openRetentionModal);
        retentionClose.addEventListener('click', closeRetentionModal);
        retentionModal.addEventListener('click', (e) => {
            if(e.target === retentionModal) closeRetentionModal();
        });
        retentionBtn.addEventListener('click', () => {
            window.open('https://t.me/em3rex', '_blank');
        });

        // ЛОГИКА ЧАСТИЦ (ИСКР) НА ФОНЕ
        const canvas = document.getElementById('particles-bg');
        if (canvas) {
            const ctx = canvas.getContext('2d');
            let particlesArray = [];

            function resizeCanvas() {
                canvas.width = window.innerWidth;
                canvas.height = window.innerHeight;
            }
            window.addEventListener('resize', resizeCanvas);
            resizeCanvas();

            class Particle {
                constructor() {
                    this.x = Math.random() * canvas.width;
                    this.y = Math.random() * canvas.height;
                    this.size = Math.random() * 2 + 0.5; 
                    this.speedX = (Math.random() - 0.5) * 0.4;
                    this.speedY = (Math.random() - 0.5) * 0.4;
                    this.color = Math.random() > 0.85 ? '255, 26, 26' : '180, 180, 180';
                    this.opacity = Math.random() * 0.5 + 0.1;
                }
                update() {
                    this.x += this.speedX;
                    this.y += this.speedY;

                    if (this.x < 0) this.x = canvas.width;
                    if (this.x > canvas.width) this.x = 0;
                    if (this.y < 0) this.y = canvas.height;
                    if (this.y > canvas.height) this.y = 0;
                }
                draw() {
                    ctx.fillStyle = `rgba(${this.color}, ${this.opacity})`;
                    ctx.beginPath();
                    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                    ctx.fill();
                }
            }

            function initParticles() {
                particlesArray = [];
                let numberOfParticles = (canvas.width * canvas.height) / 8000;
                for (let i = 0; i < numberOfParticles; i++) {
                    particlesArray.push(new Particle());
                }
            }

            function animateParticles() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                for (let i = 0; i < particlesArray.length; i++) {
                    particlesArray[i].update();
                    particlesArray[i].draw();
                }
                requestAnimationFrame(animateParticles);
            }

            initParticles();
            animateParticles();
        }

        // ЛОГИКА КАСТОМНОГО КУРСОРА
        if (window.matchMedia("(pointer: fine)").matches) {
            const cursorDot = document.getElementById('cursor-dot');
            const cursorRing = document.getElementById('cursor-ring');
            let mouseX = window.innerWidth / 2;
            let mouseY = window.innerHeight / 2;
            let ringX = mouseX;
            let ringY = mouseY;

            window.addEventListener('mousemove', (e) => {
                mouseX = e.clientX;
                mouseY = e.clientY;
                cursorDot.style.left = `${mouseX}px`;
                cursorDot.style.top = `${mouseY}px`;
            });

            function renderCursor() {
                ringX += (mouseX - ringX) * 0.15;
                ringY += (mouseY - ringY) * 0.15;
                
                cursorRing.style.left = `${ringX}px`;
                cursorRing.style.top = `${ringY}px`;
                
                requestAnimationFrame(renderCursor);
            }
            requestAnimationFrame(renderCursor);

            const interactiveElements = document.querySelectorAll('a, button, input, textarea, #retention-card, .lang-btn, i.fa-star');
            
            interactiveElements.forEach(el => {
                el.addEventListener('mouseenter', () => document.body.classList.add('cursor-hover'));
                el.addEventListener('mouseleave', () => document.body.classList.remove('cursor-hover'));
            });
            
            document.addEventListener('mousedown', () => document.body.classList.remove('cursor-hover'));
            document.addEventListener('mouseup', () => {
                if(document.querySelector('a:hover, button:hover')) {
                    document.body.classList.add('cursor-hover');
                }
            });
        }
    </script>
</body>
</html>
