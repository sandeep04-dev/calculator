<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Advanced Calculator</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: linear-gradient(to right, #1f4037, #99f2c8);
    }
    .calculator {
      background-color: #202124;
      border-radius: 20px;
      padding: 30px;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
      width: 340px;
    }
    .display {
      background: #000;
      color: #0f0;
      font-size: 2em;
      padding: 20px;
      border-radius: 10px;
      margin-bottom: 20px;
      text-align: right;
      overflow-x: auto;
    }
    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 15px;
    }
    .btn {
      background-color: #333;
      color: white;
      font-size: 1.5em;
      padding: 20px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      transition: 0.2s;
    }
    .btn:hover {
      background-color: #444;
    }
    .btn.operator {
      background-color: #f57c00;
    }
    .btn.equal {
      background-color: #388e3c;
      grid-column: span 2;
    }
    .btn.clear {
      background-color: #d32f2f;
      grid-column: span 2;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <div id="display" class="display">0</div>
    <div class="buttons">
      <button class="btn clear" onclick="clearDisplay()">C</button>
      <button class="btn" onclick="backspace()">⌫</button>
      <button class="btn operator" onclick="append('/')">÷</button>
      <button class="btn operator" onclick="append('*')">×</button>
      <button class="btn" onclick="append('7')">7</button>
      <button class="btn" onclick="append('8')">8</button>
      <button class="btn" onclick="append('9')">9</button>
      <button class="btn operator" onclick="append('-')">−</button>
      <button class="btn" onclick="append('4')">4</button>
      <button class="btn" onclick="append('5')">5</button>
      <button class="btn" onclick="append('6')">6</button>
      <button class="btn operator" onclick="append('+')">+</button>
      <button class="btn" onclick="append('1')">1</button>
      <button class="btn" onclick="append('2')">2</button>
      <button class="btn" onclick="append('3')">3</button>
      <button class="btn" onclick="append('.')">.</button>
      <button class="btn" onclick="append('0')">0</button>
      <button class="btn equal" onclick="calculate()">=</button>
    </div>
  </div>

  <script>
    const display = document.getElementById('display');

    function append(value) {
      if (display.innerText === '0') display.innerText = '';
      display.innerText += value;
    }

    function clearDisplay() {
      display.innerText = '0';
    }

    function backspace() {
      display.innerText = display.innerText.slice(0, -1);
      if (display.innerText === '') display.innerText = '0';
    }

    function calculate() {
      try {
        display.innerText = eval(display.innerText.replace(/÷/g, '/').replace(/×/g, '*'));
      } catch (e) {
        display.innerText = 'Error';
      }
    }
  </script>
</body>
</html>
