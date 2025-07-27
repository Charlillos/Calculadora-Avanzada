<html lang="es">
    <head> 
        <meta charset="UTF-8">
        <title> Calculadora Avanzada </title>
        <style>
          
    .pantalla {
      
  border: none !important;
  outline: none !important;
  margin: 0;
  padding: 0;
  box-shadow: none;
    }
    .pantalla {
  display: none;
}

.pantalla.activa {
  display: block;
}
  </style>
    </head>
    <style>
   

    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(132deg, #000000,#00ff00, #0000ff,#e60073,#ff0000,#ffffff);
      background-size: 400% 400%;
      animation: BackgroundGradient 15s ease infinite;
      font-family: 'Jost', sans-serif;
    }

    @keyframes BackgroundGradient {
      0% {background-position: 0% 50%;}
      50% {background-position: 100% 50%;}
      100% {background-position: 0% 50%;}
    }

    h1 {
      font-family: "Bungee", sans-serif;
      font-weight: 800;
      color: red;
      text-align: center;
      margin-top: 50px;
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


    .centrado {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-top: 30px;
    }

    .pantalla {
      display: none;
    }

</style>

    <body> 
        <link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Bitcount+Prop+Double:wght@100..900&family=Bungee&family=Jost:ital,wght@0,100..900;1,100..900&family=Oswald:wght@200..700&family=Playwrite+AU+QLD:wght@100..400&display=swap" rel="stylesheet">




        </style>
<div id="pantallaPrincipal" class="visible"></div>
    <center>  <h1> BIENVENIDOS A LA CALCULADORA AVANZADA </h1> </center>
    <p> Esta es una calculadora que le permitira realizar conversiones, operaciones y calculos que vaya a necesitar </p>
    <center> 
    <button onclick="mostrarPantalla('pantalla-operaciones')">Operaciones</button>
    <button onclick="mostrarPantalla('pantalla-conversiones')">Conversiones</button>
    <button onclick="mostrarPantalla('pantalla-calculos')">Cálculos</button>
  </div>

  <!-- Pantalla de Operaciones -->
   <link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Bitcount+Prop+Double:wght@100..900&family=Bungee&family=Jost:ital,wght@0,100..900;1,100..900&family=Oswald:wght@200..700&family=Playwrite+AU+QLD:wght@100..400&display=swap" rel="stylesheet">

  <div id="pantalla-operaciones" class="pantalla">
    <style> 
    h2 {
font-family: "Goldman", sans-serif;
  font-weight: 700;
  font-style: normal;
  color: blueviolet;
   
  
    <h2>Operaciones</h2>
    <button onclick="realizarOperacion('+')">Sumar</button>
    <button onclick="realizarOperacion('-')">Restar</button>
    <button onclick="realizarOperacion('*')">Multiplicar</button>
    <button onclick="realizarOperacion('/')">Dividir</button>
    <button onclick="realizarOperacion('^')">Potencia</button>
    <button onclick="realizarOperacion('√')">Raíz</button>
    <br><br>
    <button onclick="mostrarPantalla('pantalla-principal')">Volver</button>
    <p id="resultado"></p>
  </div>

  <!-- Pantalla de Conversiones -->
  <div id="pantalla-conversiones" class="pantalla">
    <h2>Conversiones</h2>
    <p>Aquí van las opciones para convertir.</p>
    <button onclick="mostrarSubmenu()">Mostrar menú de conversiones</button>
    <div id="submenu-conversiones" style="display:none; margin-top: 20px;">
      <button onclick="mostrarFormulario('kg')">Kg a gramos</button>
      <button onclick="mostrarFormulario('km')">Km a metros</button>
    </div>

    <!-- Formularios de conversión -->
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
    <br>
    <button onclick="mostrarPantalla('pantalla-principal')">Volver</button>
  </div>

  <script>
    function mostrarPantalla(id) {
      document.querySelectorAll('div').forEach(div => {
        div.classList.remove('visible');
        div.classList.add('pantalla');
      });
      document.getElementById(id).classList.add('visible');
    }

    function mostrarSubmenu() {
      document.getElementById('submenu-conversiones').style.display = 'block';
    }

    function mostrarFormulario(tipo) {
      document.getElementById('form-kg').style.display = 'none';
      document.getElementById('form-km').style.display = 'none';

      if (tipo === 'kg') {
        document.getElementById('form-kg').style.display = 'block';
      } else if (tipo === 'km') {
        document.getElementById('form-km').style.display = 'block';
      }

      document.getElementById('resultado').innerText = '';
    }

    function convertirKg() {
      const valor = parseFloat(document.getElementById('input-kg').value);
      if (isNaN(valor)) {
        alert("Por favor, ingrese un número válido.");
        return;
      }
      const gramos = valor * 1000;
      document.getElementById('resultadoConversion').innerText = `${valor} kg = ${gramos} gramos.`;

    }

    function convertirKm() {
      const valor = parseFloat(document.getElementById('input-km').value);
      if (isNaN(valor)) {
        alert("Por favor, ingrese un número válido.");
        return;
      }
      const metros = valor * 1000;
      document.getElementById('resultadoConversion').innerText = `${valor} km = ${metros} metros.`;

    }
  </script>

 


  <div id="pantalla-calculos" class="pantalla">
    <h2>Cálculos</h2>
    <p>Aquí irán los cálculos especiales.</p>
    <button onclick="mostrarPantalla('pantalla-principal')">Volver</button>
  

  <script>
    function mostrarPantalla(id) {
      const pantallas = document.querySelectorAll("div");
      pantallas.forEach(p => {
        p.classList.remove("visible");
        p.classList.add("pantalla");
      });
      document.getElementById(id).classList.remove("pantalla");
      document.getElementById(id).classList.add("visible");
    }

    function realizarOperacion(tipo) {
      let a = parseFloat(prompt("Primer número:"));
      let b, resultado;

      if (tipo !== "√") {
        b = parseFloat(prompt("Segundo número:"));
      }

      switch(tipo) {
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
