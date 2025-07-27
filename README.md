<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Calculadora Avanzada</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Bungee&family=Goldman&family=Jost&family=Oswald&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(132deg, #000000, #00ff00, #0000ff, #e60073, #ff0000, #ffffff);
      background-size: 400% 400%;
      animation: BackgroundGradient 15s ease infinite;
      font-family: 'Jost', sans-serif;
    }

    @keyframes BackgroundGradient {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    h1, h2, p {
      text-align: center;
      font-family: "Goldman", sans-serif;
    }

    h1 {
      color: red;
      margin-top: 50px;
    }

    h2 {
      color: blueviolet;
    }

    p {
      font-family: "Goldman", sans-serif;
      color: lightgray;
      text-align: center;
      font-size: 1.1em;
    }

    button {
      font-family: "Barlow", sans-serif;
      font-weight: 300;
      background-color: aquamarine;
      color: #333;
      padding: 10px 20px;
      margin: 5px;
      border-radius: 5px;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background-color: #00e6ac;
    }

    .pantalla {
      display: none;
      text-align: center;
      padding: 20px;
    }

    .visible {
      display: block;
    }
  </style>
</head>
<body>

  <div id="pantalla-principal" class="pantalla visible">
    <h1>BIENVENIDOS A LA CALCULADORA AVANZADA</h1>
    <p>Esta es una calculadora que le permitirá realizar conversiones, operaciones y cálculos que vaya a necesitar</p>
    <button onclick="mostrarPantalla('pantalla-operaciones')">Operaciones</button>
    <button onclick="mostrarPantalla('pantalla-conversiones')">Conversiones</button>
    <button onclick="mostrarPantalla('pantalla-calculos')">Cálculos</button>
  </div>

  <!-- Pantalla de Operaciones -->
  <div id="pantalla-operaciones" class="pantalla">
    <h2>Operaciones</h2>
    <button onclick="realizarOperacion('+')">Sumar</button>
    <button onclick="realizarOperacion('-')">Restar</button>
    <button onclick="realizarOperacion('*')">Multiplicar</button>
    <button onclick="realizarOperacion('/')">Dividir</button>
    <button onclick="realizarOperacion('^')">Potencia</button>
    <button onclick="realizarOperacion('√')">Raíz</button>
    <br><br>
    <p id="resultado"></p>
    <br>
    <button onclick="mostrarPantalla('pantalla-principal')">Volver</button>
  </div>

  <!-- Pantalla de Conversiones -->
  <div id="pantalla-conversiones" class="pantalla">
    <h2>Conversiones</h2>
    <button onclick="mostrarSubmenu()">Mostrar menú de conversiones</button>
    <div id="submenu-conversiones" style="display: none; margin-top: 20px;">
      <button onclick="mostrarFormulario('kg')">Kg a gramos</button>
      <button onclick="mostrarFormulario('km')">Km a metros</button>
    </div>

    <div id="form-kg" style="display: none;">
      <p>Ingrese kilogramos:</p>
      <input type="number" id="input-kg">
      <button onclick="convertirKg()">Convertir</button>
    </div>

    <div id="form-km" style="display: none;">
      <p>Ingrese kilómetros:</p>
      <input type="number" id="input-km">
      <button onclick="convertirKm()">Convertir</button>
    </div>

    <p id="resultadoConversion"></p>
    <br>
    <button onclick="mostrarPantalla('pantalla-principal')">Volver</button>
  </div>

  <!-- Pantalla de Cálculos -->
  <div id="pantalla-calculos" class="pantalla">
    <h2>Cálculos</h2>
    <p>Aquí irán los cálculos especiales.</p>
    <button onclick="mostrarPantalla('pantalla-principal')">Volver</button>
  </div>

  <script>
    function mostrarPantalla(id) {
      document.querySelectorAll('.pantalla').forEach(div => {
        div.classList.remove('visible');
      });
      document.getElementById(id).classList.add('visible');
    }

    function realizarOperacion(tipo) {
      let a = parseFloat(prompt("Primer número:"));
      let b, resultado;

      if (tipo !== "√") {
        b = parseFloat(prompt("Segundo número:"));
      }

      switch (tipo) {
        case "+": resultado = a + b; break;
        case "-": resultado = a - b; break;
        case "*": resultado = a * b; break;
        case "/": resultado = b !== 0 ? a / b : "Error: división por cero"; break;
        case "^": resultado = Math.pow(a, b); break;
        case "√": resultado = a >= 0 ? Math.sqrt(a) : "Error: raíz negativa"; break;
        default: resultado = "Operación inválida";
      }

      document.getElementById("resultado").innerText = "Resultado: " + resultado;
    }

    function mostrarSubmenu() {
      document.getElementById("submenu-conversiones").style.display = "block";
    }

    function mostrarFormulario(tipo) {
      document.getElementById("form-kg").style.display = "none";
      document.getElementById("form-km").style.display = "none";

      if (tipo === "kg") {
        document.getElementById("form-kg").style.display = "block";
      } else if (tipo === "km") {
        document.getElementById("form-km").style.display = "block";
      }

      document.getElementById("resultadoConversion").innerText = "";
    }

    function convertirKg() {
      const valor = parseFloat(document.getElementById("input-kg").value);
      if (isNaN(valor)) {
        alert("Por favor, ingrese un número válido.");
        return;
      }
      const gramos = valor * 1000;
      document.getElementById("resultadoConversion").innerText = `${valor} kg = ${gramos} gramos.`;
    }

    function convertirKm() {
      const valor = parseFloat(document.getElementById("input-km").value);
      if (isNaN(valor)) {
        alert("Por favor, ingrese un número válido.");
        return;
      }
      const metros = valor * 1000;
      document.getElementById("resultadoConversion").innerText = `${valor} km = ${metros} metros.`;
    }
  </script>

</body>
</html>
