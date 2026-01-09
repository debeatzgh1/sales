
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Debeatzgh – Digital Hub Launcher</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Icons -->
<link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">

<style>
:root{
  --primary:#0f172a;
  --accent:#38bdf8;
  --glass:rgba(255,255,255,0.08);
}

*{box-sizing:border-box;margin:0;padding:0}

body{
  font-family:system-ui,-apple-system,BlinkMacSystemFont;
  background:linear-gradient(135deg,#020617,#020617,#020617);
  color:#e5e7eb;
}

/* HEADER */
header{
  display:flex;
  justify-content:space-between;
  align-items:center;
  padding:14px 18px;
  background:rgba(15,23,42,.9);
  position:sticky;
  top:0;
  z-index:1000;
}

header h1{
  font-size:1.1rem;
  color:#38bdf8;
}

.header-actions i{
  margin-left:14px;
  cursor:pointer;
  font-size:1.1rem;
}

/* MAIN LAYOUT */
main{
  display:grid;
  grid-template-columns:1fr 380px;
  gap:16px;
  padding:16px;
}

@media(max-width:900px){
  main{grid-template-columns:1fr}
}

/* SECTION BOX */
.section{
  background:var(--glass);
  border-radius:16px;
  padding:14px;
  backdrop-filter:blur(12px);
}

/* PREVIEW GRID */
.preview-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(220px,1fr));
  gap:14px;
}

.card{
  background:rgba(255,255,255,0.06);
  border-radius:14px;
  padding:12px;
  cursor:pointer;
  transition:.25s;
}

.card:hover{
  transform:translateY(-4px);
  background:rgba(56,189,248,0.15);
}

.card h3{
  font-size:.95rem;
  margin-bottom:6px;
}

.card p{
  font-size:.8rem;
  opacity:.8;
}

/* IFRAME PREVIEW */
#previewFrame{
  width:100%;
  height:420px;
  border:none;
  border-radius:14px;
  margin-top:14px;
  background:#000;
}

/* CAROUSEL */
.carousel{
  position:relative;
  overflow:hidden;
  height:340px;
}

.slide{
  display:none;
  animation:fade .6s ease;
}

.slide.active{display:block}

@keyframes fade{
  from{opacity:0}
  to{opacity:1}
}

.slide h3{
  font-size:1rem;
  margin-bottom:6px;
  color:#38bdf8;
}

.slide p{
  font-size:.85rem;
  margin-bottom:10px;
}

.slide a{
  display:inline-block;
  padding:8px 12px;
  border-radius:10px;
  background:#38bdf8;
  color:#020617;
  font-size:.8rem;
  text-decoration:none;
}

/* CAROUSEL NAV */
.carousel-nav{
  display:flex;
  justify-content:space-between;
  margin-top:10px;
}

.carousel-nav i{
  cursor:pointer;
  padding:8px;
  border-radius:50%;
  background:rgba(255,255,255,0.1);
}
</style>
</head>

<body>

<header>
  <h1>Debeatzgh Digital Network</h1>
  <div class="header-actions">
    <i class="fas fa-expand" onclick="toggleFull()"></i>
    <i class="fas fa-bars" onclick="openMenu()"></i>
  </div>
</header>

<main>

<!-- SECTION 1: PREVIEW -->
<section class="section">
  <h2>Explore Our Platforms</h2>
  <p style="font-size:.85rem;opacity:.8;margin-bottom:12px">
    Click any card to preview instantly
  </p>

  <div class="preview-grid" id="cards"></div>

  <iframe id="previewFrame" src="https://debeatzgh1.blogspot.com/"></iframe>
</section>

<!-- SECTION 2: CAROUSEL -->
<section class="section">
  <h2>Featured Highlights</h2>

  <div class="carousel" id="carousel"></div>

  <div class="carousel-nav">
    <i class="fas fa-chevron-left" onclick="prevSlide()"></i>
    <i class="fas fa-chevron-right" onclick="nextSlide()"></i>
  </div>
</section>

</main>

<script>
const sites=[
  {
    title:"Debeatzgh Blog",
    desc:"AI tools, digital income & tech insights",
    url:"https://debeatzgh1.blogspot.com/"
  },
  {
    title:"AppDate GH",
    desc:"Apps, updates and mobile tools",
    url:"https://appdategh.blogspot.com/"
  },
  {
    title:"Beatzde4",
    desc:"Online income strategies & AI",
    url:"https://beatzde4.blogspot.com/"
  },
  {
    title:"Debeatzgh 2",
    desc:"Extended blogging & monetization",
    url:"https://debeatzgh2.blogspot.com/"
  },
  {
    title:"My Brands Online",
    desc:"Digital brands & affiliate products",
    url:"https://mybrandsonline.blogspot.com/"
  },
  {
    title:"Debeatzgh WordPress",
    desc:"Premium articles & insights",
    url:"https://debeatzgh.wordpress.com/"
  },
  {
    title:"Debeatzgh Bio",
    desc:"Quick access to all platforms",
    url:"https://msha.ke/debeatzgh"
  },
  {
    title:"Digimart GH",
    desc:"Side hustles & digital services",
    url:"https://digimartgh.blogspot.com/"
  }
];

const cards=document.getElementById("cards");
const frame=document.getElementById("previewFrame");
const carousel=document.getElementById("carousel");

sites.forEach((s,i)=>{
  const c=document.createElement("div");
  c.className="card";
  c.innerHTML=`<h3>${s.title}</h3><p>${s.desc}</p>`;
  c.onclick=()=>frame.src=s.url;
  cards.appendChild(c);

  const slide=document.createElement("div");
  slide.className="slide"+(i===0?" active":"");
  slide.innerHTML=`
    <h3>${s.title}</h3>
    <p>${s.desc}</p>
    <a href="${s.url}" target="_blank">Visit Platform</a>
  `;
  carousel.appendChild(slide);
});

let index=0;
function showSlide(i){
  const slides=document.querySelectorAll(".slide");
  slides.forEach(s=>s.classList.remove("active"));
  slides[i].classList.add("active");
}

function nextSlide(){
  index=(index+1)%sites.length;
  showSlide(index);
}

function prevSlide(){
  index=(index-1+sites.length)%sites.length;
  showSlide(index);
}

let auto=setInterval(nextSlide,4000);
carousel.onmouseenter=()=>clearInterval(auto);
carousel.onmouseleave=()=>auto=setInterval(nextSlide,4000);

function toggleFull(){
  document.fullscreenElement?
  document.exitFullscreen():
  document.documentElement.requestFullscreen();
}

function openMenu(){
  window.open("https://debeatzgh1.github.io/1/","_blank");
}
</script>

</body>
</html>
