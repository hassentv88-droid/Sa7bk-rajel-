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

    <!-- محتوى الصفحة الثانية مباشرة بدون html, head, body -->
    <header>
      <h1>Cinema</h1>
    </header>

    <h1 class="section-title">TV Shows</h1>
    <div class="box">
      <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/tv2.PNG?raw=true">
      <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/tv3.PNG?raw=true">
      <img id="doctor" src="https://www.digital-discovery.tn/wp-content/uploads/2023/04/56c2b4e34-1-850x560.jpg">
    </div>

    <h1 class="section-title">Movies</h1>
    <div class="box">
      <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/m1.PNG?raw=true">
    </div>

    <div id="doctor-popup">
      <iframe srcdoc='
        <!-- هنا محتوى iframe كما هو في الكود الأصلي بدون تغيير -->
      '></iframe>
    </div>

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
      }, 1000); 
    }, 4000);

    // popup
    const doctor = document.getElementById("doctor");
    const popup = document.getElementById("doctor-popup");

    doctor.onclick = ()=> popup.style.display="block";

    // الغلق فقط إذا ضغطت خارج iframe
    popup.addEventListener('click', function(e){
      if(e.target === popup) popup.style.display="none";
    });
  </script>

</body>
</html>
