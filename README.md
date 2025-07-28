<html lang="es">
<head> 
  <meta charset="UTF-8">
  <title>Calculadora Avanzada</title>
  <link href="https://fonts.googleapis.com/css2?family=Bungee&family=Goldman&family=Jost&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(132deg, #000000,#00ff00, #0000ff,#e60073,#ff0000,#ffffff);
      background-size: 400% 400%;
      animation: BackgroundGradient 15s ease infinite;
      font-family: 'Goldman', sans-serif;
    }

    @keyframes BackgroundGradient {
      0% {background-position: 0% 50%;}
      50% {background-position: 100% 50%;}
      100% {background-position: 0% 50%;}
    }

    h1, h2 {
      text-align: center;
      font-family: 'Bungee', sans-serif;
      color: black;
      margin-top: 30px;
    }

    p {
      color: lightgray;
      text-align: center;
      font-size: 1.1em;
    }

    button {
      background-color: aquamarine;
      color: #333;
      padding: 10px 20px;
      margin: 5px;
      border-radius: 5px;
      cursor: pointer;
      transition: 0.3s;
      font-family: 'Jost', sans-serif;
    }

    button:hover {
      background-color: #00e6ac;
    }

    .pantalla {
      display: none;
    }

    .visible {
      display: block;
    }

    .centrado {
      text-align: center;
      margin-top: 30px;
    }

    .bloque {
      margin-top: 15px;
      text-align: center;
    }

  </style>
</head>

<body>

  <!-- Pantalla principal -->
  <div id="pantallaPrincipal" class="visible">
    <h1>BIENVENIDOS A LA CALCULADORA AVANZADA</h1>
    <p>Esta es una calculadora que le permitirá realizar conversiones, operaciones y cálculos que necesite.</p>
    <div class="centrado">
      <button onclick="mostrarPantalla('pantalla-operaciones')">Operaciones</button>
      <button onclick="mostrarPantalla('pantalla-conversiones')">Conversiones</button>
      <button onclick="mostrarPantalla('pantalla-calculos')">Cálculos</button>
    </div>
  </div>

  <!-- Operaciones -->
  <div id="pantalla-operaciones" class="pantalla">
    <h2>Operaciones</h2>
    <div class="centrado">
      <button onclick="realizarOperacion('+')">Sumar</button>
      <button onclick="realizarOperacion('-')">Restar</button>
      <button onclick="realizarOperacion('*')">Multiplicar</button>
      <button onclick="realizarOperacion('/')">Dividir</button>
      <button onclick="realizarOperacion('^')">Potencia</button>
      <button onclick="realizarOperacion('√')">Raíz</button><br><br>
      <button onclick="mostrarPantalla('pantallaPrincipal')">Volver</button>
      <p id="resultado"></p>
    </div>
  </div>

  <!-- Conversiones -->
  <div id="pantalla-conversiones" class="pantalla">
    <h2>Conversiones</h2>
    <div class="centrado">
      <button onclick="mostrarSubmenu()">Mostrar menú de conversiones</button>
      <div id="submenu-conversiones" style="display:none;">
        <button onclick="mostrarFormulario('kg')">Kg a gramos</button>
        <button onclick="mostrarFormulario('km')">Km a metros</button>
      </div>

      <div id="form-kg" class="bloque" style="display:none;">
        <p>Ingrese kilogramos:</p>
        <input type="number" id="input-kg">
        <button onclick="convertirKg()">Convertir</button>
      </div>

      <div id="form-km" class="bloque" style="display:none;">
        <p>Ingrese kilómetros:</p>
        <input type="number" id="input-km">
        <button onclick="convertirKm()">Convertir</button>
      </div>

      <p id="resultadoConversion"></p>
      <button onclick="mostrarPantalla('pantallaPrincipal')">Volver</button>
    </div>
  </div>

  <!-- Cálculos -->
  <div id="pantalla-calculos" class="pantalla">
    <h2>Cálculos</h2>
    <div class="centrado">
      <button onclick="mostrarSubmenuCalculos()">Mostrar menú de cálculos</button>

      <div id="submenu-calculos" style="display:none;">
        <button onclick="mostrarFormularioCalculo('t')">Tiempo</button>
        <button onclick="mostrarFormularioCalculo('d')">Distancia</button>
        <button onclick="mostrarFormularioCalculo('v')">Velocidad</button>
      </div>

      <div id="form-t" class="bloque" style="display:none;">
        <p>Ingrese la distancia (km):</p>
        <input type="number" id="input-distancia-t">
        <p>Ingrese la velocidad (km/h):</p>
        <input type="number" id="input-velocidad-t">
        <button onclick="calcularTiempo()">Calcular Tiempo</button>
      </div>

      <div id="form-d" class="bloque" style="display:none;">
        <p>Ingrese la velocidad (km/h):</p>
        <input type="number" id="input-velocidad-d">
        <p>Ingrese el tiempo (h):</p>
        <input type="number" id="input-tiempo-d">
        <button onclick="calcularDistancia()">Calcular Distancia</button>
      </div>

      <div id="form-v" class="bloque" style="display:none;">
        <p>Ingrese la distancia (km):</p>
        <input type="number" id="input-distancia-v">
        <p>Ingrese el tiempo (h):</p>
        <input type="number" id="input-tiempo-v">
        <button onclick="calcularVelocidad()">Calcular Velocidad</button>
      </div>

      <p id="resultadoCalculo"></p>
      <button onclick="mostrarPantalla('pantallaPrincipal')">Volver</button>
    </div>
  </div>

  <script>
    function mostrarPantalla(id) {
      const pantallas = document.querySelectorAll(".pantalla, #pantallaPrincipal");
      pantallas.forEach(p => p.classList.remove("visible"));
      document.getElementById(id).classList.add("visible");
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
      if (isNaN(valor)) return alert("Ingrese un número válido.");
      document.getElementById("resultadoConversion").innerText = `${valor} kg = ${valor * 1000} gramos.`;
    }

    function convertirKm() {
      const valor = parseFloat(document.getElementById("input-km").value);
      if (isNaN(valor)) return alert("Ingrese un número válido.");
      document.getElementById("resultadoConversion").innerText = `${valor} km = ${valor * 1000} metros.`;
    }

    function mostrarSubmenuCalculos() {
      document.getElementById("submenu-calculos").style.display = "block";
    }

    function mostrarFormularioCalculo(tipo) {
      document.getElementById("form-t").style.display = "none";
      document.getElementById("form-d").style.display = "none";
      document.getElementById("form-v").style.display = "none";
      document.getElementById(`form-${tipo}`).style.display = "block";
      document.getElementById("resultadoCalculo").innerText = "";
    }

    function calcularTiempo() {
      const d = parseFloat(document.getElementById("input-distancia-t").value);
      const v = parseFloat(document.getElementById("input-velocidad-t").value);
      if (isNaN(d) || isNaN(v) || v === 0) return alert("Datos inválidos.");
      document.getElementById("resultadoCalculo").innerText = `El tiempo es ${(d / v).toFixed(2)} horas.`;
    }

    function calcularDistancia() {
      const v = parseFloat(document.getElementById("input-velocidad-d").value);
      const t = parseFloat(document.getElementById("input-tiempo-d").value);
      if (isNaN(v) || isNaN(t)) return alert("Datos inválidos.");
      document.getElementById("resultadoCalculo").innerText = `La distancia es ${(v * t).toFixed(2)} km.`;
    }

    function calcularVelocidad() {
      const d = parseFloat(document.getElementById("input-distancia-v").value);
      const t = parseFloat(document.getElementById("input-tiempo-v").value);
      if (isNaN(d) || isNaN(t) || t === 0) return alert("Datos inválidos.");
      document.getElementById("resultadoCalculo").innerText = `La velocidad es ${(d / t).toFixed(2)} km/h.`;
    }
  </script>

</body>
</html>

