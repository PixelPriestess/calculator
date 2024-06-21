# calculator
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #a97373;
            margin: 0;
            font-family: Arial, sans-serif;
        }

        .calculator {
            width: 300px;
            border: 2px solid #e88181;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            background-color: rgb(127, 78, 78);
        }

        .display {
            height: 60px;
            background-color: #000000;
            color: rgb(141, 98, 98);
            font-size: 2em;
            display: flex;
            justify-content: flex-end;
            align-items: center;
            padding: 0 20px;
            box-sizing: border-box;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1px;
        }

        .btn {
            height: 60px;
            font-size: 1.5em;
            border: none;
            cursor: pointer;
            background-color: #997777;
            transition: background-color 0.3s;
        }

        .btn:hover {
            background-color: #ab7474;
        }

        .btn:active {
            background-color: #8b4b4b;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button class="btn" onclick="clearDisplay()">C</button>
            <button class="btn" onclick="appendToDisplay('7')">7</button>
            <button class="btn" onclick="appendToDisplay('8')">8</button>
            <button class="btn" onclick="appendToDisplay('9')">9</button>
            <button class="btn" onclick="appendToDisplay('/')">/</button>

            <button class="btn" onclick="appendToDisplay('4')">4</button>
            <button class="btn" onclick="appendToDisplay('5')">5</button>
            <button class="btn" onclick="appendToDisplay('6')">6</button>
            <button class="btn" onclick="appendToDisplay('*')">*</button>

            <button class="btn" onclick="appendToDisplay('1')">1</button>
            <button class="btn" onclick="appendToDisplay('2')">2</button>
            <button class="btn" onclick="appendToDisplay('3')">3</button>
            <button class="btn" onclick="appendToDisplay('-')">-</button>

            <button class="btn" onclick="appendToDisplay('0')">0</button>
            <button class="btn" onclick="appendToDisplay('.')">.</button>
            <button class="btn" onclick="calculateResult()">=</button>
            <button class="btn" onclick="appendToDisplay('+')">+</button>
        </div>
    </div>
    <script>
        let displayElement = document.getElementById('display');
        let currentInput = '';

        function appendToDisplay(value) {
            if (currentInput === '0' && value !== '.') {
                currentInput = value;
            } else {
                currentInput += value;
            }
            updateDisplay();
        }

        function clearDisplay() {
            currentInput = '';
            updateDisplay();
        }

        function updateDisplay() {
            displayElement.textContent = currentInput || '0';
        }

        function calculateResult() {
            try {
                currentInput = eval(currentInput).toString();
            } catch (e) {
                currentInput = 'Error';
            }
            updateDisplay();
        }
    </script>
</body>
</html>
