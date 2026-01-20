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

/* POPUP */
#doctor-popup{
  display:none;
  position:fixed;
  inset:0;
  background:rgba(0,0,0,0.95);
  z-index:999;
}
#doctor-popup iframe{
  width:100%;
  height:100%;
  border:none;
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

  <!-- الطبيب المعجزة -->
  <img id="doctor" src="https://www.digital-discovery.tn/wp-content/uploads/2023/04/56c2b4e34-1-850x560.jpg">
</div>

<!-- MOVIES -->
<h1 class="section-title">Movies</h1>
<div class="box">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/m1.PNG?raw=true"
       data-video="https://www.w3schools.com/html/mov_bbb.mp4">
</div>

<!-- POPUP: iframe يحتوي الكود الثاني كما هو -->
<div id="doctor-popup">
  <iframe srcdoc='
  <!DOCTYPE html>
  <html lang="ar">
  <head>
  <meta charset="UTF-8">
  <title>Nessma Style</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
  *{margin:0;padding:0;box-sizing:border-box}
  body{background:#0c0c0c;color:#fff;font-family:Arial;}
  .header{position:fixed;top:0;width:100%;display:flex;justify-content:space-between;padding:15px;z-index:10;}
  .header span{font-size:22px}
  .cover{height:60vh;background:url("https://www.digital-discovery.tn/wp-content/uploads/2023/04/56c2b4e34-1-850x560.jpg") center/cover;position:relative;}
  .cover::after{content:"";position:absolute;inset:0;background:linear-gradient(to top,#0c0c0c,transparent);}
  .content{padding:15px;}
  h2{margin-bottom:10px}.desc{color:#bbb;margin-bottom:15px;}
  .episodes-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;}
  .season{background:#222;padding:6px 12px;border-radius:20px;font-size:14px;}
  .episode{position:relative;margin-bottom:15px;}
  .episode img{width:100%;border-radius:10px;}
  .play{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);background:#e50914;width:55px;height:55px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:24px;}
  .ep-title{margin-top:6px;font-size:15px;}
  #player{position:fixed;inset:0;background:#000;display:none;z-index:999;}
  #player iframe{width:100%;height:100%;border:none;}
  </style>
  </head>
  <body>
  <div class="header">
    <span onclick="history.back()">←</span>
    <span>🔍</span>
  </div>
  <div class="cover"></div>
  <div class="content">
    <h2>الطبيب المعجزة</h2>
    <p class="desc">قصة طبيب عبقري يعاني من التوحّد، يثبت قدرته رغم كل الصعوبات.</p>
    <div class="episodes-header">
      <strong>الحلقات</strong>
      <div class="season">Saison 01 ⌄</div>
    </div>
    <div class="episode" onclick="play(13)">
      <img src="https://i.imgur.com/2yaf2wb.jpg">
      <div class="play">▶</div>
      <div class="ep-title">Episode 13</div>
    </div>
    <div class="episode" onclick="play(14)">
      <img src="https://i.imgur.com/2yaf2wb.jpg">
      <div class="play">▶</div>
      <div class="ep-title">Episode 14</div>
    </div>
  </div>
  <div id="player">
    <iframe id="frame" allow="autoplay; fullscreen" allowfullscreen></iframe>
  </div>
  <script>
  function play(ep){
    const vids={13:"https://player.vimeo.com/video/1155509564?autoplay=1",
                14:"https://player.vimeo.com/video/1155548749?autoplay=1"};
    frame.src=vids[ep];
    player.style.display="block";
    player.requestFullscreen();
  }
  </script>
  </body>
  </html>
  '></iframe>
</div>

<footer>
  <p>© 2026 Cinema</p>
</footer>

<script>
// عرض popup iframe عند الضغط على طبيب المعجزة
const doctor = document.getElementById("doctor");
const popup = document.getElementById("doctor-popup");

doctor.onclick = ()=>{
  popup.style.display = "block";
};

// إخفاء popup عند النقر على الخلفية
popup.onclick = ()=>{
  popup.style.display = "none";
};

// تشغيل الفيديوهات الأخرى
document.querySelectorAll('.box img[data-video]').forEach(img=>{
  img.onclick = ()=>{
    const videoSrc = img.getAttribute('data-video');
    window.open(videoSrc, "_blank");
  };
});
</script>

</body>
</html
