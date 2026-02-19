<!DOCTYPE html>
<html>
<head>
    <title>Advanced Cyber Security Login</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <style>
        *{
            margin:0;
            padding:0;
            box-sizing:border-box;
            font-family: Arial, sans-serif;
        }

        body{
            height:100vh;
            display:flex;
            justify-content:center;
            align-items:center;
            background: linear-gradient(135deg,#0f2027,#203a43,#2c5364);
            color:aqua;
        }

        
        .container{
            width:380px;
            background:rgba(255,255,255,0.1);
            padding:30px;
            border-radius:15px;
            backdrop-filter:blur(10px);
            box-shadow:0 10px 25px rgba(0,0,0,0.5);
        }

        h2{
            text-align:center;
            margin-bottom:20px;
        }

        input{
            width:100%;
            padding:10px;
            margin-bottom:10px;
            border:none;
            border-radius:8px;
            outline:none;
        }

        button{
            width:100%;
            padding:10px;
            border:none;
            border-radius:8px;
            background:#00c6ff;
            color:white;
            font-weight:bold;
            cursor:pointer;
            transition:0.3s;
        }

        button:hover{
            background:#0072ff;
        }

        .error{
            font-size:13px;
            color:yellow;
            margin-bottom:8px;
        }

        .strength-bar{
            height:8px;
            width:100%;
            background:#ccc;
            border-radius:10px;
            overflow:hidden;
            margin-bottom:10px;
        }

        .strength-fill{
            height:100%;
            width:0%;
            transition:0.3s;
        }

        .tips{
            margin-top:15px;
            font-size:13px;
            opacity:0.9;
        }

        .toggle{
            position:relative;
            top:-38px;
            right:-310px;
            cursor:pointer;
            font-size:12px;
            color:black;
        }

    </style>
</head>

<body>

<div class="container">
    <h2>🔐 Secure Login</h2>

    <input type="text" id="email" placeholder="Enter Email" onkeyup="validateEmail()">
    <div id="emailError" class="error"></div>

    <input type="password" id="password" placeholder="Enter Password" onkeyup="checkStrength()">
    <span class="toggle" onclick="togglePassword()">Show</span>

    <div class="strength-bar">
        <div class="strength-fill" id="strength-fill"></div>
    </div>

    <div id="passwordMessage" class="error"></div>

    <button onclick="login()">Login</button>

    <div class="tips">
        <strong>🛡 Cyber Security Tips:</strong>
        <ul>
            <li>Use strong & unique passwords.</li>
            <li>Enable 2FA authentication.</li>
            <li>Never share OTP with anyone.</li>
            <li>Avoid clicking unknown links.</li>
            <li>Use at least 8-12 characters.</li>
            <li>Include uppercase & lowercase letters.</li>
            <li>Add numbers and special characters.</li>
            <li>Avoid common passwords (123456, password).</li>
            <li>Do not share your password with anyone.</li>
            <li>Enable Two-Factor Authentication (2FA).</li>
        </ul>
    </div>
</div>

<script>

function validateEmail(){
    var email = document.getElementById("email").value;
    var emailError = document.getElementById("emailError");

    var pattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;

    if(email.match(pattern)){
        emailError.innerHTML = "Valid Email ✅";
        emailError.style.color = "lightgreen";
        return true;
    } else {
        emailError.innerHTML = "Invalid Email ❌";
        emailError.style.color = "yellow";
        return false;
    }
}

function checkStrength(){
    var password = document.getElementById("password").value;
    var strengthFill = document.getElementById("strength-fill");
    var message = document.getElementById("passwordMessage");

    var strength = 0;

    if(password.length >= 8) strength++;
    if(password.match(/[A-Z]/)) strength++;
    if(password.match(/[a-z]/)) strength++;
    if(password.match(/[0-9]/)) strength++;
    if(password.match(/[@#$%^&*]/)) strength++;

    var width = strength * 20;
    strengthFill.style.width = width + "%";

    if(strength <= 2){
        strengthFill.style.background = "red";
        message.innerHTML = "Weak Password";
        message.style.color = "red";
        return false;
    }
    else if(strength <= 4){
        strengthFill.style.background = "orange";
        message.innerHTML = "Medium Password";
        message.style.color = "orange";
        return true;
    }
    else{
        strengthFill.style.background = "lime";
        message.innerHTML = "Strong Password";
        message.style.color = "lime";
        return true;
    }
}

function togglePassword(){
    var pass = document.getElementById("password");
    if(pass.type === "password"){
        pass.type = "text";
    } else {
        pass.type = "password";
    }
}

function login(){
    if(validateEmail() && checkStrength()){
        alert("Login Successful ✅");
    } else {
        alert("Please Enter Valid Details ❌");
    }
}

</script>

</body>
</html># Password-strength-check
 Password-strength- checker +advanced login 
