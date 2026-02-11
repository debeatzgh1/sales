<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Debeatzgh Startup & Funding FAQ</title>
    <style>
        :root {
            --bg: #0d1117;
            --card-bg: #161b22;
            --border: #30363d;
            --accent: #58a6ff;
            --premium: #d29922;
            --text-main: #c9d1d9;
            --text-dim: #8b949e;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif;
            background-color: var(--bg);
            color: var(--text-main);
            margin: 0;
            padding: 40px 20px;
            line-height: 1.6;
        }

        .header {
            text-align: center;
            margin-bottom: 50px;
        }

        .header h1 {
            font-size: 2.5rem;
            color: white;
            letter-spacing: -1px;
        }

        .main-layout {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            max-width: 1200px;
            margin: auto;
        }

        @media (max-width: 900px) {
            .main-layout { grid-template-columns: 1fr; }
        }

        /* Styling Components */
        h2 {
            font-size: 1.25rem;
            border-bottom: 1px solid var(--border);
            padding-bottom: 10px;
            color: var(--accent);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        details {
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 6px;
            margin-bottom: 12px;
            transition: all 0.3s ease;
        }

        details:hover { border-color: #8b949e; }

        summary {
            padding: 12px 15px;
            cursor: pointer;
            font-weight: 600;
            outline: none;
            list-style: none;
        }

        summary::-webkit-details-marker { display: none; }

        details p {
            padding: 0 15px 15px 15px;
            margin: 0;
            color: var(--text-dim);
            font-size: 0.95rem;
        }

        .premium { border-left: 4px solid var(--premium); }
        .premium summary { color: var(--premium); }

        /* Auto-Slide Logic */
        .slider-container {
            position: relative;
            height: 100%;
        }

        .slide {
            display: none;
            animation: fadeIn 0.8s ease-in-out;
        }

        .slide.active { display: block; }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .badge {
            font-size: 0.7rem;
            background: #238636;
            color: white;
            padding: 2px 8px;
            border-radius: 10px;
            vertical-align: middle;
        }
    </style>
</head>
<body>

    <div class="header">
        <h1>Startup, Funding & AI <span style="font-weight: 200; color: var(--text-dim);">Hub</span></h1>
    </div>

    <div class="main-layout">
        
        <div class="stable-section">
            <h2>Funding & Investment</h2>
            <details>
                <summary>What does “Funding is fuel, not the engine” mean?</summary>
                <p>Funding accelerates growth but does not create a viable business. A strong engine—customers, execution, and cash flow—must exist first.</p>
            </details>
            <details>
                <summary>What is the engine of a startup?</summary>
                <p>The engine includes a real problem, a working solution, paying customers, and sustainable cash flow.</p>
            </details>
            <details class="premium">
                <summary>What do African investors care about most? ★</summary>
                <p>Execution ability, founder resilience, understanding of local markets, and realistic revenue models.</p>
            </details>

            <h2 style="margin-top: 40px;">Startups & Growth</h2>
            <details>
                <summary>Why do most startups fail?</summary>
                <p>Most fail due to poor execution, lack of market need, and building without validation.</p>
            </details>
            <details>
                <summary>Growth vs. Scaling?</summary>
                <p>Growth means increasing effort to grow. Scaling means growing revenue without increasing costs at the same rate.</p>
            </details>
        </div>

        <div class="slider-container">
            
            <div class="slide active">
                <h2>AI & Technology <span class="badge">Auto-Updating</span></h2>
                <details>
                    <summary>Can African startups use AI without big budgets?</summary>
                    <p>Yes. Tools like ChatGPT, Claude, and Canva offer affordable plans for automation and research.</p>
                </details>
                <details class="premium">
                    <summary>What AI mistakes should startups avoid? ★</summary>
                    <p>Using AI just because it’s trendy and relying on it without understanding the core business problem.</p>
                </details>
            </div>

            <div class="slide">
                <h2>Side Hustles & Content <span class="badge">Auto-Updating</span></h2>
                <details>
                    <summary>How can skills turn into side hustles?</summary>
                    <p>Monetize skills like writing or tech through freelancing and digital products.</p>
                </details>
                <details>
                    <summary>Why treat a side hustle like a business?</summary>
                    <p>Tracking income and growth helps side hustles become sustainable income streams.</p>
                </details>
            </div>

            <div class="slide">
                <h2>Platform & Learning <span class="badge">Auto-Updating</span></h2>
                <details>
                    <summary>What is included in the premium version?</summary>
                    <p>Advanced lessons, investor insights, and downloadable African case studies.</p>
                </details>
                <details class="premium">
                    <summary>Why lock content behind premium? ★</summary>
                    <p>Premium access sustains the platform and rewards committed learners.</p>
                </details>
            </div>

        </div>
    </div>

    <script>
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');

        function showNextSlide() {
            slides[currentSlide].classList.remove('active');
            currentSlide = (currentSlide + 1) % slides.length;
            slides[currentSlide].classList.add('active');
        }

        // Change slide every 5 seconds
        setInterval(showNextSlide, 5000);
    </script>

</body>
</html>



<style>
/* ❤️ Heartbeat Animation */
@keyframes heartbeat {
  0% { transform: scale(1); }
  30% { transform: scale(1.1); }
  50% { transform: scale(1); }
  70% { transform: scale(1.15); }
  100% { transform: scale(1); }
}

/* 🔘 Floating Button (TOP RIGHT – SMALL) */
.floating-btn {
  position: fixed;
  bottom: 14px;
  left: 14px;
  z-index: 9999;
  animation: heartbeat 1.8s infinite;
}

.floating-btn a {
  background: #1e90ff;
  color: #fff;
  padding: 6px 9px;
  border-radius: 14px;
  font-size: 11px;
  font-weight: 600;
  text-decoration: none;
  box-shadow: 0 2px 6px rgba(0,0,0,0.25);
}

/* 🪟 Modal Overlay */
#iframe-modal {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.7);
  backdrop-filter: blur(4px);
  z-index: 99999;
}

/* 📦 Modal Box */
.modal-box {
  position: relative;
  margin: 2% auto;
  width: 98%;
  height: 100%;
  background: #fff;
  border-radius: 16px;
  overflow: hidden;
}

/* 🧭 Toolbar */
.modal-toolbar {
  position: absolute;
  top: 8px;
  left: 10px;
  right: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  z-index: 10;
}

.modal-toolbar button {
  background: #111;
  color: #fff;
  border: none;
  padding: 7px 10px;
  border-radius: 8px;
  font-size: 12px;
  cursor: pointer;
}

#modal-iframe {
  width: 100%;
  height: 107%;
  border: none;
}
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {

  /* 🌐 Pages */
  const pages = [
    "https://debeatzgh1.github.io/blogs/"
  ];

  let index = 0;

  /* 🔘 Floating Button */
  const floatBtn = document.createElement("div");
  floatBtn.className = "floating-btn";
  floatBtn.innerHTML = `<a href="#">🌐 Blogs</a>`;
  document.body.appendChild(floatBtn);

  /* 🪟 Modal */
  const modal = document.createElement("div");
  modal.id = "iframe-modal";
  modal.innerHTML = `
    <div class="modal-box">
      <div class="modal-toolbar">
        <div>
          <button id="prevBtn">◀ Prev</button>
          <button id="nextBtn">Next ▶</button>
        </div>
        <button id="closeBtn">✖</button>
      </div>

      <iframe
        id="modal-iframe"
        loading="lazy"
        sandbox="allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-forms"
        allow="autoplay; encrypted-media; picture-in-picture"
        referrerpolicy="no-referrer-when-downgrade">
      </iframe>
    </div>
  `;
  document.body.appendChild(modal);

  const iframe = document.getElementById("modal-iframe");

  function openModal() {
    iframe.src = pages[index];
    modal.style.display = "block";
  }

  function closeModal() {
    modal.style.display = "none";
    iframe.src = "";
  }

  function toggleModal() {
    if (modal.style.display === "block") {
      closeModal();
    } else {
      openModal();
    }
  }

  /* 🔘 Floating Button Toggle */
  floatBtn.onclick = function (e) {
    e.preventDefault();
    toggleModal();
  };

  /* ⏭ Navigation */
  document.getElementById("nextBtn").onclick = function () {
    index = (index + 1) % pages.length;
    openModal();
  };

  document.getElementById("prevBtn").onclick = function () {
    index = (index - 1 + pages.length) % pages.length;
    openModal();
  };

  /* ❌ Close */
  document.getElementById("closeBtn").onclick = closeModal;
  modal.onclick = e => e.target === modal && closeModal();

});
</script></!doctype>





<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Debeatzgh – African Startup Series</title>

<style>
body{
  margin:0;
  font-family:Arial, sans-serif;
  background:#020617;
  color:#e5e7eb;
}

/* Floating Button */
#launchBtn{
  position:fixed;
  top:20px;
  right:20px;
  background:#22c55e;
  color:#000;
  padding:14px 20px;
  border-radius:30px;
  font-weight:bold;
  cursor:pointer;
  z-index:1000;
}

/* Tabs */
.tabs{
  display:flex;
  justify-content:center;
  gap:10px;
  margin-top:80px;
}

.tabs button{
  background:#0f172a;
  color:#22c55e;
  border:1px solid #22c55e;
  padding:10px 16px;
  border-radius:20px;
  cursor:pointer;
  font-weight:bold;
}

/* Carousel */
.carousel{
  max-width:1000px;
  margin:20px auto;
  overflow:hidden;
  position:relative;
  display:none;
  border-radius:16px;
}

.track{
  display:flex;
  transition:transform .6s ease;
}

.slide{
  min-width:100%;
  padding:50px;
  background:#020617;
}

.slide h2{color:#22c55e;}

.slide button{
  margin-top:20px;
  background:#22c55e;
  border:none;
  padding:12px 20px;
  border-radius:8px;
  font-weight:bold;
  cursor:pointer;
}

/* Nav */
.nav{
  position:absolute;
  top:50%;
  transform:translateY(-50%);
  background:rgba(0,0,0,.6);
  padding:12px;
  border-radius:50%;
  cursor:pointer;
}

.prev{left:10px;}
.next{right:10px;}

/* Iframe Viewer */
#viewer{
  display:none;
  position:fixed;
  inset:0;
  background:#020617;
  z-index:2000;
}

#viewer iframe{
  width:100%;
  height:100%;
  border:none;
}

#closeViewer{
  position:absolute;
  top:15px;
  right:20px;
  background:#22c55e;
  color:#000;
  padding:10px 14px;
  border-radius:20px;
  cursor:pointer;
  font-weight:bold;
}
</style>
</head>

<body>

<div id="launchBtn">🚀 Launch Startup Series</div>

<div class="tabs" id="tabs">
  <button onclick="filterSlides('all')">All</button>
  <button onclick="filterSlides('startup')">Startups</button>
  <button onclick="filterSlides('ai')">AI</button>
  <button onclick="filterSlides('content')">Content</button>
</div>

<div class="carousel" id="carousel">
  <div class="track" id="track"></div>
  <div class="nav prev" onclick="move(-1)">❮</div>
  <div class="nav next" onclick="move(1)">❯</div>
</div>

<!-- Docs Viewer -->
<div id="viewer">
  <div id="closeViewer" onclick="closeViewer()">✕ Close</div>
  <iframe id="docFrame"></iframe>
</div>

<script>
let index=0, auto;
const track=document.getElementById("track");

const DOC_URL="https://docs.google.com/document/d/1ECpgcokd44w2MbWbYMvykJ1CLoeU1eMa/edit?usp=drivesdk&ouid=116845182021782803040&rtpof=true&sd=true";

const posts=[
 {n:1,t:"African Startup Foundations",c:"startup"},
 {n:2,t:"Validating Startup Ideas",c:"startup"},
 {n:3,t:"Funding Without VC",c:"startup"},
 {n:4,t:"Building Trust in Markets",c:"startup"},
 {n:5,t:"AI Opportunities for Founders",c:"ai"},
 {n:6,t:"Startup Mistakes to Avoid",c:"startup"},
 {n:7,t:"Trust as Growth Strategy",c:"startup"},
 {n:8,t:"Country-Based Opportunities",c:"startup"},
 {n:9,t:"Monetization Models",c:"startup"},
 {n:10,t:"Scaling Sustainably",c:"startup"},
 {n:11,t:"AI + Side Hustles",c:"ai"},
 {n:12,t:"Content to Income",c:"content"}
];

function render(category="all"){
  track.innerHTML="";
  posts.filter(p=>category==="all"||p.c===category)
    .forEach(p=>{
      track.innerHTML+=`
      <div class="slide">
        <h2>Post #${p.n} – ${p.t}</h2>
        <p>Premium African-focused insights designed for founders and creators.</p>
        <button onclick="openDoc()">Read Full Post</button>
      </div>`;
    });
  index=0;
  move(0);
}

function move(step){
  const slides=document.querySelectorAll(".slide");
  index=(index+step+slides.length)%slides.length;
  track.style.transform=`translateX(-${index*100}%)`;
}

function startAuto(){ auto=setInterval(()=>move(1),4000); }
function stopAuto(){ clearInterval(auto); }

function filterSlides(cat){ render(cat); }

function openDoc(){
  document.getElementById("viewer").style.display="block";
  document.getElementById("docFrame").src=DOC_URL;
}

function closeViewer(){
  document.getElementById("viewer").style.display="none";
  document.getElementById("docFrame").src="";
}

document.getElementById("launchBtn").onclick=()=>{
  document.getElementById("carousel").style.display="block";
  render();
  startAuto();
};

document.getElementById("carousel").addEventListener("mouseenter",stopAuto);
document.getElementById("carousel").addEventListener("mouseleave",startAuto);
</script>

</body>
</html>



<html lang="en">
<head>
<meta charset="UTF-8">
<title>Debeatzgh – Digital Feed</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">

<style>
:root{
  --bg:#020617;
  --card:rgba(255,255,255,.06);
  --accent:#38bdf8;
}

*{box-sizing:border-box}

body{
  margin:0;
  font-family:system-ui,-apple-system;
  background:var(--bg);
  color:#e5e7eb;
}

/* HEADER */
header{
  padding:20px;
  text-align:center;
  border-bottom:1px solid rgba(255,255,255,.08);
}

header h1{
  color:var(--accent);
  font-size:1.4rem;
}

header p{
  font-size:.85rem;
  opacity:.8;
}

/* FEED */
.feed{
  max-width:1100px;
  margin:auto;
  padding:20px;
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(280px,1fr));
  gap:18px;
}

/* CARD */
.item{
  background:var(--card);
  border-radius:16px;
  padding:16px;
  display:flex;
  flex-direction:column;
  gap:10px;
  transition:.25s;
}

.item:hover{
  transform:translateY(-6px);
  background:rgba(56,189,248,.15);
}

.badge{
  font-size:.7rem;
  padding:4px 8px;
  border-radius:10px;
  background:rgba(56,189,248,.2);
  width:fit-content;
}

.item h3{
  font-size:1rem;
}

.item p{
  font-size:.8rem;
  opacity:.85;
  line-height:1.4;
}

.item a{
  margin-top:auto;
  font-size:.8rem;
  color:#020617;
  background:var(--accent);
  padding:8px 12px;
  border-radius:10px;
  text-decoration:none;
  width:fit-content;
}
</style>
</head>

<body>

<header>
  <h1>Content & Blogs</h1>
  <p>Latest blogs, updates & GitHub pages</p>
</header>

<section class="feed" id="feed"></section>

<script>
const feedItems=[
  {
    type:"Blog",
    title:"online business Blog",
    desc:"AI tools, digital asset strategies & tech education.",
    url:"https://debeatzgh1.blogspot.com/"
  },
  {
    type:"Blog",
    title:"E-Hub",
    desc:"Entertainment and more.",
    url:"https://appdategh.blogspot.com/"
  },
  {
    type:"Blog",
    title:"creators Hub",
    desc:"Widgets, html previews and updates.",
    url:"https://beatzde4.blogspot.com/"
  },
  {
    type:"Blog",
    title:"Guide to AI",
    desc:"Extended blogging, Decoding AI & tutorials.",
    url:"https://debeatzgh2.blogspot.com/"
  },
  {
    type:"Blog",
    title:"products recommendations",
    desc:"AI powered brands and digital products hub.",
    url:"https://mybrandsonline.blogspot.com/"
  },
  {
    type:"Blog",
    title:"Side hustle",
    desc:"Side hustles, services & digital creation content.",
    url:"https://digimartgh.blogspot.com/"
  },
  {
    type:"links",
    title:"Home page",
    desc:"Premium long-form content and guides.",
    url:"https://debeatzgh1.github.io/Home-/"
  },
  {
    type:"GitHub",
    title:"main menu",
    desc:"Launcher pages and interactive tools.",
    url:"https://debeatzgh1.github.io/1/"
  },
  {
    type:"assistants",
    title:"Chat AI",
    desc:"Delve into personal research with AI assistants.",
    url:"https://debeatzgh1.github.io/ai-chat/"
  }
];

const feed=document.getElementById("feed");

feedItems.forEach(i=>{
  const card=document.createElement("div");
  card.className="item";
  card.innerHTML=`
    <span class="badge">${i.type}</span>
    <h3>${i.title}</h3>
    <p>${i.desc}</p>
    <a href="${i.url}" target="_blank">Open</a>
  `;
  feed.appendChild(card);
});
</script>

</body>
</html>


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Premium Digital Hub</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #2563eb;
            --secondary: #0f172a;
            --accent: #38bdf8;
            --bg: #f8fafc;
            --card-bg: #ffffff;
            --text: #0f172a;
            --glass: rgba(255, 255, 255, 0.9);
            --transition: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        [data-theme="dark"] {
            --bg: #0f172a;
            --card-bg: #1e293b;
            --text: #f8fafc;
            --secondary: #020617;
            --glass: rgba(15, 23, 42, 0.9);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', sans-serif; }
        body { background-color: var(--bg); color: var(--text); transition: background var(--transition), color var(--transition); overflow-x: hidden; }

        /* --- Progress Bar --- */
        .progress-container {
            position: fixed; top: 0; left: 0; width: 100%; height: 5px;
            background: transparent; z-index: 1001;
        }
        .progress-bar {
            height: 100%; background: var(--primary); width: 0%;
            box-shadow: 0 0 10px var(--accent);
        }

        /* --- Top Bar --- */
        .top-bar {
            position: fixed; top: 5px; width: 100%; padding: 12px 30px;
            display: flex; justify-content: space-between; align-items: center;
            z-index: 100; background: var(--glass); backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(128,128,128,0.2);
        }
        .clock-display { font-weight: 700; color: var(--primary); font-family: monospace; }

        /* --- Welcome Modal --- */
        #welcome-modal {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.8); display: none; z-index: 2000;
            justify-content: center; align-items: center;
        }
        .welcome-content {
            background: var(--card-bg); padding: 40px; border-radius: 20px;
            text-align: center; max-width: 450px; box-shadow: 0 20px 50px rgba(0,0,0,0.3);
        }

        /* --- Hero Section --- */
        .hero {
            background: linear-gradient(rgba(15, 23, 42, 0.8), rgba(15, 23, 42, 0.8)), 
                        url('https://debeatzgh.wordpress.com/wp-content/uploads/2026/01/gemini_generated_image_e3b3h0e3b3h0e3b38843226607488610379.png');
            background-size: cover; background-position: center;
            height: 55vh; display: flex; align-items: center; justify-content: center;
            text-align: center; color: white; padding-top: 60px;
        }

        /* --- Social Media Bar --- */
        .social-icons { margin-top: 20px; display: flex; justify-content: center; gap: 20px; }
        .social-icons a { color: white; font-size: 1.5rem; transition: var(--transition); opacity: 0.8; }
        .social-icons a:hover { color: var(--accent); opacity: 1; transform: scale(1.2); }

        /* --- Main Content --- */
        .container { max-width: 1200px; margin: -50px auto 40px; padding: 0 20px; }
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; }
        .card { 
            background: var(--card-bg); padding: 30px; border-radius: 16px; 
            box-shadow: 0 10px 30px rgba(0,0,0,0.05); text-align: center;
            border: 1px solid rgba(128,128,128,0.1); transition: var(--transition);
        }
        .card:hover { transform: translateY(-8px); border-color: var(--primary); }
        .btn-link { 
            display: inline-block; margin-top: 20px; padding: 12px 25px; 
            background: var(--primary); color: white; border-radius: 8px; 
            text-decoration: none; font-weight: 600; transition: var(--transition);
        }

        /* --- Auto Slider --- */
        .slider-wrap { background: var(--secondary); padding: 40px 0; overflow: hidden; color: white; }
        .slider-track { display: flex; width: calc(250px * 14); animation: scroll 35s linear infinite; }
        .mini-card { 
            width: 220px; flex-shrink: 0; margin: 0 15px; padding: 20px; 
            background: rgba(255,255,255,0.05); border-radius: 10px; text-align: center; 
            cursor: pointer; text-decoration: none; color: white;
        }

        @keyframes scroll { 0% { transform: translateX(0); } 100% { transform: translateX(calc(-250px * 7)); } }
        
        footer { padding: 40px; text-align: center; background: var(--secondary); color: white; border-top: 1px solid rgba(255,255,255,0.1); }
        .footer-socials a { color: white; margin: 0 15px; font-size: 1.3rem; transition: var(--transition); }
        .footer-socials a:hover { color: var(--primary); }
    </style>
</head>
<body data-theme="light">

    <div class="progress-container">
        <div class="progress-bar" id="myBar"></div>
    </div>

    <div id="welcome-modal">
        <div class="welcome-content">
            <i class="fas fa-bullseye" style="font-size: 3rem; color: var(--primary); margin-bottom: 20px;"></i>
            <h2 id="greeting-text">Welcome!</h2>
            <p>DeBeatzGH offers top-tier digital formatting, SEO, and web development services.</p>
            <button class="btn-link" onclick="closeWelcome()">Explore Hub</button>
        </div>
    </div>

    <div class="top-bar">
        <div class="clock-display" id="liveClock">00:00:00</div>
        <div style="display: flex; gap: 20px; align-items: center;">
            <i class="fas fa-moon" id="themeIcon" style="cursor:pointer;" onclick="toggleTheme()"></i>
        </div>
    </div>

    <section class="hero">
        <div style="padding: 20px;">
            <h1 style="font-size: 3.5rem; margin-bottom: 5px;">DeBeatzGH Digital</h1>
            <p style="font-size: 1.1rem; opacity: 0.8; letter-spacing: 1px;">INNOVATION • SEO • CONTENT</p>
            <div class="social-icons">
                <a href="https://facebook.com/Debeatzgh" target="_blank"><i class="fab fa-facebook-f"></i></a>
                <a href="https://instagram.com/debeatzgh" target="_blank"><i class="fab fa-instagram"></i></a>
                <a href="https://wa.me/233549757544" target="_blank"><i class="fab fa-whatsapp"></i></a>
                <a href="https://youtube.com/debeatzgh" target="_blank"><i class="fab fa-youtube"></i></a>
            </div>
        </div>
    </section>

    <div class="container">
        <div class="grid">
            <div class="card">
                <i class="fas fa-sign-in-alt"></i>
                <h3>User Login</h3>
                <p>Access your private client area.</p>
                <a href="https://docs.google.com/forms/d/e/1FAIpQLSdXCPUz1JBq0W8MHN9VOE0p6cnp5Wtr74Ox2gqLLyzKi0UwKA/viewform?usp=header" target="_blank" class="btn-link">Sign In</a>
            </div>
            <div class="card">
                <i class="fas fa-chart-line"></i>
                <h3>SEO Strategy</h3>
                <p>Optimize your platform for 2026.</p>
                <a href="https://docs.google.com/forms/d/e/1FAIpQLSfS_zQJx3CksS-zfLU6sNgXlqI3tq7nmpKeW7_8iWUYpCJpDQ/viewform?usp=header" target="_blank" class="btn-link">Order SEO</a>
            </div>
            <div class="card">
                <i class="fas fa-code"></i>
                <h3>Web Project</h3>
                <p>High-performance web applications.</p>
                <a href="https://docs.google.com/forms/d/e/1FAIpQLSdipVP7tU1hjTjECfWUdnhzWN-PROdQp19ng25EUDJk5-8JzA/viewform?usp=header" target="_blank" class="btn-link">Start Dev</a>
            </div>
        </div>
    </div>

    <div class="slider-wrap">
        <div class="slider-track">
            <a href="https://docs.google.com/forms/d/e/1FAIpQLSfBDlR6TcU9sWjbeVOp6dtb4GMKdL6SP_i0KB08IrtbLT9wwA/viewform?usp=header" target="_blank" class="mini-card"><i class="fas fa-headset"></i><br>Contact</a>
            <a href="https://docs.google.com/forms/d/e/1FAIpQLSdx2yQU28hg4L4Rm8rSdvjR4FZPpbys7XKEZDFul5yubv3Olg/viewform?usp=header" target="_blank" class="mini-card"><i class="fas fa-lightbulb"></i><br>Suggest</a>
            <a href="https://docs.google.com/forms/d/e/1FAIpQLSd5sIJkuaBveQLFp4-W2WLvU33oDbAZMwy61MLwpMZuXrEk7Q/viewform?usp=header" target="_blank" class="mini-card"><i class="fas fa-tasks"></i><br>Format</a>
            <a href="https://docs.google.com/forms/d/e/1FAIpQLSd2fIJuPsH_fybU1esTlCaeci2s-ERDLt2L7lAp3kW4QL6D7w/viewform?usp=header" target="_blank" class="mini-card"><i class="fas fa-pen"></i><br>Blog</a>
            <a href="https://debeatzgh1.github.io/1/" class="mini-card"><i class="fas fa-globe"></i><br>Main Website</a>
            <a href="https://docs.google.com/forms/d/e/1FAIpQLSfBDlR6TcU9sWjbeVOp6dtb4GMKdL6SP_i0KB08IrtbLT9wwA/viewform?usp=header" target="_blank" class="mini-card"><i class="fas fa-headset"></i><br>Contact</a>
            <a href="https://docs.google.com/forms/d/e/1FAIpQLSdx2yQU28hg4L4Rm8rSdvjR4FZPpbys7XKEZDFul5yubv3Olg/viewform?usp=header" target="_blank" class="mini-card"><i class="fas fa-lightbulb"></i><br>Suggest</a>
        </div>
    </div>

    <footer>
        <div class="footer-socials">
            <a href="https://facebook.com/Debeatzgh" target="_blank"><i class="fab fa-facebook"></i></a>
            <a href="https://instagram.com/debeatzgh" target="_blank"><i class="fab fa-instagram"></i></a>
            <a href="https://wa.me/233549757544" target="_blank"><i class="fab fa-whatsapp"></i></a>
            <a href="https://youtube.com/debeatzgh" target="_blank"><i class="fab fa-youtube"></i></a>
        </div>
        <p style="margin-top: 20px; opacity: 0.7;">&copy; 2026 DeBeatzGH Digital. All Rights Reserved.</p>
    </footer>

    <script>
        // Welcome Logic
        window.onload = function() {
            if (!localStorage.getItem('greeted')) {
                document.getElementById('welcome-modal').style.display = 'flex';
                const hr = new Date().getHours();
                let g = "Welcome!";
                if (hr < 12) g = "Good Morning!";
                else if (hr < 18) g = "Good Afternoon!";
                else g = "Good Evening!";
                document.getElementById('greeting-text').innerText = g;
            }
        };

        function closeWelcome() {
            document.getElementById('welcome-modal').style.display = 'none';
            localStorage.setItem('greeted', 'true');
        }

        // Live Clock
        setInterval(() => {
            document.getElementById('liveClock').innerText = new Date().toLocaleTimeString();
        }, 1000);

        // Progress Bar
        window.onscroll = function() {
            let winScroll = document.body.scrollTop || document.documentElement.scrollTop;
            let height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            let scrolled = (winScroll / height) * 100;
            document.getElementById("myBar").style.width = scrolled + "%";
        };

        // Dark Mode
        function toggleTheme() {
            const b = document.body;
            const icon = document.getElementById('themeIcon');
            if (b.getAttribute('data-theme') === 'light') {
                b.setAttribute('data-theme', 'dark');
                icon.className = 'fas fa-sun';
            } else {
                b.setAttribute('data-theme', 'light');
                icon.className = 'fas fa-moon';
            }
        }
    </script>
</body>
</html>


<!doctype html>




