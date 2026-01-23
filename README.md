<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>تسجيل الدخول - موقع سينمائي</title>

  <link href="https://fonts.googleapis.com/css2?family=Bungee+Inline&display=swap" rel="stylesheet">

  <style>
    /* الجسم كله والخلفية */
    body {
      margin: 0;
      padding: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff0000, #800000);
      font-family: 'Bungee Inline', cursive;
    }

    /* صندوق تسجيل الدخول في الوسط */
    .login-container {
      background: rgba(0, 0, 0, 0.85);
      padding: 40px 30px;
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(255, 0, 0, 0.7);
      width: 90%;
      max-width: 350px;
      text-align: center;
      color: #fff;
    }

    .login-container h2 {
      font-size: 32px;
      margin-bottom: 25px;
      color: #ffcc00;
      text-shadow: 0 0 10px #ffcc00, 0 0 20px #ff6600;
    }

    .login-container input {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border: none;
      border-radius: 8px;
      font-family: 'Bungee Inline', cursive;
      font-size: 16px;
    }

    .login-container button {
      width: 100%;
      padding: 12px;
      background: #ff0000;
      border: none;
      border-radius: 8px;
      color: white;
      font-weight: bold;
      cursor: pointer;
      transition: 0.3s;
      font-family: 'Bungee Inline', cursive;
      font-size: 16px;
    }

    .login-container button:hover {
      background: #cc0000;
    }

    .login-container a {
      display: block;
      margin-top: 12px;
      color: #ffcc00;
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
    <a href="#">نسيت كلمة المرور؟</a>
  </div>
</body>
</html>
