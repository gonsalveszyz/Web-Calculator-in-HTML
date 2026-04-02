<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Calculadora Web</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, Helvetica, sans-serif;
    }

    body {
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: white;
      padding: 24px;
    }

    .calculadora {
      width: 380px;
      background: linear-gradient(180deg, #d9ddd2 0%, #bfc5b8 100%);
      border: 3px solid #7e8579;
      border-radius: 14px;
      padding: 18px;
      box-shadow:
        0 10px 18px rgba(0, 0, 0, 0.2),
        inset 0 2px 0 rgba(255, 255, 255, 0.45),
        inset 0 -2px 0 rgba(0, 0, 0, 0.08);
    }

    .marca {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 10px;
      color: #2f3a2f;
    }

    .marca h1 {
      font-size: 1.15rem;
      letter-spacing: 1px;
      font-weight: 700;
    }

    .modelo {
      font-size: 0.72rem;
      color: #4f5a4f;
      margin-top: 2px;
    }

    .painel-solar {
      width: 110px;
      height: 28px;
      border-radius: 4px;
      background: linear-gradient(90deg, #39433a, #1d231e);
      border: 2px solid #6d7469;
      box-shadow: inset 0 2px 4px rgba(255,255,255,0.08);
    }

    .display-area {
      background: #9faa93;
      border: 3px solid #737c6e;
      border-radius: 8px;
      padding: 10px;
      margin-bottom: 16px;
      box-shadow: inset 0 2px 6px rgba(0,0,0,0.18);
    }

    .display-label {
      font-size: 0.7rem;
      color: #334033;
      margin-bottom: 6px;
      text-transform: uppercase;
      letter-spacing: 0.8px;
    }

    .display {
      width: 100%;
      height: 62px;
      border: none;
      outline: none;
      border-radius: 4px;
      padding: 10px;
      font-size: 2rem;
      text-align: right;
      background: #c7d1be;
      color: #1f2a1f;
      font-family: 'Courier New', monospace;
      box-shadow: inset 0 1px 3px rgba(0,0,0,0.15);
    }

    .botoes {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }

    button {
      height: 54px;
      border: 1px solid #5d645d;
      border-radius: 8px;
      font-size: 1.05rem;
      font-weight: 700;
      cursor: pointer;
      color: #1f241f;
      background: linear-gradient(180deg, #f1f2ed 0%, #cfd3ca 100%);
      box-shadow:
        0 3px 0 #7c827a,
        inset 0 1px 0 rgba(255,255,255,0.8);
      transition: transform 0.08s ease, box-shadow 0.08s ease;
    }

    button:hover {
      filter: brightness(0.98);
    }

    button:active {
      transform: translateY(2px);
      box-shadow:
        0 1px 0 #7c827a,
        inset 0 1px 0 rgba(255,255,255,0.5);
    }

    .numero {
      background: linear-gradient(180deg, #f5f5f1 0%, #d8dbd2 100%);
    }

    .operador {
      background: linear-gradient(180deg, #8796a8 0%, #69778a 100%);
      color: white;
      border-color: #566172;
      box-shadow:
        0 3px 0 #4d5868,
        inset 0 1px 0 rgba(255,255,255,0.35);
    }

    .acao {
      background: linear-gradient(180deg, #c88282 0%, #a95e5e 100%);
      color: white;
      border-color: #8f4d4d;
      box-shadow:
        0 3px 0 #7b4242,
        inset 0 1px 0 rgba(255,255,255,0.35);
    }

    .igual {
      background: linear-gradient(180deg, #5f738b 0%, #48596b 100%);
      color: white;
      grid-column: span 2;
      border-color: #3f4d5d;
      box-shadow:
        0 3px 0 #374452,
        inset 0 1px 0 rgba(255,255,255,0.3);
    }

    .zero {
      grid-column: span 2;
    }
  </style>
</head>
<body>
  <div class="calculadora">
    <div class="marca">
      <div>
        <h1>Calculator</h1>
        <div class="modelo">fx-web 120B</div>
      </div>
      <div class="painel-solar"></div>
    </div>

    <div class="display-area">
      <div class="display-label">calculadora eletrônica</div>
    <input type="text" class="display" id="display" disabled />
    </div>

    <div class="botoes">
      <button class="acao" onclick="limparDisplay()">C</button>
      <button class="acao" onclick="apagarUltimo()">⌫</button>
      <button class="operador" onclick="adicionarValor('%')">%</button>
      <button class="operador" onclick="adicionarValor('/')">÷</button>

      <button class="numero" onclick="adicionarValor('7')">7</button>
      <button class="numero" onclick="adicionarValor('8')">8</button>
      <button class="numero" onclick="adicionarValor('9')">9</button>
      <button class="operador" onclick="adicionarValor('*')">×</button>

      <button class="numero" onclick="adicionarValor('4')">4</button>
      <button class="numero" onclick="adicionarValor('5')">5</button>
      <button class="numero" onclick="adicionarValor('6')">6</button>
      <button class="operador" onclick="adicionarValor('-')">−</button>

      <button class="numero" onclick="adicionarValor('1')">1</button>
      <button class="numero" onclick="adicionarValor('2')">2</button>
      <button class="numero" onclick="adicionarValor('3')">3</button>
      <button class="operador" onclick="adicionarValor('+')">+</button>

      <button class="numero zero" onclick="adicionarValor('0')">0</button>
      <button class="numero" onclick="adicionarValor('.')">.</button>
      <button class="igual" onclick="calcular()">=</button>
    </div>
  </div>

  <script>
    const display = document.getElementById('display');

    function adicionarValor(valor) {
      display.value += valor;
    }

    function limparDisplay() {
      display.value = '';
    }

    function apagarUltimo() {
      display.value = display.value.slice(0, -1);
    }

    function calcular() {
      try {
        if (display.value === '') return;
        display.value = eval(display.value);
      } catch (erro) {
        display.value = 'Erro';
      }
    }

    document.addEventListener('keydown', function(evento) {
      const tecla = evento.key;

      if ((tecla >= '0' && tecla <= '9') || ['+', '-', '*', '/', '.', '%'].includes(tecla)) {
        adicionarValor(tecla);
      } else if (tecla === 'Enter') {
        calcular();
      } else if (tecla === 'Backspace') {
        apagarUltimo();
      } else if (tecla === 'Escape') {
        limparDisplay();
      }
    });
  </script>
</body>
</html>
