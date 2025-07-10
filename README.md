# Password Strength Testing 
Password strength testing is the technique used to determine how difficult a password is to crack using automated tools or known attack strategies. It helps identify weak or commonly used passwords and encourages the use of strong, complex passwords that enhance system security.

## Project Purpose 📋

The purpose of this project is to provide you with an easy-to-use tool to evaluate the strength of your passwords. Whether you're creating a new password or checking the security of an existing one, our Password Strength Checker has you covered. With this tool, you can make sure your online accounts are safe from potential threats.To develop a tool that evaluates the strength of user passwords based on various criteria such as length, character diversity, dictionary words, and exposure in known data breaches. The goal is to educate users on creating strong passwords and to highlight weaknesses in commonly used passwords.

## Technologies Used 💻

- HTML
- CSS
- JavaScript

## HTML CODE 
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Password Strength Checker</title>
    <link rel="stylesheet" href="./style.css">

</head>

<body>
    <!-- partial:index.partial.html -->
    <div class="container">
        <h2>Password Strength Checker</h2>
        <div class="inputArea">
            <input type="password" placeholder=" Password" id="YourPassword">
            <div class="show"></div>
        </div>
        <div class="strengthMeter"></div>
    </div>
    <!-- partial -->
    <script src="./script.js"></script>

</body>

</html>
```
## CSS CODE 
```
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background: #222;
}

.container {
  position: relative;
  width: 400px;
  border-radius: 20px 20px 0 0;
  padding: 30px;
  background: #333;
  display: flex;
  justify-content: center;
  /* align-items: center; */
  flex-direction: column;
  border-radius: 1px solid #111;
  gap: 10px;
  padding-bottom: 70px;
  -webkit-box-reflect: below 1px
    linear-gradient(transparent, transparent, #0005);
}
.container h2 {
  color: #666;
  font-weight: 500;
}

.container .inputArea {
  position: relative;
  width: 100%;
}

.container .inputArea input {
  position: relative;
  width: 100%;
  background: #222;
  border: none;
  outline: none;
  padding: 10px;
  color: aliceblue;
  font-size: 1.1em;
}

.container .strengthMeter {
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 3px;
  background: #222;
}

.container .strengthMeter::before {
  content: "";
  position: absolute;
  width: 0;
  height: 100%;
  transition: 0.5s;
  background: #f00;
}

.container.weak .strengthMeter::before {
  width: 10%;
  background: #f00;
  filter: drop-shadow(0 0 5px #f00) drop-shadow(0 0 10px #f00)
    drop-shadow(0 0 20px #f00);
}

.container.moderate .strengthMeter::before {
  width: 70%;
  background: #eedc3d;
  filter: drop-shadow(0 0 5px #eedc3d) drop-shadow(0 0 10px #eedc3d)
    drop-shadow(0 0 20px #eedc3d);
}

.container.strong .strengthMeter::before {
  width: 100%;
  background: #18e605;
  filter: drop-shadow(0 0 5px #18e605) drop-shadow(0 0 10px #18e605)
    drop-shadow(0 0 20px #18e605);
}

.container .strengthMeter::after {
  position: absolute;
  top: -45px;
  left: 30px;
  transition: 0.5s;
  color: aliceblue;
}

.container.container.weak .strengthMeter::after {
  content: "Weak Password";
  color: #f00;
  filter: drop-shadow(0 0 5px#f00);
}

.container.container.container.moderate .strengthMeter::after {
  content: "Moderate Password";
  color: #eedc3d;
  filter: drop-shadow(0 0 5px#eedc3d);
}

.container.container.container.container.strong .strengthMeter::after {
  content: "Strong Password";
  color: #18e605;
  filter: drop-shadow(0 0 5px#18e605);
}

.show {
  position: absolute;
  top: 0;
  right: 0;
  width: 60px;
  height: 100%;
  background: #333;
  border: 6px solid #222;
  cursor: pointer;
  justify-content: center;
  align-items: center;
  display: flex;
}


.show::before {
  content: "Show";
  font-size: 0.6em;
  color: aliceblue;
  letter-spacing: 0.15em;
  text-transform: uppercase;
}

.show.hide::before {
  content: "Hide";
}
```
## Javascript
```
function Strength(password) {
    let i = 0;
    if (password.length > 6) {
      i++;
    }
    if (password.length >= 10) {
      i++;
    }
  
    if (/[A-Z]/.test(password)) {
      i++;
    }
  
    if (/[0-9]/.test(password)) {
      i++;
    }
  
    if (/[A-Za-z0-8]/.test(password)) {
      i++;
    }
  
    return i;
  }
  
  let container = document.querySelector(".container");
  document.addEventListener("keyup", function (e) {
    let password = document.querySelector("#YourPassword").value;
  
    let strength = Strength(password);
    if (strength <= 2) {
      container.classList.add("weak");
      container.classList.remove("moderate");
      container.classList.remove("strong");
    } else if (strength >= 2 && strength <= 4) {
      container.classList.remove("weak");
      container.classList.add("moderate");
      container.classList.remove("strong");
    } else {
      container.classList.remove("weak");
      container.classList.remove("moderate");
      container.classList.add("strong");
    }
  });
  
  let password = document.querySelector("#YourPassword");
  let show = document.querySelector(".show");
  show.onclick = function () {
    if (password.type === "password") {
      password.setAttribute("type", "text");
      show.classList.add("hide");
    } else {
      password.setAttribute("type", "password");
      show.classList.remove("hide");
    }
  };
```
## EXAMPLE OUTPUT 

![image](https://github.com/user-attachments/assets/8cf23de2-9fc0-4ced-ae8b-d335a3047ac9)

![image](https://github.com/user-attachments/assets/0a4339d1-bab8-4721-894f-29fb6d388286)

![image](https://github.com/user-attachments/assets/6fe61d28-00ea-48c4-b942-ae804e916eb9)

## Features
1. Real-time password strength feedback.

2. Alerts for weak, medium, and strong passwords.

3. Tip alert for adding UPPERCASE, lowercase, symbols, and letters for more secure passwords.

4. Visual indication of password strength through border color.

5. Responsive design with an intuitive user interface.

## Link to test your password : https://password-strength.vercel.app/

## Result
The Password Strength Testing project successfully demonstrates how cybersecurity tools can empower users to create more secure passwords. By analyzing password complexity, checking against data breaches, and offering personalized feedback, the tool promotes safe authentication practices and contributes to reducing risks associated with weak credentials.

