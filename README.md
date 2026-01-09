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
