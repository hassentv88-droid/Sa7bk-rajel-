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

/* PLAYER */
#player-container{
  display:none;
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.95);
  z-index:999;
  justify-content:center;
  align-items:center;
  flex-direction:column;
}

#player-container video,
#player-container iframe{
  width:90%;
  height:80%;
  border:none;
}

#close-player{
  margin-top:15px;
  padding:10px 20px;
  background:var(--red);
  color:#fff;
  border:none;
  font-size:18px;
  cursor:pointer;
}

/* EPISODES POPUP */
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

/* FOOTER */
footer{
  text-align:center;
  padding:20px;
  color:var(--dark);
}
</style>
</head>

<body>

<header>
  <div class="cinemaLogo"><h1>Cinema</h1></div>
</header>

<!-- TV SHOWS -->
<h1 class="section-title">TV Shows</h1>
<div class="box">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/tv2.PNG?raw=true">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/tv3.PNG?raw=true">

  <!-- الطبيب المعجزة (فقط هذا) -->
  <img id="doctor"
    src="https://www.digital-discovery.tn/wp-content/uploads/2023/04/56c2b4e34-1-850x560.jpg">
</div>

<!-- MOVIES (لم نلمسهم) -->
<h1 class="section-title">Movies</h1>
<div class="box">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/m1.PNG?raw=true"
       data-video="https://www.w3schools.com/html/mov_bbb.mp4">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/m2.PNG?raw=true"
       data-video="https://www.w3schools.com/html/mov_bbb.mp4">
</div>

<!-- PLAYER -->
<div id="player-container">
  <iframe id="iframePlayer" allowfullscreen></iframe>
  <button id="close-player">إغلاق</button>
</div>

<!-- EPISODES -->
<div id="episodes-popup">
  <h2>مسلسل الطبيب المعجزة</h2>
  <button class="episode-btn" id="ep1">▶ الحلقة 1</button>
  <button class="episode-btn" id="close-episodes">إغلاق</button>
</div>

<footer>
  <p>© 2026 Cinema</p>
</footer>

<script>
/* الأفلام العادية */
document.querySelectorAll('[data-video]').forEach(img=>{
  img.onclick=()=>{
    iframePlayer.src = img.dataset.video;
    playerBox.style.display="flex";
  }
});

/* الطبيب المعجزة */
const doctor = document.getElementById("doctor");
const episodes = document.getElementById("episodes-popup");
const ep1 = document.getElementById("ep1");
const closeEpisodes = document.getElementById("close-episodes");

const playerBox = document.getElementById("player-container");
const iframePlayer = document.getElementById("iframePlayer");
const closePlayer = document.getElementById("close-player");

doctor.onclick = ()=>{
  episodes.style.display="flex";
};

ep1.onclick = ()=>{
  episodes.style.display="none";
  iframePlayer.src = "https://streamable.com/e/cqfwth";
  playerBox.style.display="flex";
};

closeEpisodes.onclick = ()=>{
  episodes.style.display="none";
};

closePlayer.onclick = ()=>{
  iframePlayer.src="";
  playerBox.style.display="none";
};
</script>

</body>
</html
