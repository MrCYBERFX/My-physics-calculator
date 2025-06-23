<!DOCTYPE html>
<html lang="en">
<h1 style="color:pink"><head>MR CYBER</head></h1>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Physics Formula Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #665566;
      padding: 20px;
      text-align: center;
    }

    .container {
      max-width: 500px;
      margin: auto;
      background: #fff;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    input, select, button {
      padding: 10px;
      width: 90%;
      margin: 10px 0;
      font-size: 1em;
    }

    #result {
      margin-top: 20px;
      font-size: 1.2em;
      color: #004d00;
    }

    .input-group {
      display: none;
    }

    .input-group.active {
      display: block;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Physics Formula Calculator</h2>

    <select id="formulaSelector" onchange="showInputs()">
      <option value="">-- Select Formula --</option>
      <option value="speed">Speed = Distance ÷ Time</option>
      <option value="acceleration">Acceleration = ΔVelocity ÷ Time</option>
      <option value="force">Force = Mass × Acceleration</option>
      <option value="ke">Kinetic Energy = ½ × Mass × Velocity²</option>
    </select>

    <!-- Speed -->
    <div id="speedInputs" class="input-group">
      <input type="number" id="speed_distance" placeholder="Distance (m)">
      <input type="number" id="speed_time" placeholder="Time (s)">
    </div>

    <!-- Acceleration -->
    <div id="accelerationInputs" class="input-group">
      <input type="number" id="accel_velocity" placeholder="ΔVelocity (m/s)">
      <input type="number" id="accel_time" placeholder="Time (s)">
    </div>

    <!-- Force -->
    <div id="forceInputs" class="input-group">
      <input type="number" id="force_mass" placeholder="Mass (kg)">
      <input type="number" id="force_acceleration" placeholder="Acceleration (m/s²)">
    </div>

    <!-- Kinetic Energy -->
    <div id="keInputs" class="input-group">
      <input type="number" id="ke_mass" placeholder="Mass (kg)">
      <input type="number" id="ke_velocity" placeholder="Velocity (m/s)">
    </div>

    <button onclick="calculate()">Calculate</button>
    <div id="result"></div>
  </div>

  <script>
    function showInputs() {
      const groups = document.querySelectorAll(".input-group");
      groups.forEach(group => group.classList.remove("active"));

      const selected = document.getElementById("formulaSelector").value;
      if (selected === "speed") document.getElementById("speedInputs").classList.add("active");
      else if (selected === "acceleration") document.getElementById("accelerationInputs").classList.add("active");
      else if (selected === "force") document.getElementById("forceInputs").classList.add("active");
      else if (selected === "ke") document.getElementById("keInputs").classList.add("active");

      document.getElementById("result").innerHTML = ""; // Clear previous result
    }

    function calculate() {
      const selected = document.getElementById("formulaSelector").value;
      const resultDiv = document.getElementById("result");

      let result = "";

      if (selected === "speed") {
        const d = parseFloat(document.getElementById("speed_distance").value);
        const t = parseFloat(document.getElementById("speed_time").value);
        if (d > 0 && t > 0) result = `Speed = ${(d / t).toFixed(2)} m/s`;
        else result = "Enter valid distance and time.";

      } else if (selected === "acceleration") {
        const v = parseFloat(document.getElementById("accel_velocity").value);
        const t = parseFloat(document.getElementById("accel_time").value);
        if (v > 0 && t > 0) result = `Acceleration = ${(v / t).toFixed(2)} m/s²`;
        else result = "Enter valid Δvelocity and time.";

      } else if (selected === "force") {
        const m = parseFloat(document.getElementById("force_mass").value);
        const a = parseFloat(document.getElementById("force_acceleration").value);
        if (m > 0 && a > 0) result = `Force = ${(m * a).toFixed(2)} N`;
        else result = "Enter valid mass and acceleration.";

      } else if (selected === "ke") {
        const m = parseFloat(document.getElementById("ke_mass").value);
        const v = parseFloat(document.getElementById("ke_velocity").value);
        if (m > 0 && v > 0) result = `Kinetic Energy = ${(0.5 * m * v * v).toFixed(2)} J`;
        else result = "Enter valid mass and velocity.";
      } else {
        result = "Please select a formula.";
      }

      resultDiv.innerHTML = result;
    }
  </script>
</body>
</html>
