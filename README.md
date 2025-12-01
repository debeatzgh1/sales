<style>
  /* 🌟 Fade Slide Animation */
  @keyframes fadeSlideUp {
    0% { opacity: 0; transform: translateY(0) translateX(20px); }
    100% { opacity: 1; transform: translateY(0) translateX(0); }
  }

  /* ❤️ Heartbeat Animation */
  @keyframes heartbeat {
    0% { transform: scale(1); }
    25% { transform: scale(1.08); }
    50% { transform: scale(1); }
    75% { transform: scale(1.08); }
    100% { transform: scale(1); }
  }

  .floating-btn-group {
    animation: fadeSlideUp 0.6s ease-out;
  }

  /* Iframe Modal Styles */
  #iframe-modal {
    display: none;
    position: fixed;
    z-index: 9999;
    left: 0;
    top: 0;
    width: 100%;
    height: 115%;
    background: rgba(0,0,0,0.6);
    backdrop-filter: blur(4px);
  }

  .modal-content {
    position: relative;
    margin: 2% auto;
    background: #fff;
    border-radius: 16px;
    width: 95%;
    height: 90%;
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
    overflow: hidden;
    animation: fadeIn 0.3s ease;
  }

  #modal-iframe {
    width: 100%;
    height: 105%;
    border: none;
  }

  .close-btn {
    position: absolute;
    top: 10px;
    right: 18px;
    font-size: 30px;
    color: #333;
    cursor: pointer;
    transition: color 0.2s;
    z-index: 10;
  }

  .close-btn:hover {
    color: #e11d48;
  }

  @keyframes fadeIn {
    from {opacity: 0; transform: translateY(-10px);}
    to {opacity: 1; transform: translateY(0);}
  }
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {

  // 🔹 Floating Button at TOP-LEFT
  const btnGroup = document.createElement("div");
  btnGroup.className = "floating-btn-group";
  Object.assign(btnGroup.style, {
    position: "fixed",
    top: "20px",          // Top-left positioning
    left: "20px",
    zIndex: "9999",
    animation: "heartbeat 2.5s infinite ease-in-out, fadeSlideUp 0.6s ease-out forwards"
  });

  // -------------------------------------------------------
  // 📌 Updates Button
  // -------------------------------------------------------
  const button = document.createElement("a");
  button.href = "#";
  button.innerText = "📌 Updates";
  Object.assign(button.style, {
    background: "#16a34a",
    color: "#fff",
    padding: "12px 24px",
    borderRadius: "30px",
    textDecoration: "none",
    fontSize: "15px",
    fontWeight: "700",
    boxShadow: "0 4px 10px rgba(0,0,0,0.25)",
    whiteSpace: "nowrap",
  });

  // 🔹 Iframe Modal
  const modal = document.createElement("div");
  modal.id = "iframe-modal";
  modal.innerHTML = `
    <div class="modal-content">
      <span class="close-btn">&times;</span>
      <iframe id="modal-iframe" src="" loading="lazy"></iframe>
    </div>
  `;

  document.body.appendChild(modal);

  // 🔹 Open Iframe on click
  button.addEventListener("click", function (e) {
    e.preventDefault();
    document.getElementById("modal-iframe").src = "https://debeatzgh1.github.io/Digital-Creator-s-Essential-Guides-Tools/";
    modal.style.display = "block";
  });

  btnGroup.appendChild(button);
  document.body.appendChild(btnGroup);

  // 🔹 Close Modal
  document.addEventListener("click", function (e) {
    if (e.target.classList.contains("close-btn") || e.target.id === "iframe-modal") {
      modal.style.display = "none";
      document.getElementById("modal-iframe").src = "";
    }
  });

  // 🔹 Auto-open external ads in a new tab
  document.getElementById("modal-iframe").addEventListener("load", function () {
    try {
      const links = this.contentDocument.querySelectorAll("a");
      links.forEach(link => {
        if (!link.href.includes("debeatzgh.wordpress.com")) {
          link.setAttribute("target", "_blank");
          link.setAttribute("rel", "noopener");
        }
      });
    } catch (err) {
      console.warn("External site - cannot rewrite links");
    }
  });

});
</script>


<!doctype html>


<!-- ============================
     Your Branding Banner
============================= -->
<p align="center">
  <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/09/asleekandmoderngoogleclassroombannerfortechaihubfeaturingfuturisticdigitalelements261807892942313727.jpg"
       alt="Tech-AI Hub Banner"
       style="max-width:100%; height:auto; border-radius: 8px;"/>
</p>

# Welcome to **Tech-AI Hub & Blogs Collection** 👋

We curate and publish content on **AI-driven side hustles, digital tools, online income strategies, and creative tech insights** — all aimed at empowering you to build, grow, and scale in the digital age.

> Explore our blogs below. Click on any card to open it in an embedded viewer (iframe), or use the floating “Blogs 🔗” button at the bottom-right to open the carousel at any time.

---

<div id="blog-carousel-container"></div>

---

## About This Hub

This GitHub Pages repo serves as a **central gateway** to all our active blogs — making it easy for readers to:  
- Browse through all blogs in one place,  
- Preview them without leaving the hub site,  
- And navigate seamlessly between them.

Perfect for **developers, side hustlers, bloggers, and digital creators** exploring AI, tech, and online income.

---

## How to Use

1. **Clone or Fork** this repo and enable GitHub Pages (or host it as a static site).
2. Ensure that the `carousel.html` (or inline script below) is included so the floating button and carousel UI load correctly.
3. Click any blog title or the floating “Blogs 🔗” button to start exploring.

---

## Blog Highlights

| Blog | What to Expect |
|------|----------------|
| **DigiMartGH – Digital Market Insights** | Practical guides on launching digital marketplaces and monetizing digital products, with case studies and step-by-step walkthroughs. |
| **DebeatzGH 2 – Tech & Hustle Edition** | Combines tech tutorials, AI-powered side hustle ideas, and freelance strategies for aspiring digital entrepreneurs. |
| **BeatzDe4 – AI & Online Income Hub** | Deep dives into AI tools, automation workflows, and passive income techniques — for students, side hustlers, and small business owners. |
| **DebeatzGH 1 – Creative Tech & Blogging** | Blogging tips, content creation strategies, SEO guides, and how to turn blogging into a revenue channel. |
| **BeatzDe4 (Archive Edition)** | Legacy content: earlier explorations in AI, blogging, and online income experiments — still valuable reference material. |

---



<!-- Carousel + Floating Button UI -->
<style>
  /* Carousel overlay */
  #blog-carousel-overlay {
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: rgba(0,0,0,0.8);
    display: none;
    align-items: center;
    justify-content: center;
    z-index: 1000;
  }
  #blog-carousel {
    background: #fff;
    width: 90%;
    max-width: 800px;
    max-height: 90%;
    overflow-y: auto;
    border-radius: 8px;
    padding: 24px;
    box-shadow: 0 4px 16px rgba(0,0,0,0.3);
  }
  .blog-card {
    border: 1px solid #ddd;
    border-radius: 6px;
    padding: 16px;
    margin-bottom: 16px;
  }
  .blog-card h3 {
    margin: 0 0 8px;
  }
  .blog-card p {
    margin: 0 0 12px;
    color: #555;
  }
  .blog-card button {
    padding: 8px 12px;
    background: #2563eb;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  .blog-card button:hover {
    background: #1e40af;
  }
  /* Floating button */
  #open-carousel-btn {
    position: fixed;
    bottom: 24px;
    right: 24px;
    background: #2563eb;
    color: #fff;
    border: none;
    border-radius: 50%;
    width: 56px;
    height: 56px;
    font-size: 24px;
    cursor: pointer;
    box-shadow: 0 2px 12px rgba(0,0,0,0.3);
    z-index: 999;
  }
</style>

<button id="open-carousel-btn" title="Open Blogs">📚</button>

<div id="blog-carousel-overlay">
  <div id="blog-carousel">
    <button id="close-carousel-btn" style="float:right; font-size:18px; background:transparent; border:none; cursor:pointer;">✖️</button>
    <h2>Our Blogs</h2>

    <!-- Blog Cards -->
    <div class="blog-card">
      <h3>DigiMartGH – Digital Market Insights</h3>
      <p>Practical guides on launching digital marketplaces and monetizing digital products — full of case studies and step-by-step walkthroughs.</p>
      <button onclick="openInIframe('https://digimartgh.blogspot.com/')">Open DigiMartGH</button>
    </div>

    <div class="blog-card">
      <h3>DebeatzGH 2 – Tech & Hustle Edition</h3>
      <p>Tech tutorials, AI-powered side hustle ideas, and freelance strategies for aspiring digital entrepreneurs.</p>
      <button onclick="openInIframe('https://debeatzgh2.blogspot.com/')">Open DebeatzGH 2</button>
    </div>

    <div class="blog-card">
      <h3>BeatzDe4 – AI & Online Income Hub</h3>
      <p>Deep dives into AI tools, automation workflows, and passive income techniques — ideal for students, side hustlers, and small business owners.</p>
      <button onclick="openInIframe('https://beatzde4.blogspot.com/')">Open BeatzDe4</button>
    </div>

    <div class="blog-card">
      <h3>DebeatzGH 1 – Creative Tech & Blogging</h3>
      <p>Blogging tips, content-creation strategies, SEO guides, and how to turn blogging into a revenue stream.</p>
      <button onclick="openInIframe('https://debeatzgh1.blogspot.com/')">Open DebeatzGH 1</button>
    </div>

    <div class="blog-card">
      <h3>BeatzDe4 (Archive Edition)</h3>
      <p>Legacy content — earlier explorations in AI, blogging, and online income experiments. A rich repository of insights and lessons learned.</p>
      <button onclick="openInIframe('https://beatzde4.blogspot.com/')">Open Archive</button>
    </div>

  </div>
</div>

<!-- Iframe overlay -->
<div id="iframe-overlay" style="display:none; position:fixed; top:0; left:0; right:0; bottom:0; background:rgba(0,0,0,0.9); z-index:1100; align-items:center; justify-content:center;">
  <div style="position: relative; width:90%; height:90%; max-width:1000px; max-height:800px; background:#fff; border-radius:8px; overflow:hidden;">
    <button id="close-iframe-btn" style="position:absolute; top:8px; right:8px; z-index:1200; background:transparent; border:none; font-size:24px; cursor:pointer;">✖️</button>
    <iframe id="blog-iframe" src="" style="width:100%; height:100%; border:none;"></iframe>
  </div>
</div>

<script>
  const openBtn = document.getElementById('open-carousel-btn')
  const overlay = document.getElementById('blog-carousel-overlay')
  const closeBtn = document.getElementById('close-carousel-btn')
  const iframeOverlay = document.getElementById('iframe-overlay')
  const iframe = document.getElementById('blog-iframe')
  const closeIframeBtn = document.getElementById('close-iframe-btn')

  openBtn.onclick = () => overlay.style.display = 'flex'
  closeBtn.onclick = () => overlay.style.display = 'none'

  function openInIframe(url) {
    iframe.src = url
    overlay.style.display = 'none'
    iframeOverlay.style.display = 'flex'
  }
  closeIframeBtn.onclick = () => {
    iframe.src = ''
    iframeOverlay.style.display = 'none'
  }
</script>
