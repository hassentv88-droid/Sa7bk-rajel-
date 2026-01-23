<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>مشاهدة الفيلم</title>

<style>
body{
  background:#000;
  color:#fff;
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
  font-family:Arial;
}
.box{
  background:#111;
  padding:25px;
  border-radius:10px;
  text-align:center;
  width:300px;
}
input{
  width:100%;
  padding:10px;
  margin-top:10px;
  border:none;
  border-radius:5px;
}
button{
  margin-top:15px;
  padding:10px;
  width:100%;
  border:none;
  background:red;
  color:#fff;
  font-size:16px;
  border-radius:5px;
  cursor:pointer;
}
#error{
  color:#ff4d4d;
  margin-top:10px;
}
</style>
</head>

<body>

<div class="box">
  <h3>لمشاهدة الفيلم</h3>
  <p>الرجاء إدخال كلمة المرور</p>
  <input type="password" id="password" placeholder="كلمة المرور">
  <button onclick="checkPassword()">دخول</button>
  <div id="error"></div>
</div>

<script>
const passwords = [
  "MOVIE123",
  "VIP456",
  "WATCH789",
  "FILM2026"
];

function checkPassword(){
  var input = document.getElementById("password").value;
  var error = document.getElementById("error");

  var used = JSON.parse(localStorage.getItem("usedPasswords") || "[]");

  if(passwords.indexOf(input) === -1){
    error.innerText = "كلمة المرور غير صحيحة";
    return;
  }

  if(used.indexOf(input) !== -1){
    error.innerText = "هذه الكلمة تم استعمالها من قبل";
    return;
  }

  used.push(input);
  localStorage.setItem("usedPasswords", JSON.stringify(used));

  // 🔁 تحويل مباشر
  window.location.replace("https://jorogo9825.wixstudio.com/sahbekrajel22");
}
</script>

</body>
</html>
