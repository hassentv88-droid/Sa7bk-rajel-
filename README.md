<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>سينما VIP</title>
<style>
body {
  margin:0;
  padding:0;
  font-family: Arial,sans-serif;
  background: linear-gradient(120deg,#0a0a0a,#1a1a1a);
  color:#fff;
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
  overflow:hidden;
}

.container {
  text-align:center;
  background: rgba(0,0,0,0.7);
  padding:40px;
  border-radius:15px;
  box-shadow:0 0 20px rgba(0,0,0,0.8);
  width:400px;
  position:relative;
  z-index:1;
}

button {
  padding:10px 20px;
  border:none;
  border-radius:5px;
  background:#ff4c4c;
  color:#fff;
  cursor:pointer;
  margin-top:10px;
}
button:hover {background:#ff1a1a;}

#spinner {
  display:none;
  margin:20px auto;
  width:50px;
  height:50px;
  border:6px solid rgba(255,255,255,0.3);
  border-top:6px solid #ff4c4c;
  border-radius:50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% {transform: rotate(0deg);}
  100% {transform: rotate(360deg);}
}

#backgroundCanvas {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index:0;
}
</style>
</head>
<body>
<canvas id="backgroundCanvas"></canvas>
<div class="container" id="app">
<h1>مرحبا بك في سينما VIP</h1>
<button id="loginBtn">تسجيل الدخول بجوجل</button>
<div id="spinner"></div>
</div>

<script type="module">
// ---------------- Firebase Setup -----------------
import { initializeApp } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-app.js";
import { getAuth, GoogleAuthProvider, signInWithPopup } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-auth.js";

const firebaseConfig = {
  apiKey: "AIzaSyCKcf5ADCZKBUe4-t9uiBB6e1KyJgusGPI",
  authDomain: "ttodj-dbcb6.firebaseapp.com",
  projectId: "ttodj-dbcb6",
  storageBucket: "ttodj-dbcb6.firebasestorage.app",
  messagingSenderId: "870906941163",
  appId: "1:870906941163:web:37bdb62b6e91a7663df8ae",
  measurementId: "G-3DKFGWNKYS"
};

const app = initializeApp(firebaseConfig);
const auth = getAuth();
const provider = new GoogleAuthProvider();

const loginBtn = document.getElementById('loginBtn');
const spinner = document.getElementById('spinner');

loginBtn.onclick = async ()=>{
  // اظهار spinner
  spinner.style.display = 'block';
  loginBtn.disabled = true;

  // تسجيل دخول Google
  await signInWithPopup(auth, provider);

  // 4 ثواني انتظار
  setTimeout(()=>{
    // بعد 4 ثواني افتح الصفحة الموالية (هنا مثال subscribe.html)
    window.location.href = 'subscribe.html';
  },4000);
};

// ---------------- Background animation ----------------
const canvas = document.getElementById('backgroundCanvas');
const ctx = canvas.getContext('2d');
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
const stars = [];
for(let i=0;i<150;i++){stars.push({x:Math.random()*canvas.width,y:Math.random()*canvas.height,r:Math.random()*2+1,dx:(Math.random()-0.5)*0.5,dy:(Math.random()-0.5)*0.5});}
function animate(){
  ctx.fillStyle='rgba(0,0,0,0.3)'; ctx.fillRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle='white';
  stars.forEach(s=>{
    ctx.beginPath();
    ctx.arc(s.x,s.y,s.r,0,Math.PI*2);
    ctx.fill();
    s.x+=s.dx; s.y+=s.dy;
    if(s.x<0)s.x=canvas.width;if(s.x>canvas.width)s.x=0;
    if(s.y<0)s.y=canvas.height;if(s.y>canvas.height)s.y=0;
  });
  requestAnimationFrame(animate);
}
animate();
</script>
</body>
</html>
