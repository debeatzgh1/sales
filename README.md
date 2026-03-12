
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DEBEATZGH | Software Ecosystem</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;800&family=JetBrains+Mono&display=swap');

        :root {
            --accent: #00f2ff;
            --page-bg: #030712;
            --card-bg: rgba(15, 15, 18, 0.6);
            --nav-bg: rgba(10, 10, 12, 0.8);
            --text: #f0f6fc;
            --border: rgba(255, 255, 255, 0.08);
            --shimmer: rgba(255, 255, 255, 0.03);
        }

        body[data-theme="light"] {
            --page-bg: #f8fafc;
            --card-bg: rgba(255, 255, 255, 0.8);
            --nav-bg: rgba(255, 255, 255, 0.9);
            --text: #0f172a;
            --accent: #2563eb;
            --border: rgba(0, 0, 0, 0.08);
            --shimmer: rgba(0, 0, 0, 0.03);
        }

        body { background-color: var(--page-bg); color: var(--text); font-family: 'Plus Jakarta Sans', sans-serif; transition: background 0.4s ease; overflow-x: hidden; }

        /* 1. LAZY LOADING SKELETON ANIMATION */
        .skeleton { position: relative; overflow: hidden; background: var(--shimmer); }
        .skeleton::after {
            content: ""; position: absolute; inset: 0;
            background: linear-gradient(90deg, transparent, var(--shimmer), transparent);
            animation: shimmer 1.5s infinite;
        }
        @keyframes shimmer { 0% { transform: translateX(-100%); } 100% { transform: translateX(100%); } }

        /* 2. PROGRESS BAR & SLIM NAV */
        .progress-container { position: absolute; bottom: 0; left: 0; width: 100%; height: 2px; background: transparent; overflow: hidden; border-radius: 0 0 12px 12px; }
        .progress-bar { height: 100%; width: 0%; background: var(--accent); transition: width 0.1s ease; box-shadow: 0 0 10px var(--accent); }

        .slim-nav-container {
            position: fixed; top: 15px; left: 50%; transform: translateX(-50%);
            width: 92%; max-width: 800px; height: 46px;
            background: var(--nav-bg); backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
            border: 1px solid var(--border); border-radius: 14px;
            display: flex; align-items: center; justify-content: space-between;
            padding: 0 12px; z-index: 10000; transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .nav-up { transform: translateX(-50%) translateY(-100px); }

        /* 3. PREMIUM CARD STYLING */
        .hub-card {
            background: var(--card-bg); backdrop-filter: blur(16px);
            border: 1px solid var(--border); border-radius: 28px;
            transition: all 0.5s cubic-bezier(0.23, 1, 0.32, 1);
            position: relative; overflow: hidden; opacity: 0; transform: translateY(20px);
        }
        .hub-card.loaded { opacity: 1; transform: translateY(0); }
        .hub-card:hover { transform: translateY(-10px); border-color: var(--accent); box-shadow: 0 20px 40px rgba(0,0,0,0.3); }

        /* 4. MOUSE EXPLORE INDICATOR */
        .scroll-indicator { position: absolute; bottom: 30px; left: 50%; transform: translateX(-50%); animation: bounce 2s infinite; }
        @keyframes bounce { 0%, 20%, 50%, 80%, 100% {transform: translateY(0) translateX(-50%);} 40% {transform: translateY(-10px) translateX(-50%);} 60% {transform: translateY(-5px) translateX(-50%);} }

        /* 5. CANVAS & STATUS */
        #bg-canvas { position: fixed; inset: 0; z-index: -1; opacity: 0.4; pointer-events: none; }
        .status-pulse { width: 10px; height: 10px; background: #22c55e; border-radius: 50%; display: inline-block; box-shadow: 0 0 10px #22c55e; animation: pulse 2s infinite; }
        @keyframes pulse { 0%, 100% { opacity: 1; transform: scale(1); } 50% { opacity: 0.5; transform: scale(1.2); } }

        #portal-overlay { position: fixed; inset: 0; background: rgba(0,0,0,0.95); backdrop-filter: blur(20px); display: none; z-index: 20000; align-items: center; justify-content: center; }
        .portal-content { width: 95%; height: 90vh; background: #000; border-radius: 24px; overflow: hidden; border: 1px solid var(--border); }
    </style>
</head>
<body data-theme="dark">

    <canvas id="bg-canvas"></canvas>

    <nav id="slim-nav" class="slim-nav-container">
        <div class="flex items-center gap-3">
            <button class="w-8 h-8 rounded-lg flex items-center justify-center text-current hover:bg-white/10 transition" onclick="toggleTheme()">
                <i id="theme-icon" class="fas fa-moon"></i>
            </button>
            <div class="h-4 w-px bg-white/10 mx-1"></div>
            <span class="text-[10px] font-black uppercase tracking-widest cursor-pointer hover:text-cyan-400" onclick="window.open('https://debeatzgh1.github.io/Pages-/', '_blank')">
                Browse UI Layouts <i class="fas fa-arrow-right ml-1"></i>
            </span>
        </div>
        <div class="flex items-center gap-2">
            <button onclick="scrollToTop()" class="w-8 h-8 text-[10px]"><i class="fas fa-chevron-up"></i></button>
            <button onclick="scrollToBottom()" class="w-8 h-8 text-[10px]"><i class="fas fa-chevron-down"></i></button>
        </div>
        <div class="progress-container"><div id="scroll-bar" class="progress-bar"></div></div>
    </nav>

    <main class="max-w-6xl mx-auto px-6 pt-32 pb-20">
        <header class="mb-20 text-center relative" data-aos="fade-down">
            <h1 class="text-6xl font-black tracking-tighter mb-4">DEBEATZ<span class="text-cyan-400">GH</span></h1>
            <div class="flex items-center justify-center gap-6 font-mono text-[10px] uppercase tracking-widest opacity-60">
                <span><span class="status-pulse mr-2"></span>Systems Online</span>
                <span class="h-1 w-1 bg-white/20 rounded-full"></span>
                <span>Software Developer</span>
                <span class="h-1 w-1 bg-white/20 rounded-full"></span>
                <span>AI Strategist</span>
            </div>
            <div class="scroll-indicator text-slate-500 text-xs mt-12">
                <i class="fas fa-mouse"></i><br><i class="fas fa-chevron-down"></i>
            </div>
        </header>

        <div id="card-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            
            <div class="hub-card p-8 group skeleton" data-url="https://debeatzgh1.github.io/appdategh/">
                <div class="w-12 h-12 bg-cyan-500/10 rounded-2xl flex items-center justify-center text-cyan-400 mb-6 group-hover:scale-110 transition">
                    <i class="fab fa-android text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">AppDateGH</h3>
                <p class="text-sm opacity-50 leading-relaxed">Cross-platform entertainment repository & ecosystem.</p>
            </div>

            <div class="hub-card p-8 group skeleton" data-url="https://beatzde4.blogspot.com">
                <div class="w-12 h-12 bg-purple-500/10 rounded-2xl flex items-center justify-center text-purple-400 mb-6 group-hover:scale-110 transition">
                    <i class="fas fa-brain text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">Decode AI</h3>
                <p class="text-sm opacity-50 leading-relaxed">Automating business logic & generative content workflows.</p>
            </div>

            <div class="hub-card p-8 group skeleton" data-url="https://debeatzgh1.github.io/1">
                <div class="w-12 h-12 bg-blue-500/10 rounded-2xl flex items-center justify-center text-blue-400 mb-6 group-hover:scale-110 transition">
                    <i class="fab fa-google text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">G-Dev Node</h3>
                <p class="text-sm opacity-50 leading-relaxed">Google Developer credentials and verified cloud badges.</p>
            </div>

            <div class="hub-card p-8 group skeleton" data-url="https://debeatzgh1.github.io/blogs">
                <div class="w-12 h-12 bg-yellow-500/10 rounded-2xl flex items-center justify-center text-yellow-400 mb-6 group-hover:scale-110 transition">
                    <i class="fas fa-briefcase text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">Dkonsult</h3>
                <p class="text-sm opacity-50 leading-relaxed">Strategic technical consulting & premium software services.</p>
            </div>

            <div class="hub-card p-8 group skeleton" data-external="true" data-url="https://github.com/debeatzgh1">
                <div class="w-12 h-12 bg-white/10 rounded-2xl flex items-center justify-center text-white mb-6 group-hover:scale-110 transition">
                    <i class="fab fa-github text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">Source Code</h3>
                <p class="text-sm opacity-50 leading-relaxed">Open-source contributions and development repositories.</p>
            </div>

            <div class="hub-card p-8 border-dashed border-cyan-500/30 group skeleton" onclick="openContact()">
                <div class="w-12 h-12 bg-red-500/10 rounded-2xl flex items-center justify-center text-red-500 mb-6 group-hover:scale-110 transition">
                    <i class="fas fa-paper-plane text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">Collab Space</h3>
                <p class="text-sm opacity-50 leading-relaxed">Ready to build? Send your project brief directly.</p>
            </div>
        </div>
    </main>

    <div id="portal-overlay">
        <div class="portal-content">
            <div class="px-6 py-4 bg-black/80 flex justify-between items-center border-b border-white/10">
                <span id="portal-title" class="text-[10px] font-mono uppercase text-cyan-400 tracking-widest">Node Initialized</span>
                <button onclick="closePortal()" class="w-8 h-8 rounded-full hover:bg-red-500/20 text-red-500 transition"><i class="fas fa-times"></i></button>
            </div>
            <iframe id="portal-frame" src="" class="w-full h-full"></iframe>
        </div>
    </div>

    <a href="https://wa.me/233270201181?text=Project%20Inquiry" target="_blank" class="fixed bottom-6 right-6 flex items-center gap-3 bg-[#25D366] text-white px-6 py-3 rounded-2xl font-black text-xs uppercase tracking-tighter shadow-2xl hover:scale-105 transition-all z-[500]">
        <i class="fab fa-whatsapp text-lg"></i> Hire Me
    </a>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        AOS.init({ duration: 800, once: true });

        // --- LAZY LOADING & INTERSECTION OBSERVER ---
        document.addEventListener("DOMContentLoaded", () => {
            const cards = document.querySelectorAll('.hub-card');
            
            const observer = new IntersectionObserver((entries) => {
                entries.forEach((entry, index) => {
                    if (entry.isIntersecting) {
                        setTimeout(() => {
                            entry.target.classList.remove('skeleton');
                            entry.target.classList.add('loaded');
                            
                            // Attach Click Events only after loading
                            const url = entry.target.getAttribute('data-url');
                            const isExternal = entry.target.getAttribute('data-external');
                            
                            if(url) {
                                entry.target.onclick = () => {
                                    if(isExternal) window.open(url, '_blank');
                                    else openPortal(url);
                                };
                            }
                        }, index * 100); // Staggered entrance
                        observer.unobserve(entry.target);
                    }
                });
            }, { threshold: 0.1 });

            cards.forEach(card => observer.observe(card));
        });

        // --- THEME ENGINE ---
        function toggleTheme() {
            const b = document.body;
            const icon = document.getElementById('theme-icon');
            if(b.getAttribute('data-theme') === 'dark') {
                b.setAttribute('data-theme', 'light');
                icon.className = 'fas fa-sun';
                localStorage.setItem('theme', 'light');
            } else {
                b.setAttribute('data-theme', 'dark');
                icon.className = 'fas fa-moon';
                localStorage.setItem('theme', 'dark');
            }
        }
        if(localStorage.getItem('theme') === 'light') toggleTheme();

        // --- STICKY NAV & PROGRESS BAR ---
        let lastScroll = 0;
        window.addEventListener('scroll', () => {
            const nav = document.getElementById('slim-nav');
            const bar = document.getElementById('scroll-bar');
            const currentScroll = window.scrollY;
            
            const winScroll = document.body.scrollTop || document.documentElement.scrollTop;
            const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrolled = (winScroll / height) * 100;
            bar.style.width = scrolled + "%";

            if (currentScroll > lastScroll && currentScroll > 100) nav.classList.add('nav-up');
            else nav.classList.remove('nav-up');
            lastScroll = currentScroll;
        });

        // --- PORTAL LOGIC ---
        function openPortal(url) {
            const overlay = document.getElementById('portal-overlay');
            document.getElementById('portal-frame').src = url;
            document.getElementById('portal-title').innerText = "Accessing: " + url;
            overlay.style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }

        function closePortal() {
            document.getElementById('portal-overlay').style.display = 'none';
            document.getElementById('portal-frame').src = "";
            document.body.style.overflow = 'auto';
        }

        function scrollToTop() { window.scrollTo({top: 0, behavior: 'smooth'}); }
        function scrollToBottom() { window.scrollTo({top: document.body.scrollHeight, behavior: 'smooth'}); }
        
        function openContact() {
            alert("Official Contact Details:\nEmail: debeatz4@gmail.com\nWhatsApp: +233 27 020 1181");
        }

        // --- BACKGROUND PARTICLES ---
        const canvas = document.getElementById('bg-canvas');
        const ctx = canvas.getContext('2d');
        let particles = [];
        function initCanvas() { canvas.width = window.innerWidth; canvas.height = window.innerHeight; }
        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 2;
                this.speedX = Math.random() * 0.5 - 0.25;
                this.speedY = Math.random() * 0.5 - 0.25;
            }
            update() {
                this.x += this.speedX; this.y += this.speedY;
                if (this.x > canvas.width) this.x = 0; if (this.x < 0) this.x = canvas.width;
                if (this.y > canvas.height) this.y = 0; if (this.y < 0) this.y = canvas.height;
            }
            draw() {
                ctx.fillStyle = document.body.getAttribute('data-theme') === 'light' ? '#cbd5e1' : '#1e293b';
                ctx.beginPath(); ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2); ctx.fill();
            }
        }
        for (let i = 0; i < 80; i++) particles.push(new Particle());
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => { p.update(); p.draw(); });
            requestAnimationFrame(animate);
        }
        window.addEventListener('resize', initCanvas);
        initCanvas(); animate();
    </script>
</body>
</html>
