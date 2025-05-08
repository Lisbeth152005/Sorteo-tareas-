<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Sorteo de Tareas del Proyecto</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 30px;
      background-color: #f2f2f2;
    }

    h1 {
      color: #333;
    }

    #resultado {
      font-size: 1.5em;
      margin-top: 20px;
      color: #006600;
    }

    button {
      padding: 10px 20px;
      font-size: 1em;
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 8px;
      margin-top: 20px;
    }

    button:hover {
      background-color: #45a049;
    }

    ul {
      text-align: left;
      display: inline-block;
      margin-top: 20px;
    }

    #asignaciones {
      margin-top: 30px;
      text-align: center;
    }
  </style>
</head>
<body>

  <h1>Sorteo de Tareas del Proyecto</h1>
  <p>Haz clic para asignar una tarea a cada participante.</p>

  <button onclick="asignarTarea()">Sortear tarea</button>

  <div id="resultado"></div>

  <h3>Tareas restantes:</h3>
  <ul id="listaTareas"></ul>

  <div id="asignaciones">
    <h3>Asignaciones realizadas:</h3>
    <ul id="listaAsignaciones"></ul>
  </div>

  <script>
    const participantes = ["Ginger", "Scarlet", "Bhritany", "Ilvania", "María José", "Tamy", "0991767769"];
    const tareas = [
      "Introducción, Objetivos, Marco teórico y Desarrollo",
      "7 ejercicios de suma",
      "3 ejercicios de suma y 5 de resta",
      "5 de resta y 4 ejercicios con multiplicación",
      "6 ejercicios de multiplicación y 3 de ecuación matricial",
      "8 ejercicios de ecuación matricial y 1 de determinar los valores",
      "9 ejercicios de determinar los valores"
    ];

    let indiceParticipante = 0;

    function actualizarLista() {
      const ul = document.getElementById("listaTareas");
      ul.innerHTML = "";
      tareas.forEach((tarea, index) => {
        const li = document.createElement("li");
        li.textContent = `${index + 1}) ${tarea}`;
        ul.appendChild(li);
      });
    }

    function asignarTarea() {
      if (tareas.length === 0 || indiceParticipante >= participantes.length) {
        document.getElementById("resultado").textContent = "¡Ya se asignaron todas las tareas!";
        return;
      }

      const indiceTarea = Math.floor(Math.random() * tareas.length);
      const tareaSeleccionada = tareas.splice(indiceTarea, 1)[0];
      const participante = participantes[indiceParticipante++];

      document.getElementById("resultado").textContent =
        `${participante} debe hacer: ${tareaSeleccionada}`;

      const lista = document.getElementById("listaAsignaciones");
      const li = document.createElement("li");
      li.textContent = `${participante} → ${tareaSeleccionada}`;
      lista.appendChild(li);

      actualizarLista();
    }

    actualizarLista();
  </script>
</body>
</html>
