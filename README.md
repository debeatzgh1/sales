<html lang="en">
<head>
<meta charset="UTF-8">
<title>Ultra Mini Blog Launcher</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">

<style>
.mini-launcher{
  position:fixed;
  bottom:18px;
  right:18px;
  z-index:9999;
}

.mini-btn{
  width:48px;
  height:48px;
  border-radius:50%;
  background:#38bdf8;
  color:#020617;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:1.2rem;
  cursor:pointer;
  box-shadow:0 8px 20px rgba(56,189,248,.6);
}

.mini-panel{
  position:absolute;
  bottom:60px;
  right:0;
  width:240px;
  background:rgba(15,23,42,.95);
  backdrop-filter:blur(10px);
  border-radius:14px;
  padding:10px;
  display:none;
}

.mini-panel.active{display:block}

.mini-header{
  display:flex;
  justify-content:space-between;
  align-items:center;
  font-size:.8rem;
  margin-bottom:8px;
  color:#38bdf8;
}

.mini-header i{cursor:pointer}

.mini-link{
  padding:8px 10px;
  border-radius:10px;
  font-size:.75rem;
  cursor:pointer;
  transition:.2s;
}

.mini-link:hover{
  background:rgba(56,189,248,.15);
}

.preview-modal{
  display:none;
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.75);
  z-index:99999;
}

.preview-box{
  position:absolute;
  inset:6%;
  background:#020617;
  border-radius:14px;
  overflow:hidden;
}

.preview-box iframe{
  width:100%;
  height:100%;
  border:none;
}

.close-preview{
  position:absolute;
  top:10px;
  right:14px;
  color:#fff;
  font-size:1.2rem;
  cursor:pointer;
}
</style>
</head>

<body>

<div class="mini-launcher">
  <div class="mini-btn" onclick="toggleMini()">
    <i class="fas fa-bolt"></i>
  </div>

  <div class="mini-panel" id="miniPanel">
    <div class="mini-header">
      <span>Quick Blogs</span>
      <i class="fas fa-bars" onclick="openHub()"></i>
    </div>

    <div class="mini-link" onclick="openPreview('https://debeatzgh1.blogspot.com/')">Debeatzgh Blog</div>
    <div class="mini-link" onclick="openPreview('https://appdategh.blogspot.com/')">AppDate GH</div>
    <div class="mini-link" onclick="openPreview('https://beatzde4.blogspot.com/')">Beatzde4</div>
    <div class="mini-link" onclick="openPreview('https://debeatzgh2.blogspot.com/')">Debeatzgh 2</div>
    <div class="mini-link" onclick="openPreview('https://mybrandsonline.blogspot.com/')">My Brands Online</div>
    <div class="mini-link" onclick="openPreview('https://debeatzgh.wordpress.com/')">Debeatzgh (WP)</div>
    <div class="mini-link" onclick="openPreview('https://digimartgh.blogspot.com/')">Digimart GH</div>
    <div class="mini-link" onclick="openPreview('https://msha.ke/debeatzgh')">Bio / All Links</div>
  </div>
</div>

<div class="preview-modal" id="previewModal">
  <div class="preview-box">
    <i class="fas fa-times close-preview" onclick="closePreview()"></i>
    <iframe id="previewFrame"></iframe>
  </div>
</div>

<script>
function toggleMini(){
  document.getElementById("miniPanel").classList.toggle("active");
}

function openHub(){
  window.open("https://debeatzgh1.github.io/1/","_blank");
}

function openPreview(url){
  document.getElementById("previewFrame").src=url;
  document.getElementById("previewModal").style.display="block";
  document.getElementById("miniPanel").classList.remove("active");
}

function closePreview(){
  document.getElementById("previewModal").style.display="none";
  document.getElementById("previewFrame").src="";
}
</script>

</body>
</html>
