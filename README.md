<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>Cinema</title>
<meta name="viewport" content="width=device-width, initial-scale=1">

<link href="https://fonts.googleapis.com/css2?family=Anton&display=swap" rel="stylesheet">
<script defer src="https://use.fontawesome.com/releases/v5.1.0/js/all.js"></script>

<style>
:root {
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

/* ICONS */
.fab.logo{
  color:var(--light);
  margin:10px;
  transition:0.3s;
}
.fab.logo:hover{color:var(--red)}

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
  transition:0.3s;
}
.box img:hover{transform:scale(1.1)}

/* VIDEO PLAYER */
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
#player-container video{
  max-width:90%;
  max-height:80%;
}
#player-container button{
  margin-top:15px;
  padding:10px 20px;
  background:var(--red);
  color:#fff;
  border:none;
  font-size:18px;
  cursor:pointer;
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

<!-- HEADER -->
<header>
  <div class="cinemaLogo">
    <h1>Cinema</h1>
  </div>
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

  <!-- 💥 هنا مسلسل الطبيب المعجزة -->
  <!-- الصورة تعمل كزر، عند الضغط عليها يشغل الفيديو -->
  <img id="special-movie"
       src="https://www.digital-discovery.tn/wp-content/uploads/2023/04/56c2b4e34-1-850x560.jpg"
       alt="مسلسل الطبيب المعجزة">
  <!-- ضع الفيديو الخاص بك هنا على الجهاز، المسار الذي أعطيته لك -->
  <!-- مثال: /storage/emulated/0/Android/data/com.fazil.htmleditor/files/Documents/hshs/media/videos/4_5824321466962806937.mp4 -->
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

<!-- VIDEO PLAYER الافتراضي -->
<div id="player-container">
  <video id="player" controls autoplay></video>
  <button id="close-player">إغلاق</button>
</div>

<!-- FOOTER -->
<footer>
  <p>© 2026 Cinema — جميع الحقوق محفوظة</p>
</footer>

<script>
const images = document.querySelectorAll('[data-video]');
const playerBox = document.getElementById('player-container');
const player = document.getElementById('player');
const closeBtn = document.getElementById('close-player');

// المشغّل الافتراضي لكل الفيديوهات العادية
images.forEach(img=>{
  img.onclick=()=>{
    player.src = img.dataset.video;
    playerBox.style.display="flex";
  }
});

closeBtn.onclick=()=>{
  player.pause()
  playerBox.style.display="none";
};

// 🌟 خاص بمسلسل الطبيب المعجزة
const specialMovie = document.getElementById('special-movie');
specialMovie.onclick = () => {
  // 💡 ضع هنا مسار الفيديو على جهازك
  window.location.href = "/storage/emulated/0/Android/data/com.fazil.htmleditor/files/Documents/httpsfonts.googleapis.comcss2familyAntondisplayswap/media/videos/TUNISIA Explained in 12 Minutes (History, Geography, & Culture).mp4";
};
</script>

</body
</html>
