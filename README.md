<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>75% Attendance Checker - GTU</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f9f9f9;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      padding: 20px;
    }

    .container {
      background: white;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 8px 16px rgba(0,0,0,0.1);
      max-width: 400px;
      width: 100%;
      text-align: center;
    }

    h1 {
      margin-bottom: 20px;
      color: #222;
    }

    input {
      width: 100%;
      padding: 10px;
      margin-bottom: 15px;
      border: 1px solid #ddd;
      border-radius: 8px;
      font-size: 16px;
    }

    button {
      padding: 10px 20px;
      font-size: 16px;
      background: #007BFF;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background: #0056b3;
    }

    .result {
      margin-top: 20px;
      font-size: 18px;
      color: #333;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>📚 GTU 75% Attendance</h1>
    
    <input type="number" id="total" placeholder="Total classes held">
    <input type="number" id="attended" placeholder="Classes attended">
    <button onclick="calculate()">Check</button>

    <div class="result" id="result"></div>
  </div>

  <script>
    function calculate() {
      const total = parseInt(document.getElementById("total").value);
      const attended = parseInt(document.getElementById("attended").value);
      const result = document.getElementById("result");

      if (isNaN(total) || isNaN(attended) || total <= 0 || attended < 0 || attended > total) {
        result.innerHTML = "⚠️ Please enter valid numbers.";
        return;
      }

      const percent = (attended / total) * 100;
      result.innerHTML = `🎯 Current attendance: ${percent.toFixed(2)}%`;

      if (percent >= 75) {
        result.innerHTML += "<br>✅ You're safe! You meet the 75% requirement.";
      } else {
        let x = 0;
        while (((attended + x) / (total + x)) * 100 < 75) {
          x++;
        }
        result.innerHTML += `<br>⚠️ Attend next <strong>${x}</strong> classes without missing to reach 75%.`;
      }
    }
  </script>

</body>
</html>
