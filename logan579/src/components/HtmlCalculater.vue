<template>

    <div class="calculator">
        <input type="text" id="display" class="calculator-display" disabled>
        <div class="calculator-keys"> <h3>my calculator</h3>
            <button class="key" onclick="appendNumber('7')">7</button>
            <button class="key" onclick="appendNumber('8')">8</button>
            <button class="key" onclick="appendNumber('9')">9</button>
            <button class="key operator" onclick="setOperation('/')">/</button>

            <button class="key" onclick="appendNumber('4')">4</button>
            <button class="key" onclick="appendNumber('5')">5</button>
            <button class="key" onclick="appendNumber('6')">6</button>
            <button class="key operator" onclick="setOperation('*')">*</button>

            <button class="key" onclick="appendNumber('1')">1</button>
            <button class="key" onclick="appendNumber('2')">2</button>
            <button class="key" onclick="appendNumber('3')">3</button>
            <button class="key operator" onclick="setOperation('-')">-</button>

            <button class="key" onclick="appendNumber('0')">0</button>
            <button class="key" onclick="appendNumber('.')">.</button>
            <button class="key" onclick="calculate()">=</button>
            <button class="key operator" onclick="setOperation('+')">+</button>

            <button class="key clear" onclick="clearDisplay()">C</button>
        </div>
    </div>
    <!--<script src="script.js"></script>-->
   <script>
export default {
    name: 'HtmlCalculater'
}

    let display = document.getElementById('display');
let currentInput = '';
let operator = '';
let previousInput = '';

function appendNumber(number) {
    currentInput += number;
    display.value = currentInput;
}

function setOperation(op) {
    if (currentInput === '') return;
    if (previousInput !== '') {
        calculate();
    }
    operator = op;
    previousInput = currentInput;
    currentInput = '';
}

function calculate() {
    if (currentInput === '' || previousInput === '') return;
    let result;
    const prev = parseFloat(previousInput);
    const current = parseFloat(currentInput);

    switch (operator) {
        case '+':
            result = prev + current;
            break;
        case '-':
            result = prev - current;
            break;
        case '*':
            result = prev * current;
            break;
        case '/':
            result = prev / current;
            break;
        default:
            return;
    }

    currentInput = result;
    operator = '';
    previousInput = '';
    display.value = result;
}

function clearDisplay() {
    currentInput = '';
    previousInput = '';
    operator = '';
    display.value = '';
}
   </script> 
   <style>
    body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f0f0f0;
    margin: 0;
    font-family: Arial, sans-serif;
}

.calculator {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.calculator-display {
    width: 100%;
    height: 40px;
    margin-bottom: 10px;
    text-align: right;
    padding: 10px;
    font-size: 1.5em;
    border: 1px solid #ccc;
    border-radius: 5px;
}

.calculator-keys {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}

.key {
    padding: 20px;
    font-size: 1.2em;
    border: none;
    background-color: #e0e0e0;
    border-radius: 5px;
    cursor: pointer;
}

.key.operator {
    background-color: #ff9500;
    color: white;
}

.key.clear {
    grid-column: span 4;
    background-color: #ff3b30;
    color: white;
}

.key:active {
    background-color: #ccc;
}

.key.operator:active {
    background-color: #e08900;
}

.key.clear:active {
    background-color: #e03232;
}
   </style>
</template>