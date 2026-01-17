<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>Cinema</title>
<meta name="viewport" content="width=device-width, initial-scale=1">

<link href="https://fonts.googleapis.com/css2?family=Anton&display=swap" rel="stylesheet">
<script defer src="https://use.fontawesome.com/releases/v5.1.0/js/all.js"></script>

<style>
:root{
  --primary:#141414;
  --light:#f3f3f3;
  --dark:#686868;
  --red:#e50914;
}

*{margin:0;padding:0;box-sizing:border-box}

body{
  background:var(--primary);
  color:var(--light);
  font-family:Arial,Helvetica,sans-serif;
}

/* HEADER */
header{
  position:fixed;
  top:0;
  width:100%;
  background:var(--primary);
  padding:10px 20px;
  display:flex;
  justify-content:space-between;
  align-items:center;
  z-index:100;
}

.cinemaLogo h1{
  color:var(--red);
  font-family:'Anton',sans-serif;
  font-size:46px;
}

/* SECTIONS */
.section-title{
  margin:100px 20px 10px;
}

.box{
  display:flex;
  gap:10px;
  overflow-x:auto;
  padding:10px 20px;
}
.box::-webkit-scrollbar{display:none}

.box img{
  width:200px;
  border-radius:6px;
  cursor:pointer;
  transition:.3s;
}
.box img:hover{transform:scale(1.1)}

/* FOOTER */
footer{
  text-align:center;
  padding:20px;
  color:var(--dark);
}

/* POPUP EPISODES */
#episodes-popup{
  display:none;
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.95);
  z-index:998;
  justify-content:center;
  align-items:center;
  flex-direction:column;
}

.episode-btn{
  padding:12px 20px;
  margin:10px;
  background:var(--red);
  color:#fff;
  border:none;
  font-size:18px;
  cursor:pointer;
  border-radius:6px;
}

/* PLAYER TEMPLATE */
#player-template{
  display:none;
  position:fixed;
  inset:0;
  background:rgba(0,0,0,0.9);
  z-index:999;
  justify-content:center;
  align-items:center;
  flex-direction:column;
}

#video-box{
  position:relative;
  width:80%;
  max-width:900px;
  aspect-ratio:16/9;
  background:#000;
  border-radius:10px;
  overflow:hidden;
  display:flex;
  justify-content:center;
  align-items:center;
}

#video-box iframe{
  width:100%;
  height:100%;
  object-fit:contain;
  border:none;
  transition:all 0.3s ease;
}

#template-close{
  margin-top:15px;
  padding:10px 20px;
  background:var(--red);
  color:#fff;
  border:none;
  font-size:18px;
  cursor:pointer;
}
</style>
</head>

<body>

<header>
  <div class="cinemaLogo"><h1>Cinema</h1></div>
  <div>
    <i class="fab fa-instagram fa-2x logo"></i>
    <i class="fab fa-twitter fa-2x logo"></i>
    <a href="https://www.youtube.com/@user-ri4vx7fq4o" target="_blank">
      <i class="fab fa-youtube fa-2x logo"></i>
    </a>
  </div>
</header>

<!-- TV SHOWS -->
<h1 class="section-title">TV Shows</h1>
<div class="box">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/tv2.PNG?raw=true">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/tv3.PNG?raw=true">

  <!-- الطبيب المعجزة -->
  <img id="doctor"
       src="https://www.digital-discovery.tn/wp-content/uploads/2023/04/56c2b4e34-1-850x560.jpg"
       alt="مسلسل الطبيب المعجزة">
</div>

<!-- MOVIES -->
<h1 class="section-title">Movies</h1>
<div class="box">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/m1.PNG?raw=true"
       data-video="https://www.w3schools.com/html/mov_bbb.mp4">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/m2.PNG?raw=true"
       data-video="https://www.w3schools.com/html/mov_bbb.mp4">
</div>

<!-- ORIGINALS -->
<h1 class="section-title">Cinema Originals</h1>
<div class="box">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/o1.PNG?raw=true"
       data-video="https://www.w3schools.com/html/mov_bbb.mp4">
</div>

<!-- EPISODES POPUP -->
<div id="episodes-popup">
  <h2>مسلسل الطبيب المعجزة</h2>
  <button class="episode-btn" id="ep13">▶ الحلقة 13</button>
  <button class="episode-btn" id="close-episodes">إغلاق</button>
</div>

<!-- PLAYER TEMPLATE -->
<div id="player-template">
  <div id="video-box">
    <iframe id="iframe-template" src="" allow="autoplay; fullscreen; picture-in-picture; clipboard-write; encrypted-media; web-share" allowfullscreen title="الطبيب_المعجزة_مدبلج_الحلقة_13"></iframe>
  </div>
  <button id="template-close">إغلاق</button>
</div>

<footer>
  <p>© 2026 Cinema</p>
</footer>

<script>
// الأفلام العادية
document.querySelectorAll('[data-video]').forEach(img=>{
  img.onclick=()=>{
    const playerBox = document.createElement("div");
    playerBox.style.position="fixed";
    playerBox.style.inset="0";
    playerBox.style.background="rgba(0,0,0,0.95)";
    playerBox.style.display="flex";
    playerBox.style.justifyContent="center";
    playerBox.style.alignItems="center";
    playerBox.style.zIndex="999";
    const video = document.createElement("video");
    video.src = img.dataset.video;
    video.controls = true;
    video.autoplay = true;
    video.style.width="90%";
    video.style.height="80%";
    playerBox.appendChild(video);
    document.body.appendChild(playerBox);
    video.onended = ()=>{ playerBox.remove(); }
    playerBox.onclick = ()=>{ playerBox.remove(); }
  }
});

// الطبيب المعجزة
const doctor = document.getElementById("doctor");
const episodes = document.getElementById("episodes-popup");
const ep13 = document.getElementById("ep13");
const closeEpisodes = document.getElementById("close-episodes");

const playerTemplate = document.getElementById("player-template");
const iframeTemplate = document.getElementById("iframe-template");
const closeTemplate = document.getElementById("template-close");

doctor.onclick = ()=>{ episodes.style.display = "flex"; }

ep13.onclick = ()=>{
  episodes.style.display = "none";
  iframeTemplate.src = "https://player.vimeo.com/video/1155509564?badge=0&autopause=0&player_id=0&app_id=58479";
  playerTemplate.style.display = "flex";
  iframeTemplate.style.width = "100%";
  iframeTemplate.style.height = "100%";
  iframeTemplate.style.objectFit = "contain";
};

// إغلاق القالب
closeTemplate.onclick = ()=>{
  iframeTemplate.src="";
  playerTemplate.style.display = "none";
  iframeTemplate.style.width = "100%";
  iframeTemplate.style.height = "100%";
  iframeTemplate.style.objectFit = "contain";
};

// إغلاق قائمة الحلقات
closeEpisodes.onclick = ()=>{ episodes.style.display = "none"; }

</script>

</body>
</html
