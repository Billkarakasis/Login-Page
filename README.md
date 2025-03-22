# Login-Page
Front Page, Registeration Page, Login Page
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cyber Security Awareness</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #1a1a2e;
            color: white;
            margin: 0;
            padding: 0;
        }
        .container {
            max-width: 800px;
            margin: 50px auto;
            background: #16213e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(255, 255, 255, 0.2);
        }
        .buttons {
            margin-top: 20px;
        }
        button {
            background-color: #e94560;
            color: white;
            border: none;
            padding: 10px;
            width: 45%;
            border-radius: 5px;
            cursor: pointer;
            margin: 5px;
            font-size: 16px;
        }
        button:hover {
            background-color: #d63447;
        }
        input {
            display: block;
            width: 90%;
            margin: 10px auto;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .hidden {
            display: none;
        }
        h2 {
            color: #e94560;
        }
        .info-section {
            margin-top: 20px;
            text-align: left;
            padding: 10px;
        }
        .info-section p {
            font-size: 16px;
            line-height: 1.5;
        }
    </style>
</head>
<body>
    <div class="container" id="home-container">
        <h2>Welcome to Cyber Security Awareness</h2>
        <p>Protect yourself from cyber threats by learning the best security practices.</p>
        <div class="info-section">
            <h3>Why Cyber Security Matters?</h3>
            <p>Cyber threats are evolving every day. Hackers and malicious actors seek to steal personal data, disrupt systems, and exploit vulnerabilities. Being aware of cybersecurity risks is the first step toward protecting yourself online.</p>
            <h3>Best Practices:</h3>
            <ul>
                <li>Use strong, unique passwords for all your accounts.</li>
                <li>Enable two-factor authentication wherever possible.</li>
                <li>Be cautious of phishing emails and scam links.</li>
                <li>Keep your software and antivirus updated.</li>
                <li>Avoid sharing personal information on untrusted websites.</li>
            </ul>
        </div>
        <div class="buttons">
            <button onclick="showLogin()">Login</button>
            <button onclick="showRegister()">Register</button>
        </div>
    </div>

    <div class="container hidden" id="login-container">
        <h2>Login</h2>
        <input type="text" id="login-username" placeholder="Username">
        <input type="password" id="login-password" placeholder="Password">
        <button onclick="login()">Login</button>
        <p id="login-error-message" style="color: red;"></p>
        <p class="toggle-link" onclick="showHome()">Back to Home</p>
    </div>

    <div class="container hidden" id="register-container">
        <h2>Register</h2>
        <input type="text" id="register-username" placeholder="Username">
        <input type="password" id="register-password" placeholder="Password">
        <input type="email" id="register-email" placeholder="Email">
        <input type="text" id="register-mobile" placeholder="Mobile Number">
        <input type="text" id="register-address" placeholder="Address">
        <input type="text" id="register-postal" placeholder="Postal Code">
        <button onclick="register()">Register</button>
        <p id="register-error-message" style="color: red;"></p>
        <p class="toggle-link" onclick="showHome()">Back to Home</p>
    </div>

    <script>
        let users = {};

        function showLogin() {
            document.getElementById('home-container').classList.add('hidden');
            document.getElementById('login-container').classList.remove('hidden');
            document.getElementById('register-container').classList.add('hidden');
        }

        function showRegister() {
            document.getElementById('home-container').classList.add('hidden');
            document.getElementById('register-container').classList.remove('hidden');
            document.getElementById('login-container').classList.add('hidden');
        }

        function showHome() {
            document.getElementById('home-container').classList.remove('hidden');
            document.getElementById('login-container').classList.add('hidden');
            document.getElementById('register-container').classList.add('hidden');
        }

        function login() {
            const username = document.getElementById('login-username').value;
            const password = document.getElementById('login-password').value;
            const errorMessage = document.getElementById('login-error-message');

            if (users[username] && users[username].password === password) {
                alert('Login successful!');
                showHome();
            }else if (username === 'admin123' && password === '2025'){
                alert('Login successful!');
                showHome();
            } else {
                errorMessage.textContent = 'Invalid username or password';
            }
        }

        function register() {
            const username = document.getElementById('register-username').value;
            const password = document.getElementById('register-password').value;
            const email = document.getElementById('register-email').value;
            const mobile = document.getElementById('register-mobile').value;
            const address = document.getElementById('register-address').value;
            const postal = document.getElementById('register-postal').value;
            const errorMessage = document.getElementById('register-error-message');

            if (username && password && email && mobile && address && postal) {
                if (users[username]) {
                    errorMessage.textContent = 'Username already taken';
                } else {
                    users[username] = { password, email, mobile, address, postal };
                    alert('Registration successful! Now you can log in.');
                    showLogin();
                }
            } else {
                errorMessage.textContent = 'Please fill in all fields';
            }
        }
    </script>
</body>
</html>
