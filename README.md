<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>سينما VIP</title>
<style>
body {margin:0;padding:0;font-family: Arial, sans-serif;background: linear-gradient(120deg,#0a0a0a,#1a1a1a);color:#fff;display:flex;justify-content:center;align-items:center;height:100vh;overflow:hidden;}
.container {text-align:center;background: rgba(0,0,0,0.7);padding:40px;border-radius:15px;box-shadow:0 0 20px rgba(0,0,0,0.8);width:400px;position:relative;z-index:1;}
input {padding:10px;margin:10px 0;border-radius:5px;border:none;width:90%;}
button {padding:10px 20px;border:none;border-radius:5px;background:#ff4c4c;color:#fff;cursor:pointer;margin-top:10px;}
button:hover {background:#ff1a1a;}
#backgroundCanvas {position:absolute;top:0;left:0;width:100%;height:100%;z-index:0;}
</style>
</head>
<body>
<canvas id="backgroundCanvas"></canvas>
<div class="container" id="app">
<h1>مرحبا بك في سينما VIP</h1>
<button id="loginBtn">تسجيل الدخول بجوجل</button>
</div>

<script type="module">
// ---------------- Firebase Setup ----------------
import { initializeApp } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-app.js";
import { getAuth, GoogleAuthProvider, signInWithPopup, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-auth.js";
import { getFirestore, doc, getDoc, setDoc, updateDoc } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-firestore.js";

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
const db = getFirestore(app);

// ---------------- Google Login ----------------
document.getElementById('loginBtn').onclick = ()=>{ signInWithPopup(auth, provider); };

// ---------------- Auth State ----------------
onAuthStateChanged(auth, async user=>{
  if(user){
    const userRef = doc(db,'users',user.uid);
    const userSnap = await getDoc(userRef);

    if(userSnap.exists() && userSnap.data().subActive){
      // User subscribed
      document.getElementById('app').innerHTML = `<h1>مرحبا ${user.displayName}</h1>
      <p>اشتراكك فعال حتى ${new Date(userSnap.data().subEnd).toLocaleDateString()}</p>
      <button id='logoutBtn'>تسجيل الخروج</button>`;
      document.getElementById('logoutBtn').onclick = ()=>{auth.signOut(); location.reload();};
    } else {
      // Enter subscription code
      document.getElementById('app').innerHTML = `<h2>ادخل كود الاشتراك</h2>
      <input type='text' id='codeInput' placeholder='اكتب الكود هنا'>
      <button id='activateBtn'>تفعيل الاشتراك</button>
      <p id='message'></p>
      <hr><h3>لوحة Admin (للكود)</h3>
      <input type='text' id='newCode' placeholder='اكتب الكود الجديد'>
      <input type='number' id='days' placeholder='مدة الاشتراك بالايام'>
      <button id='generateBtn'>توليد الكود</button>
      <p id='adminMsg'></p>`;

      // Activate subscription code
      document.getElementById('activateBtn').onclick = async ()=>{
        const codeVal = document.getElementById('codeInput').value.trim();
        const codeRef = doc(db,'codes',codeVal);
        const codeSnap = await getDoc(codeRef);
        if(!codeSnap.exists()){ document.getElementById('message').innerText='الكود غير صالح'; return; }
        if(codeSnap.data().used){ document.getElementById('message').innerText='الكود مستعمل'; return; }
        const expires = new Date(); expires.setDate(expires.getDate()+codeSnap.data().days);
        await setDoc(userRef,{subActive:true,subEnd:expires.toISOString()});
        await updateDoc(codeRef,{used:true});
        location.reload();
      };

      // Admin code generation
      document.getElementById('generateBtn').onclick = async ()=>{
        if(user.email !== 'YOUR_EMAIL@gmail.com'){ document.getElementById('adminMsg').innerText='ليس لديك صلاحية'; return; }
        const code = document.getElementById('newCode').value.trim();
        const days = parseInt(document.getElementById('days').value);
        if(!code || !days){ document.getElementById('adminMsg').innerText='املأ جميع الحقول'; return; }
        const codeRef = doc(db,'codes',code);
        await setDoc(codeRef,{used:false,days});
        document.getElementById('adminMsg').innerText=`تم توليد الكود: ${code} لمدة ${days} يوم`;
      };
    }
  }
});

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
  stars.forEach(s=>{ctx.beginPath();ctx.arc(s.x,s.y,s.r,0,Math.PI*2);ctx.fill(); s.x+=s.dx; s.y+=s.dy; if(s.x<0)s.x=canvas.width;if(s.x>canvas.width)s.x=0;if(s.y<0)s.y=canvas.height;if(s.y>canvas.height)s.y=0;});
  requestAnimationFrame(animate);
}
animate();
</script>
</body>
</html>
