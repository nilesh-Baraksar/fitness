<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Fitness Game</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0;
      padding: 0;
      background: linear-gradient(to right, #f5f7fa, #c3cfe2);
    }
    header {
      background: #0077b6;
      padding: 1.5em;
      color: white;
      text-align: center;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    }
    .container {
      padding: 2em;
      max-width: 1000px;
      margin: auto;
    }
    .form-section, .game-section, .qa-section, .consult-section {
      margin-bottom: 2.5em;
      background: white;
      padding: 2em;
      border-radius: 15px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    }
    input, select, button, textarea {
      width: 100%;
      padding: 0.75em;
      margin-top: 0.75em;
      margin-bottom: 1.25em;
      border-radius: 8px;
      border: 1px solid #ccc;
      font-size: 1em;
    }
    button {
      background: #0077b6;
      color: white;
      border: none;
      cursor: pointer;
      transition: background 0.3s;
    }
    button:hover {
      background: #023e8a;
    }
    h2 {
      color: #023e8a;
    }
    .avatar {
      display: flex;
      justify-content: center;
      margin-top: 1em;
    }
    .avatar img {
      height: 180px;
      width: 180px;
      margin: 0 10px;
      border-radius: 12px;
      border: 3px solid #0077b6;
      object-fit: cover;
    }
    .section-title {
      display: flex;
      align-items: center;
      gap: 1em;
    }
    .section-title img {
      width: 40px;
      height: 40px;
    }
  </style>
</head>
<body>
  <header>
    <h1>💪 Fitness Game & Supplement Tracker</h1>
    <p>Experience supplement impact visually and track dosage based on your age & gender!</p>
  </header>
  <div class="container">
    <!-- Login/Register -->
    <div class="form-section">
      <div class="section-title">
        <img src="https://cdn-icons-png.flaticon.com/512/5087/5087579.png" alt="Login Icon" />
        <h2>Login / Register</h2>
      </div>
      <input type="text" id="username" placeholder="Username or Mobile Number" />
      <input type="password" id="password" placeholder="Password or OTP" />
      <button onclick="loginUser()">Login</button>
      <button onclick="registerUser()">Register</button>
    </div>

    <!-- Dose Calculator -->
    <div class="game-section">
      <div class="section-title">
        <img src="https://cdn-icons-png.flaticon.com/512/1024/1024726.png" alt="Dose Icon" />
        <h2>Fitness Product Dose Calculator</h2>
      </div>
      <select id="gender">
        <option value="male">Male</option>
        <option value="female">Female</option>
      </select>
      <input type="number" id="age" placeholder="Enter your Age" />
      <select id="product">
        <option value="protein">Protein Powder</option>
        <option value="creatine">Creatine</option>
        <option value="preworkout">Pre-Workout</option>
      </select>
      <button onclick="calculateDose()">Calculate Dose</button>
      <p id="doseResult"></p>

      <div class="avatar">
        <img id="avatarImg" src="https://cdn-icons-png.flaticon.com/512/4140/4140048.png" alt="Avatar" />
      </div>
    </div>

    <!-- Q&A Section -->
    <div class="qa-section">
      <div class="section-title">
        <img src="https://cdn-icons-png.flaticon.com/512/1055/1055687.png" alt="QA Icon" />
        <h2>Questions & Answers</h2>
      </div>
      <textarea id="userQuestion" placeholder="Ask your question... (e.g., Is creatine safe at 16?)"></textarea>
      <button onclick="submitQuestion()">Submit</button>
      <div id="qaResponses"></div>
    </div>

    <!-- Consultation -->
    <div class="consult-section">
      <div class="section-title">
        <img src="https://cdn-icons-png.flaticon.com/512/2920/2920277.png" alt="Consult Icon" />
        <h2>Expert Consultation</h2>
      </div>
      <input type="text" placeholder="Your Name" />
      <input type="email" placeholder="Your Email" />
      <textarea placeholder="Describe your issue or query..."></textarea>
      <button>Book Consultation</button>
    </div>
  </div>

  <script>
    function loginUser() {
      alert("Login feature with OTP/Social Media coming soon!");
    }

    function registerUser() {
      alert("Register feature with OTP/Social Media coming soon!");
    }

    function calculateDose() {
      const gender = document.getElementById("gender").value;
      const age = parseInt(document.getElementById("age").value);
      const product = document.getElementById("product").value;
      let dose = 0;
      let effect = "";

      if (!age || age <= 0) {
        alert("Enter a valid age.");
        return;
      }

      if (product === "protein") {
        dose = age < 18 ? 20 : 30;
        effect = "Helps in muscle recovery and strength gain.";
      } else if (product === "creatine") {
        dose = age < 18 ? 3 : 5;
        effect = "Boosts high-intensity exercise performance.";
      } else if (product === "preworkout") {
        dose = age < 18 ? 150 : 250;
        effect = "Improves workout energy and focus.";
      }

      document.getElementById("doseResult").innerHTML =
        `<strong>Recommended Dose:</strong> ${dose}g/ml<br><strong>Effect:</strong> ${effect}`;

      const avatar = document.getElementById("avatarImg");
      avatar.src = gender === "male"
        ? "https://cdn-icons-png.flaticon.com/512/4140/4140048.png"
        : "https://cdn-icons-png.flaticon.com/512/4140/4140051.png";
    }

    function submitQuestion() {
      const question = document.getElementById("userQuestion").value;
      if (!question) return alert("Please enter a question.");
      const responseBox = document.getElementById("qaResponses");
      const newResponse = document.createElement("p");
      newResponse.innerHTML = `<strong>User:</strong> ${question}<br><strong>Expert:</strong> Answer will be provided soon.`;
      responseBox.appendChild(newResponse);
      document.getElementById("userQuestion").value = "";
    }
  </script>
</body>
</html>
