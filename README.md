<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Comfort Calculator</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: #f5f5f5;
        }

        .calculator {
            background: #ffffff;
            padding: 25px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            width: 350px;
        }

        .display {
            width: 100%;
            height: 80px;
            margin-bottom: 20px;
            padding: 20px;
            font-size: 32px;
            text-align: right;
            border: none;
            border-radius: 10px;
            background: #f8f8f8;
            box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.05);
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
        }

        button {
            padding: 18px;
            font-size: 20px;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            transition: all 0.2s ease;
            background: #f0f0f0;
            color: #333;
        }

        button:hover {
            background: #e0e0e0;
            transform: translateY(-2px);
        }

        button:active {
            transform: translateY(0);
        }

        .operator {
            background: #ff9500;
            color: white;
        }

        .operator:hover {
            background: #ff8a00;
        }

        .clear {
            background: #ff3b30;
            color: white;
        }

        .equals {
            background: #34c759;
            color: white;
            grid-column: span 2;
        }

        .zero {
            grid-column: span 2;
        }

        .history {
            font-size: 14px;
            color: #666;
            text-align: right;
            min-height: 20px;
            margin-bottom: 5px;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="history" id="history"></div>
        <input type="text" class="display" readonly id="display">
        <div class="buttons">
            <button class="clear" onclick="clearDisplay()">C</button>
            <button onclick="backspace()">⌫</button>
            <button class="operator" onclick="appendToDisplay('%')">%</button>
            <button class="operator" onclick="appendToDisplay('/')">/</button>
            
            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button class="operator" onclick="appendToDisplay('*')">×</button>
            
            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button class="operator" onclick="appendToDisplay('-')">-</button>
            
            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button class="operator" onclick="appendToDisplay('+')">+</button>
            
            <button class="zero" onclick="appendToDisplay('0')">0</button>
            <button onclick="appendToDisplay('.')">.</button>
            <button class="equals" onclick="calculate()">=</button>
        </div>
    </div>

    <script>
        const display = document.getElementById('display');
        const history = document.getElementById('history');

        function appendToDisplay(value) {
            if (display.value.length < 15) {
                display.value += value;
            }
        }

        function clearDisplay() {
            display.value = '';
            history.textContent = '';
        }

        function backspace() {
            display.value = display.value.slice(0, -1);
        }

        function calculate() {
            try {
                const expression = display.value;
                const result = eval(expression);
                history.textContent = expression + ' =';
                display.value = result.toString().slice(0, 15);
            } catch (error) {
                display.value = 'Error';
                setTimeout(clearDisplay, 1000);
            }
        }

        // Keyboard support
        document.addEventListener('keydown', (e) => {
            if (e.key >= '0' && e.key <= '9' || e.key === '.') appendToDisplay(e.key);
            if (['+', '-', '*', '/', '%'].includes(e.key)) appendToDisplay(e.key);
            if (e.key === 'Enter') calculate();
            if (e.key === 'Backspace') backspace();
            if (e.key === 'Escape') clearDisplay();
        });
    </script>
</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Comfort Calculator</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: #f5f5f5;
        }

        .calculator {
            background: #ffffff;
            padding: 25px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            width: 350px;
        }

        .display {
            width: 100%;
            height: 80px;
            margin-bottom: 20px;
            padding: 20px;
            font-size: 32px;
            text-align: right;
            border: none;
            border-radius: 10px;
            background: #f8f8f8;
            box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.05);
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
        }

        button {
            padding: 18px;
            font-size: 20px;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            transition: all 0.2s ease;
            background: #f0f0f0;
            color: #333;
        }

        button:hover {
            background: #e0e0e0;
            transform: translateY(-2px);
        }

        button:active {
            transform: translateY(0);
        }

        .operator {
            background: #ff9500;
            color: white;
        }

        .operator:hover {
            background: #ff8a00;
        }

        .clear {
            background: #ff3b30;
            color: white;
        }

        .equals {
            background: #34c759;
            color: white;
            grid-column: span 2;
        }

        .zero {
            grid-column: span 2;
        }

        .history {
            font-size: 14px;
            color: #666;
            text-align: right;
            min-height: 20px;
            margin-bottom: 5px;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="history" id="history"></div>
        <input type="text" class="display" readonly id="display">
        <div class="buttons">
            <button class="clear" onclick="clearDisplay()">C</button>
            <button onclick="backspace()">⌫</button>
            <button class="operator" onclick="appendToDisplay('%')">%</button>
            <button class="operator" onclick="appendToDisplay('/')">/</button>
            
            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button class="operator" onclick="appendToDisplay('*')">×</button>
            
            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button class="operator" onclick="appendToDisplay('-')">-</button>
            
            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button class="operator" onclick="appendToDisplay('+')">+</button>
            
            <button class="zero" onclick="appendToDisplay('0')">0</button>
            <button onclick="appendToDisplay('.')">.</button>
            <button class="equals" onclick="calculate()">=</button>
        </div>
    </div>

    <script>
        const display = document.getElementById('display');
        const history = document.getElementById('history');

        function appendToDisplay(value) {
            if (display.value.length < 15) {
                display.value += value;
            }
        }

        function clearDisplay() {
            display.value = '';
            history.textContent = '';
        }

        function backspace() {
            display.value = display.value.slice(0, -1);
        }

        function calculate() {
            try {
                const expression = display.value;
                const result = eval(expression);
                history.textContent = expression + ' =';
                display.value = result.toString().slice(0, 15);
            } catch (error) {
                display.value = 'Error';
                setTimeout(clearDisplay, 1000);
            }
        }

        // Keyboard support
        document.addEventListener('keydown', (e) => {
            if (e.key >= '0' && e.key <= '9' || e.key === '.') appendToDisplay(e.key);
            if (['+', '-', '*', '/', '%'].includes(e.key)) appendToDisplay(e.key);
            if (e.key === 'Enter') calculate();
            if (e.key === 'Backspace') backspace();
            if (e.key === 'Escape') clearDisplay();
        });
    </script>
</body>
</html>
