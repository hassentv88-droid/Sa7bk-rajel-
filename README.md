<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>تسجيل الدخول - موقع سينمائي</title>
  <style>
    /* خلفية متحركة */
    body {
      margin: 0;
      padding: 0;
      font-family: Arial, Helvetica, sans-serif;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      background: linear-gradient(-45deg, #1a1a1a, #ff0000, #1a1a1a, #000);
      background-size: 400% 400%;
      animation: gradientBG 15s ease infinite;
    }

    @keyframes gradientBG {
      0% {background-position: 0% 50%;}
      50% {background-position: 100% 50%;}
      100% {background-position: 0% 50%;}
    }

    /* صندوق تسجيل الدخول */
    .login-container {
      background: rgba(0, 0, 0, 0.7);
      padding: 40px;
      border-radius: 10px;
      box-shadow: 0 0 20px rgba(255,0,0,0.5);
      width: 300px;
      text-align: center;
      color: #fff;
    }

    .login-container h2 {
      margin-bottom: 20px;
      color: #ff0000;
    }

    .login-container input {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: none;
      border-radius: 5px;
    }

    .login-container button {
      width: 100%;
      padding: 10px;
      background: #ff0000;
      border: none;
      border-radius: 5px;
      color: white;
      font-weight: bold;
      cursor: pointer;
      transition: background 0.3s;
    }

    .login-container button:hover {
      background: #cc0000;
    }

    .login-container a {
      color: #ff6666;
      text-decoration: none;
      font-size: 14px;
    }

    .login-container a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>
  <div class="login-container">
    <h2>تسجيل الدخول</h2>
    <form>
      <input type="text" placeholder="اسم المستخدم" required>
      <input type="password" placeholder="كلمة المرور" required>
      <button type="submit">دخول</button>
    </form>
    <p><a href="#">نسيت كلمة المرور؟</a></p>
  </div>
</body>
</html>
