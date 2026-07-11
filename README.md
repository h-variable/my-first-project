# my-first-project
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Agriculture Management Login</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

  <style>
    /* Reset */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    /* ====================
       BACKGROUND IMAGE SETUP
       ==================== */
    /* POSITION: Lines 23-39 - Body styling with background image */
    /* Explanation: The background image is applied to the entire page body
       - background-image: Loads cows.jpg from the same directory
       - background-size: cover ensures image covers entire viewport
       - background-position: center centers the image
       - background-repeat: no-repeat prevents tiling
       - position: relative allows for overlay positioning
    */
    body {
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background-image: url('goto.jpg'); /* IMAGE PLACEMENT HERE */
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      position: relative;
    }

    /* ====================
       OVERLAY FOR READABILITY
       ==================== */
    /* POSITION: Lines 41-51 - Pseudo-element overlay
       Explanation: This creates a semi-transparent black overlay over the background image
       to improve text contrast. The overlay sits behind the login card (z-index: -1)
       but in front of the background image
    */
    body::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.4); /* Dark overlay for contrast */
      z-index: -1;
    }

    /* ====================
       LOGIN CARD STYLING
       ==================== */
    /* POSITION: Lines 53-64 - Main login container */
    /* Explanation: The login card sits on top of the background and overlay
       with a solid white background for readability
    */
    .login-card {
  background: #1B5E20;
  color: white;
  padding: 40px 30px;
  border-radius: 12px;
  width: 100%;
  max-width: 380px;
  text-align: center;
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.2);
  animation: fadeIn 0.6s ease-in-out;
}
    

    /* Logo */
    .logo {
      font-size: 42px;
      color: #42d77d;
      margin-bottom: 15px;
    }

    /* Titles */
    .login-card h2 {
      margin-bottom: 8px;
      font-size: 24px;
      color: #000000;
    }

    .subtitle {
      font-size: 14px;
      color: #666;
      margin-bottom: 25px;
    }

    /* Inputs */
    .input-group {
      display: flex;
      align-items: center;
      border: 1px solid #ddd;
      border-radius: 8px;
      padding: 12px;
      margin-bottom: 18px;
      background: #fafafa;
      transition: 0.3s;
    }

    .input-group i {
      margin-right: 10px;
      color: #777;
    }

    .input-group input {
      border: none;
      outline: none;
      flex: 1;
      font-size: 14px;
      background: transparent;
    }

    .input-group:focus-within {
      border-color: #42d77d;
      background: #fff;
    }

    /* Password visibility toggle */
    .show-password-container {
      display: flex;
      align-items: center;
      margin: -10px 0 15px 0;
      font-size: 13px;
      color: white;
    }

    .show-password-container input {
      margin-right: 8px;
    }

    /* Options */
    .options {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 13px;
      margin-bottom: 20px;
    }

    .options a {
      text-decoration: none;
      color: #42d77d;
      transition: 0.3s;
    }

    .options a:hover {
      text-decoration: underline;
    }

    /* Button */
    .btn {
      background: #42d77d;
      color: #fff;
      border: none;
      width: 100%;
      padding: 14px;
      font-size: 15px;
      font-weight: bold;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.3s;
    }

    .btn:hover {
      background: #36b769;
    }

    /* Links */
    .login-link {
      margin-top: 15px;
      font-size: 13px;
      color: #444;
    }

    .login-link a {
      color: #42d77d;
      text-decoration: none;
      font-weight: 600;
      transition: 0.3s;
    }

    .register-link {
      margin-top: 15px;
      font-size: 13px;
      color: #444;
    }

    .register-link a {
      color: #42d77d;
      text-decoration: none;
      font-weight: 600;
      transition: 0.3s;
    }

    .register-link a:hover,
    .login-link a:hover {
      text-decoration: underline;
    }

    /* Footer */
    .footer-note {
      margin-top: 20px;
      font-size: 12px;
      color: #999;
    }

    /* Animation */
    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(-20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
  </style>
</head>
<body>

  <div class="login-card">
    <div class="logo"><i class="fas fa-tractor"></i></div>
    <h2>AgriSys Login</h2>
    <p class="subtitle">Sign in to manage your farm</p>

    <!-- Error Handling -->
    <script>
      const params = new URLSearchParams(window.location.search);
      if (params.get("error") === "1") {
          alert("Invalid username or password");
      }
    </script>

    <!-- Login Form -->
    <form action="backend/login.php" method="POST">
      <!-- Username input -->
      <div class="input-group">
        <i class="fas fa-user"></i>
        <input type="text" name="username" placeholder="Username" required>
      </div>
      
      <!-- Password input -->
      <div class="input-group">
        <i class="fas fa-lock"></i>
        <input type="password" name="password" id="password" placeholder="Password" required>
      </div>
      
      <!-- Show Password checkbox -->
      <div class="show-password-container">
        <input type="checkbox" id="showPassword">
        <label for="showPassword">Show Password</label>
      </div>

      <!-- Password visibility toggle script -->
  <script>
    document.getElementById('showPassword').addEventListener('change', function() {
        const passwordField = document.getElementById('password');
        passwordField.type = this.checked ? 'text' : 'password';
    });
  </script>


      <!-- Remember me & Forgot password -->
      <div class="options">
        <label><input type="checkbox"> </label>
        <a href="#">Forgot Password?</a>
      </div>

      <!-- Submit button -->
      <button type="submit" class="btn">Login</button>
    </form>

    <p class="login-link">
      Already have an account? <a href="index.html">Login</a>
    </p>

    <p class="register-link">
      Don't have an account? <a href="reg.html">Register</a>
    </p>

    <p class="footer-note">© 2025 Agriculture Management System</p>
  </div>

  
</body>
</html>
