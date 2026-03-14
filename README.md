<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>G-Dev Portfolio | Hiring Portal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Google+Sans:wght@400;500;700&display=swap');

        :root {
            --g-blue: #8ab4f8;
            --g-green: #34A853;
            --dark-bg: #1a1c1e;
            --dark-card: #2d2f31;
            --glass-border: rgba(255, 255, 255, 0.08);
        }

        body { font-family: 'Google Sans', sans-serif; background: #121212; margin: 0; }

        /* 1. LAUNCHER */
        #gdev-launcher {
            position: fixed; left: 20px; top: 50%; transform: translateY(-50%);
            display: flex; align-items: center; gap: 12px;
            background: var(--dark-card); padding: 8px 18px 8px 8px;
            border-radius: 40px; cursor: pointer; z-index: 9999;
            box-shadow: 0 10px 40px rgba(0,0,0,0.5);
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: 1px solid var(--glass-border);
        }

        #gdev-launcher:hover { transform: translateY(-50%) scale(1.08) translateX(5px); border-color: var(--g-blue); }

        .dev-avatar {
            width: 30px; height: 30px; background: #121212; border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            border: 2px solid var(--g-blue); color: var(--g-blue); position: relative;
        }

        .status-dot {
            position: absolute; bottom: 2px; right: 2px; width: 10px; height: 10px;
            background: var(--g-green); border-radius: 50%; border: 2px solid var(--dark-card);
        }

        .status-glow {
            position: absolute; inset: 0; background: var(--g-green);
            border-radius: 50%; animation: status-pulse 2s infinite;
        }

        @keyframes status-pulse { 0% { transform: scale(1); opacity: 0.8; } 100% { transform: scale(2.5); opacity: 0; } }

        /* 2. OVERLAY MODAL */
        #gdev-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.85);
            backdrop-filter: blur(12px); display: none; z-index: 10000;
            justify-content: center; align-items: center; padding: 20px;
            opacity: 0; transition: opacity 0.4s ease;
        }

        #gdev-overlay.active { display: flex; opacity: 1; }

        .gdev-modal {
            width: 100%; max-width: 950px; height: 92vh;
            background: var(--dark-bg); border-radius: 28px;
            display: flex; flex-direction: column; overflow: hidden;
            border: 1px solid var(--glass-border); position: relative;
        }

        /* 3. IFRAME & FOOTER */
        #gdev-frame { flex-grow: 1; width: 100%; border: none; background: #fff; }

        .close-gdev {
            position: absolute; top: 20px; right: 25px; width: 40px; height: 30px;
            background: var(--dark-card); border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            cursor: pointer; color: #fff; z-index: 20;
        }

        /* CONTACT ME BUTTON STYLE */
        .hire-btn {
            background: var(--g-green);
            color: white;
            padding: 8px 18px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: 800;
            text-transform: uppercase;
            letter-spacing: 1px;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: 0.3s;
            box-shadow: 0 4px 15px rgba(52, 168, 83, 0.3);
        }
        .hire-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(52, 168, 83, 0.4); background: #2e964a; }

        @media (max-width: 768px) {
            .gdev-modal { height: 100vh; border-radius: 0; }
            .footer-controls { flex-direction: column; gap: 10px; padding: 15px; }
        }
    </style>
</head>
<body>

    <div id="gdev-launcher" onclick="toggleGDev()">
        <div class="dev-avatar">
            <i class="fab fa-google"></i>
            <div class="status-dot"><div class="status-glow"></div></div>
        </div>
        <div class="hidden sm:block">
            <div class="flex items-center gap-2">
                <span class="text-[9px] text-[#34A853] font-bold uppercase tracking-widest">Active</span>
            </div>
            <p class="text-[14px] font-medium text-gray-200">@debeatzgh</p>
        </div>
    </div>

    <div id="gdev-overlay">
        <div class="gdev-modal">
            <div class="close-gdev" onclick="toggleGDev()"><i class="fas fa-times"></i></div>
            
            <iframe id="gdev-frame" src=""></iframe>

            <div class="footer-controls p-4 bg-[#1a1c1e] border-t border-white/5 flex justify-between items-center px-8">
                <span class="text-[9px] text-gray-600 font-bold uppercase tracking-[2px]">G-Dev Protocol v4.0</span>
                
                <div class="flex items-center gap-3">
                    <button id="copy-btn" class="text-[11px] text-[#8ab4f8] font-bold px-4 py-2 hover:text-white transition" onclick="copyProfileLink()">
                        Copy Profile
                    </button>
                    <a href="https://wa.me/233549757544?text=Hi%20DeBeatz,%20I%20saw%20your%20Google%20Dev%20profile%20and%20would%20like%20to%20discuss%20a%20project." 
                       target="_blank" class="hire-btn">
                        <i class="fas fa-briefcase"></i> Contact Me
                    </a>
                </div>
            </div>
        </div>
    </div>

    <script>
        const overlay = document.getElementById('gdev-overlay');
        const frame = document.getElementById('gdev-frame');
        const profileUrl = "https://docs.google.com/forms/d/e/1FAIpQLSdipVP7tU1hjTjECfWUdnhzWN-PROdQp19ng25EUDJk5-8JzA/viewform?usp=header";

        function toggleGDev() {
            if (overlay.style.display === 'flex') {
                overlay.classList.remove('active');
                setTimeout(() => { overlay.style.display = 'none'; frame.src = ""; }, 400);
                document.body.style.overflow = 'auto';
            } else {
                overlay.style.display = 'flex';
                setTimeout(() => overlay.classList.add('active'), 10);
                frame.src = profileUrl;
                document.body.style.overflow = 'hidden';
            }
        }

        async function copyProfileLink() {
            await navigator.clipboard.writeText(profileUrl);
            const btn = document.getElementById('copy-btn');
            btn.innerText = "Copied!";
            setTimeout(() => { btn.innerText = "Copy Profile"; }, 2000);
        }

        overlay.onclick = (e) => { if (e.target === overlay) toggleGDev(); };
    </script>
</body>
</html>





<div id="smart-float-container" class="float-wrapper">
    <div id="float-nudge" class="float-nudge">
        <p>Claim your <strong>.wordpress.com</strong> site!</p>
        <button onclick="dismissNudge()" class="nudge-close">×</button>
    </div>

    <div class="float-main-btn" onclick="launchWPSignup()">
        <i class="fab fa-wordpress"></i>
        <span class="btn-label">Create Site</span>
    </div>
</div>

<style>
    .float-wrapper {
        position: fixed;
        bottom: 20px;
        left: 40%;
        transform: translateX(-50%);
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 12px;
        z-index: 10005;
        font-family: 'Plus Jakarta Sans', sans-serif;
    }

    /* Floating Nudge Bubble */
    .float-nudge {
        background: rgba(10, 10, 12, 0.9);
        backdrop-filter: blur(10px);
        border: 1px solid rgba(0, 242, 255, 0.3);
        padding: 8px 15px;
        border-radius: 12px;
        color: #f0f6fc;
        font-size: 11px;
        white-space: nowrap;
        box-shadow: 0 10px 25px rgba(0,0,0,0.5);
        display: none; /* Controlled by JS */
        animation: slideUpFade 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        align-items: center;
        gap: 10px;
    }

    .nudge-close {
        background: none;
        border: none;
        color: #64748b;
        font-size: 16px;
        cursor: pointer;
        padding: 0 2px;
        line-height: 1;
    }

    .nudge-close:hover { color: #00f2ff; }

    /* Main Button */
    .float-main-btn {
        background: #00f2ff;
        color: #000;
        padding: 10px 20px;
        border-radius: 99px;
        display: flex;
        align-items: center;
        gap: 8px;
        cursor: pointer;
        font-weight: 800;
        text-transform: uppercase;
        font-size: 10px;
        letter-spacing: 1px;
        box-shadow: 0 0 20px rgba(0, 242, 255, 0.3);
        transition: all 0.3s ease;
    }

    .float-main-btn:hover {
        transform: translateY(-3px) scale(1.05);
        background: #fff;
        box-shadow: 0 0 30px rgba(255, 255, 255, 0.4);
    }

    .float-main-btn i { font-size: 14px; }

    @keyframes slideUpFade {
        from { opacity: 0; transform: translateY(15px); }
        to { opacity: 1; transform: translateY(0); }
    }

    @media (max-width: 480px) {
        .float-main-btn { padding: 10px 16px; }
        .btn-label { display: none; } /* On mobile, only show icon to save space */
    }
</style>

<script>
    const NUDGE_KEY = 'wp_nudge_dismissed';

    function showNudge() {
        const isDismissed = localStorage.getItem(NUDGE_KEY);
        if (!isDismissed) {
            document.getElementById('float-nudge').style.display = 'flex';
        }
    }

    function dismissNudge() {
        document.getElementById('float-nudge').style.display = 'none';
        // Remember dismissal for 24h
        localStorage.setItem(NUDGE_KEY, 'true');
    }

    function launchWPSignup() {
        const targetUrl = "https://debeatzgh1.github.io/Blogger-sign-up-button-/";
        
        // Use existing overlay logic if available
        if (typeof openLink === "function") {
            openLink(targetUrl);
        } else if (typeof openFrame === "function") {
            openFrame(targetUrl);
        } else {
            window.open(targetUrl, '_blank');
        }
    }

    // Auto-popup nudge after 8 seconds
    window.addEventListener('load', () => {
        setTimeout(showNudge, 8000);
    });
</script>


<div id="wp-identity-popup" class="wp-popup-overlay">
    <div class="wp-popup-card">
        <button onclick="closeWPPopup()" class="wp-close-btn">
            <i class="fas fa-times"></i>
        </button>

        <div class="wp-header">
            <div class="wp-icon-box">
                <i class="fab fa-wordpress text-2xl text-white"></i>
            </div>
            <div class="wp-badge">Free Lifetime Access</div>
        </div>

        <div class="wp-body">
            <h2 class="wp-title">Secure Your <span class="text-cyan-400">Identity</span></h2>
            
            <div class="wp-slider-container">
                <div class="wp-slider-track">
                    <div class="wp-slide">Create <strong>name.debeatzgh.com</strong> today.</div>
                    <div class="wp-slide">Professional hosting, $0.00 cost.</div>
                    <div class="wp-slide">Launch your portfolio in 60 seconds.</div>
                </div>
            </div>

            <p class="wp-description">
                .
            </p>

            <button onclick="launchWPSignup()" class="wp-submit-btn">
                <span>Create My Free Site</span>
                <i class="fas fa-arrow-right ml-2"></i>
            </button>
            
            <p class="text-[9px] text-gray-500 mt-4 uppercase tracking-[0.2em]">No credit card required • Instant Activation</p>
        </div>
    </div>
</div>



# 💎 Digital Ecosystem Hub

**A High-Performance Portal for AI Automation, Software Development, and Digital Strategy.**

This repository contains UI, the source code for the **DeBeatzGH Hub**, a unified interface designed to host multiple digital nodes (AppDateGH, Decode AI, G-Dev) within a single, high-conversion ecosystem. Built with a "SaaS-first" aesthetic, it utilizes advanced browser APIs for a smooth, app-like experience.

---

## 🚀 Premium Engineering Features

### ⚡ Performance & Lazy Loading

* **Intersection Observer Logic:** Service cards utilize an observer to trigger entrance animations only when they enter the viewport.
* **Skeleton Screens:** Implements shimmering placeholders while content is initializing, ensuring a high "Perceived Speed" for users on slower connections.
* **Lazy Portal Injection:** External project nodes (iframes) are only loaded into the DOM upon a user's click, saving bandwidth and keeping the main hub lightweight.

### 🛠️ Smart UI Systems

* **Sticky-Hide Navigation:** A slim utility bar that hides on scroll-down to maximize screen real estate and reappears on scroll-up for instant navigation.
* **Reading Progress Engine:** A visual bar integrated into the navigation strip that tracks user engagement in real-time.
* **Cyber-Hybrid Theme Engine:** Full support for **Cyber Dark** and **Studio Light** modes with `localStorage` persistence and smooth color-bleed transitions.

### 🎨 Visual Identity

* **Ambient Particle Canvas:** A lightweight HTML5 Canvas engine that generates a dynamic, tech-focused atmosphere without affecting scroll performance.
* **Bento-Grid Architecture:** A responsive layout utilizing glassmorphism and Tailwind CSS for a professional, verified developer aesthetic.

---

## 🛠️ Technical Stack

| Category | Technology |
| --- | --- |
| **Framework** | [Tailwind CSS](https://tailwindcss.com/) |
| **Animations** | [AOS (Animate On Scroll)](https://michalsnik.github.io/aos/) |
| **Icons** | [FontAwesome 6.4](https://fontawesome.com/) |
| **Fonts** | Plus Jakarta Sans & JetBrains Mono |
| **Core Logic** | Vanilla JavaScript (ES6+) |
| **Rendering** | HTML5 Canvas API |

---

## 📂 Deployment & Customization

1. **Clone the Repo:**
```bash
git clone https://github.com/debeatzgh1/debeatzgh1.github.io.git

```


2. **Update Links:**
* Open `index.html` and modify the `data-url` attributes on the `.hub-card` elements to point to your specific project nodes.


3. **Deploy to GitHub Pages:**
* Push to your `main` branch.
* Go to **Settings > Pages** and set the source to `main / (root)`.



---

## ⚖️ License & Contact

**Engineered by DeBeatzGH.** 🚀

*Digital Strategist | Software Developer | AI Architect*

* **WhatsApp:** [+233 549757544](https://www.google.com/search?q=https://wa.me/233549757544)
* **Email:** debeatz4@gmail.com
* **Hub:** [debeatzgh1.github.io](https://www.google.com/search?q=https://debeatzgh1.github.io/)




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
            <span class="text-[10px] font-black uppercase tracking-widest cursor-pointer hover:text-cyan-400" onclick="window.open('https://debeatzgh1.github.io/-Firebase-Login-Popup/', '_blank')">
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
