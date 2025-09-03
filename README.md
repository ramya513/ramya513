<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Registration Form</title>
    <style>
        body { font-family: Arial, sans-serif; }
        form { max-width: 400px; margin: 40px auto; padding: 24px; border: 1px solid #ccc; border-radius: 8px; }
        label { display: block; margin-top: 16px; }
        input { width: 100%; padding: 8px; box-sizing: border-box; }
        .error { color: red; margin-top: 8px; }
        button { margin-top: 24px; padding: 10px 20px; }
    </style>
</head>
<body>
    <form id="registrationForm" autocomplete="off">
        <h2>Register</h2>
        <label>
            Username:
            <input type="text" id="username" required>
        </label>
        <label>
            Email:
            <input type="email" id="email" required>
        </label>
        <label>
            Password:
            <input type="password" id="password" required minlength="6">
        </label>
        <label>
            Confirm Password:
            <input type="password" id="confirmPassword" required>
        </label>
        <div class="error" id="errorMsg"></div>
        <button type="submit">Register</button>
    </form>

    <script>
        document.getElementById("registrationForm").addEventListener("submit", function(e) {
            e.preventDefault();
            const username = document.getElementById("username").value.trim();
            const email = document.getElementById("email").value.trim();
            const password = document.getElementById("password").value;
            const confirmPassword = document.getElementById("confirmPassword").value;
            const errorMsg = document.getElementById("errorMsg");

            if (!username || !email || !password || !confirmPassword) {
                errorMsg.textContent = "All fields are required.";
                return;
            }
            if (password.length < 6) {
                errorMsg.textContent = "Password must be at least 6 characters long.";
                return;
            }
            if (password !== confirmPassword) {
                errorMsg.textContent = "Passwords do not match.";
                return;
            }
            errorMsg.textContent = "";
            alert("Registration successful! (You can now connect this to your backend.)");
            // You can send data to your server here using fetch()/XMLHttpRequest/etc.
        });
    </script>
</body>
</html>
