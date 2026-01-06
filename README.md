<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>منصة الأفلام</title>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #0f0f0f;
    color: white;
}

header {
    background: #111;
    padding: 15px 30px;
    font-size: 24px;
    font-weight: bold;
}

.section {
    padding: 20px;
}

.movies {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
}

.movie {
    width: 200px;
    height: 120px;
    background: #222;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: 0.3s;
    text-align: center;
    padding: 5px;
}

.movie:hover {
    background: red;
}

/* نافذة كلمة المرور */
#passwordBox {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.9);
    z-index: 1000;
    align-items: center;
    justify-content: center;
}

.password-content {
    background: #111;
    padding: 25px;
    border-radius: 10px;
    text-align: center;
    width: 300px;
}

.password-content input {
    padding: 10px;
    width: 100%;
    border: none;
    border-radius: 5px;
    margin-bottom: 10px;
}

.password-content button {
    padding: 10px;
    width: 100%;
    border: none;
    background: red;
    color: white;
    cursor: pointer;
    border-radius: 5px;
}

#error {
    color: #ff4d4d;
    margin-top: 10px;
    display: none;
}

/* المشغل */
#player {
    display: none;
    position: fixed;
    inset: 0;
    background: black;
    z-index: 2000;
}

#close {
    position: absolute;
    top: 10px;
    right: 20px;
    font-size: 22px;
    cursor: pointer;
}
</style>
</head>

<body>

<header>🎬 منصة الأفلام</header>

<div class="section">
<h2>👑 أفلام العرش</h2>
<div class="movies">
    <div class="movie" onclick="openYT('https://www.youtube.com/watch?v=gcTkNV5Vg1E')">فيلم العرش 1</div>
    <div class="movie" onclick="openYT('https://www.youtube.com/watch?v=KPLWWIOCOOQ')">فيلم العرش 2</div>
    <div class="movie" onclick="openYT('https://www.youtube.com/watch?v=bjqEWgDVPe0')">فيلم تاريخي</div>
</div>
</div>

<div class="section">
<h2>🔥 أفلام عربية</h2>
<div class="movies">
    <div class="movie" onclick="openYT('https://www.youtube.com/watch?v=dQw4w9WgXcQ')">فيلم عربي 1</div>
    <div class="movie" onclick="openYT('https://www.youtube.com/watch?v=9bZkp7q19f0')">فيلم عربي 2</div>
    <div class="movie" onclick="askPassword()">صاحبك راجل 🔐</div>
</div>
</div>

<div class="section">
<h2>🍿 أفلام أخرى</h2>
<div class="movies">
    <div class="movie" onclick="openYT('https://www.youtube.com/watch?v=l482T0yNkeo')">فيلم أكشن</div>
    <div class="movie" onclick="openYT('https://www.youtube.com/watch?v=3tmd-ClpJxA')">فيلم دراما</div>
    <div class="movie" onclick="openYT('https://www.youtube.com/watch?v=fLexgOxsZu0')">فيلم عالمي</div>
</div>
</div>

<!-- نافذة كلمة المرور -->
<div id="passwordBox">
<div class="password-content">
    <h3>🔐 أدخل كلمة المرور</h3>
    <input type="password" id="password" placeholder="كلمة المرور">
    <button onclick="checkPassword()">دخول</button>
    <div id="error">هذا الكود غير صالح أو خاطئ</div>
</div>
</div>

<!-- المشغل -->
<div id="player">
<div id="close" onclick="closePlayer()">✖</div>
<iframe
sandbox="allow-same-origin allow-forms allow-popups allow-modals allow-scripts allow-pointer-lock"
width="100%" height="100%"
allow="fullscreen"
src="https://jorogo9825-wixstudio-com.filesusr.com/html/a225c5_576ba47e7d640551badc16a96383a6f2.html">
</iframe>
</div>

<script>
const correctPassword = "Hwod6G";

function openYT(link) {
    window.open(link, "_blank");
}

function askPassword() {
    document.getElementById("passwordBox").style.display = "flex";
    document.getElementById("error").style.display = "none";
    document.getElementById("password").value = "";
}

function checkPassword() {
    const pass = document.getElementById("password").value;
    if (pass === correctPassword) {
        document.getElementById("passwordBox").style.display = "none";
        document.getElementById("player").style.display = "block";
    } else {
        document.getElementById("error").style.display = "block";
    }
}

function closePlayer() {
    document.getElementById("player").style.display = "none";
}
</script>

</body>
</html>
