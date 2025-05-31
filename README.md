<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Verificador de Ecuaciones de Primer Grado</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin-top: 50px;
    }
    input, button {
      font-size: 1rem;
      padding: 10px;
      margin: 10px;
    }
  </style>
</head>
<body>
  <h1>Ecuación de Primer Grado</h1>
  <p id="ecuacion"></p>
  <input type="number" id="respuesta" placeholder="Tu respuesta">
  <button onclick="verificarRespuesta()">Verificar</button>
  <p id="resultado"></p>
  <button onclick="generarEcuacion()">Nueva Ecuación</button>

  <script>
    let solucion;

    function generarEcuacion() {
      const a = Math.floor(Math.random() * 9) + 1; // a entre 1 y 9
      const x = Math.floor(Math.random() * 20) - 10; // x entre -10 y 9
      const b = Math.floor(Math.random() * 21) - 10; // b entre -10 y 10
      const c = a * x + b;

      solucion = x;
      document.getElementById("ecuacion").textContent = `${a}x + ${b} = ${c}`;
      document.getElementById("resultado").textContent = "";
      document.getElementById("respuesta").value = "";
    }

    function verificarRespuesta() {
      const respuesta = parseFloat(document.getElementById("respuesta").value);
      const resultado = document.getElementById("resultado");

      if (respuesta === solucion) {
        resultado.textContent = "¡Correcto! 🎉";
        resultado.style.color = "green";
      } else {
        resultado.textContent = `Incorrecto. La respuesta correcta era ${solucion}.`;
        resultado.style.color = "red";
      }
    }

    // Generar la primera ecuación al cargar la página
    window.onload = generarEcuacion;
  </script>
</body>
</html>
