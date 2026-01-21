<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>Cinema</title>
<meta name="viewport" content="width=device-width, initial-scale=1">

<style>
  body {
    margin: 0;
    padding: 0;
    background: black;
    font-family: Arial, Helvetica, sans-serif;
    position: relative;
  }

  /* شاشة البداية */
  #splash {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: black;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    z-index: 9999;
    opacity: 1;
    transition: opacity 1s ease; /* تأثير Fade Out */
  }

  .logo {
    color: red;
    font-size: 80px;
    font-weight: bold;
    letter-spacing: 2px;
  }

  .version {
    color: white;
    font-size: 14px;
    opacity: 0.8;
    margin-top: 20px;
  }

  /* محتوى الصفحة الثانية مخفي في البداية */
  #mainContent {
    display: none;
    padding: 20px;
    color: white;
    background: #111;
    min-height: 100vh;
  }
</style>
</head>

<body>
  <!-- شاشة البداية -->
  <div id="splash">
    <div class="logo">Cinema</div>
    <div class="version">V.2.58.1</div>
  </div>

  <!-- محتوى الصفحة الثانية -->
  <div id="mainContent">
    <h1>  !</h1>
    <p><!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>Cinema App</title>
<meta name="viewport" content="width=device-width, initial-scale=1">

<link href="https://fonts.googleapis.com/css2?family=Anton&display=swap" rel="stylesheet">

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
  align-items:center;
  z-index:100;
}
header h1{
  color:var(--red);
  font-family:'Anton',sans-serif;
  font-size:42px;
}

/* SECTIONS */
.section-title{
  margin:100px 20px 10px;
}

.box{
  display:flex;
  gap:12px;
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

/* POPUP */
#doctor-popup{
  display:none;
  position:fixed;
  inset:0;
  background:#000;
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
  <h1>Cinema</h1>
</header>

<!-- TV SHOWS -->
<h1 class="section-title">TV Shows</h1>
<div class="box">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/tv2.PNG?raw=true">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/tv3.PNG?raw=true">

  <!-- الطبيب المعجزة -->
  <img id="doctor"
       src="https://www.digital-discovery.tn/wp-content/uploads/2023/04/56c2b4e34-1-850x560.jpg">
</div>

<!-- MOVIES -->
<h1 class="section-title">Movies</h1>
<div class="box">
  <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/m1.PNG?raw=true">
</div>

<!-- POPUP التطبيق الثاني -->
<div id="doctor-popup">
<iframe srcdoc='
<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>الطبيب المعجزة</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
*{margin:0;padding:0;box-sizing:border-box}
body{background:#0c0c0c;color:#fff;font-family:Arial}

/* HEADER */
.header{
  position:fixed;
  top:0;
  width:100%;
  display:flex;
  justify-content:space-between;
  padding:15px;
  z-index:10;
}
.header span{font-size:22px;cursor:pointer}

/* COVER */
.cover{
  height:60vh;
  background:url("https://www.digital-discovery.tn/wp-content/uploads/2023/04/56c2b4e34-1-850x560.jpg") center/cover;
  position:relative;
}
.cover::after{
  content:"";
  position:absolute;
  inset:0;
  background:linear-gradient(to top,#0c0c0c,transparent);
}

/* CONTENT */
.content{padding:15px}
.desc{color:#bbb;margin:10px 0 15px}

.episodes-header{
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin-bottom:10px;
}
.season{
  background:#222;
  padding:6px 12px;
  border-radius:20px;
  font-size:14px;
}

/* EPISODE */
.episode{
  position:relative;
  margin-bottom:15px;
}
.episode img{
  width:100%;
  border-radius:10px;
}
.play{
  position:absolute;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
  background:#e50914;
  width:55px;
  height:55px;
  border-radius:50%;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:24px;
}
.ep-title{
  margin-top:6px;
  font-size:15px;
}

/* PLAYER */
#player{
  position:fixed;
  inset:0;
  background:#000;
  display:none;
  z-index:999;
}
#player iframe{
  width:100%;
  height:100%;
  border:none;
}
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
  <p class="desc">
    قصة طبيب عبقري يعاني من التوحّد، يثبت قدرته رغم كل الصعوبات.
  </p>

  <div class="episodes-header">
    <strong>الحلقات</strong>
    <div class="season">Saison 01 ⌄</div>
  </div>

  <!-- EP 13 -->
  <div class="episode" onclick="play(13)">
    <img src="https://www.digital-discovery.tn/wp-content/uploads/2023/04/56c2b4e34-1-850x560.jpg">
    <div class="play">▶</div>
    <div class="ep-title">Episode 13</div>
  </div>

  <!-- EP 14 -->
  <div class="episode" onclick="play(14)">
    <img src="https://www.digital-discovery.tn/wp-content/uploads/2023/04/56c2b4e34-1-850x560.jpg">
    <div class="play">▶</div>
    <div class="ep-title">Episode 14</div>
  </div>
</div>

<div id="player">
  <iframe id="frame" allow="autoplay; fullscreen" allowfullscreen></iframe>
</div>

<script>
function play(ep){
  const vids={
    13:"https://player.vimeo.com/video/1155509564?autoplay=1",
    14:"https://player.vimeo.com/video/1155548749?autoplay=1"
  };
  frame.src=vids[ep];
  player.style.display="block";
  player.requestFullscreen();
}
</script>

</body>
</html>
'></iframe>
</div>

<script>
const doctor = document.getElementById("doctor");
const popup = document.getElementById("doctor-popup");

doctor.onclick = ()=> popup.style.display="block";
popup.onclick = ()=> popup.style.display="none";
</script>

</body>
</html></p>
  </div>

  <script>
    // بعد 4 ثواني، نبدأ تأثير Fade Out
    setTimeout(function() {
      const splash = document.getElementById('splash');
      splash.style.opacity = 0;

      // بعد انتهاء الفيد (1 ثانية)، نخفي الشاشة ونظهر الصفحة الثانية
      setTimeout(function() {
        splash.style.display = 'none';
        document.getElementById('mainContent').style.display = 'block';
      }, 1000); // نفس مدة transition
    }, 4000); // 4 ثواني انتظار قبل البداية
  </script>
</body>
</html>
