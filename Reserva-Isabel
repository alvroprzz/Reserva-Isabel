<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Reserva con Isabel</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      background-color: #f3f4f6;
      color: #333;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 20px;
      margin: 0;
    }
    .container {
      width: 100%;
      max-width: 1200px;
      background: white;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      padding: 20px;
    }
    h1 {
      text-align: center;
      color: #4CAF50;
    }
    .month-container {
      margin-top: 20px;
      margin-bottom: 40px;
    }
    .month {
      text-align: center;
      background-color: #4CAF50;
      color: white;
      padding: 10px;
      font-size: 1.5em;
      border-radius: 5px;
      margin-bottom: 10px;
    }
    .calendar {
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      grid-gap: 10px;
      margin-top: 20px;
    }
    .day {
      padding: 10px;
      text-align: center;
      background-color: #e0e0e0;
      cursor: pointer;
      border-radius: 5px;
    }
    .day:hover {
      background-color: #ccc;
    }
    .reserved {
      background-color: #FFEB3B;
    }
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      justify-content: center;
      align-items: center;
    }
    .modal-content {
      background: white;
      padding: 20px;
      border-radius: 10px;
      width: 300px;
      text-align: center;
    }
    .modal input, .modal button, .modal textarea {
      margin-top: 10px;
      padding: 10px;
      width: 100%;
    }
  </style>
</head>
<body>

<div class="container">
  <h1>Reserva tu día con Isabel</h1>

  <!-- Aquí se generarán los calendarios de abril a diciembre -->
  <div id="calendars"></div>
</div>

<div id="modal" class="modal">
  <div class="modal-content">
    <h2>Reserva tu día</h2>
    <input type="text" id="name" placeholder="Tu nombre">
    <textarea id="message" placeholder="Escribe algo para Isabel..."></textarea>
    <button onclick="reserveDay()">Reservar</button>
  </div>
</div>

<script>
  // Datos iniciales
  const months = [
    "Abril", "Mayo", "Junio", "Julio", "Agosto", "Septiembre", 
    "Octubre", "Noviembre", "Diciembre"
  ];

  let reservedDays = {};  // Para almacenar las reservas de los días

  // Crear el calendario para cada mes
  function createCalendar() {
    const today = new Date();
    const currentYear = today.getFullYear();
    const calendarsContainer = document.getElementById("calendars");

    // Limpiar contenedor
    calendarsContainer.innerHTML = '';

    months.forEach((monthName, monthIndex) => {
      const firstDay = new Date(currentYear, monthIndex, 1);
      const lastDay = new Date(currentYear, monthIndex + 1, 0);
      const monthContainer = document.createElement('div');
      monthContainer.classList.add('month-container');

      // Título del mes
      const monthTitle = document.createElement('div');
      monthTitle.classList.add('month');
      monthTitle.innerText = monthName;
      monthContainer.appendChild(monthTitle);

      // Crear calendario para el mes
      const calendarDiv = document.createElement('div');
      calendarDiv.classList.add('calendar');

      // Generar los días del mes
      for (let i = 1; i <= lastDay.getDate(); i++) {
        const dayDiv = document.createElement('div');
        dayDiv.classList.add('day');
        dayDiv.innerText = i;

        // Comprobar si el día está reservado
        const dateString = `${currentYear}-${monthIndex + 1}-${i}`;
        if (reservedDays[dateString]) {
          dayDiv.classList.add('reserved');
        }

        // Añadir el evento de clic para reservar el día
        dayDiv.onclick = () => openModal(dateString);

        calendarDiv.appendChild(dayDiv);
      }

      monthContainer.appendChild(calendarDiv);
      calendarsContainer.appendChild(monthContainer);
    });
  }

  // Mostrar el modal para hacer la reserva
  function openModal(dateString) {
    const modal = document.getElementById("modal");
    modal.style.display = "flex";
    window.selectedDate = dateString;
  }

  // Reservar el día
  function reserveDay() {
    const name = document.getElementById("name").value;
    const message = document.getElementById("message").value;

    if (name && message) {
      reservedDays[selectedDate] = { name, message };

      // Actualizar la interfaz
      createCalendar();
      
      // Cerrar el modal
      const modal = document.getElementById("modal");
      modal.style.display = "none";
    } else {
      alert("Por favor, ingresa tu nombre y un mensaje.");
    }
  }

  // Inicializar los calendarios
  createCalendar();
</script>

</body>
</html>
