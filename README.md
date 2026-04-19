[index.html.txt](https://github.com/user-attachments/files/26870231/index.html.txt)
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formación Ciclo Combinado</title>
    <style>
        /* CSS para que se vea moderno */
        body { font-family: sans-serif; background: #f4f7f6; display: flex; justify-content: center; padding: 20px; }
        .card { background: white; padding: 2rem; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); max-width: 500px; width: 100%; }
        h2 { color: #2c3e50; font-size: 1.2rem; }
        .opcion { 
            display: block; width: 100%; padding: 10px; margin: 10px 0; 
            border: 1px solid #ddd; border-radius: 6px; cursor: pointer; text-align: left; background: #fff;
        }
        .opcion:hover { background: #e9ecef; }
        .btn-verificar { 
            background: #27ae60; color: white; border: none; padding: 10px 20px; 
            border-radius: 6px; cursor: pointer; width: 100%; font-weight: bold; margin-top: 10px;
        }
        .resultado { margin-top: 15px; font-weight: bold; text-align: center; }
        .correcto { color: #27ae60; }
        .incorrecto { color: #e74c3c; }
    </style>
</head>
<body>

<div class="card" id="quiz-container">
    <div id="pregunta-seccion">
        <h2 id="pregunta-texto">Cargando pregunta...</h2>
        <div id="opciones-contenedor"></div>
        <button class="btn-verificar" onclick="verificarRespuesta()">Verificar Respuesta</button>
        <div id="mensaje" class="resultado"></div>
    </div>
</div>

<script>
    // Datos de ejemplo (Esto podrías ampliarlo luego)
    const datosExamen = {
        pregunta: "¿Qué componente realiza el intercambio de calor entre los gases de escape y el agua del ciclo agua-vapor?",
        opciones: [
            "Condensador",
            "Caldera de Recuperación (HRSG)",
            "Turbina de Gas",
            "Compresor"
        ],
        correcta: 1 // La segunda opción (empezando de 0)
    };

    let opcionSeleccionada = null;

    // Función para mostrar la pregunta
    function cargarPregunta() {
        document.getElementById('pregunta-texto').innerText = datosExamen.pregunta;
        const contenedor = document.getElementById('opciones-contenedor');
        
        datosExamen.opciones.forEach((opcion, index) => {
            const boton = document.createElement('button');
            boton.innerText = opcion;
            boton.className = 'opcion';
            boton.onclick = () => seleccionar(index, boton);
            contenedor.appendChild(boton);
        });
    }

    function seleccionar(index, elemento) {
        // Limpiar selecciones previas
        document.querySelectorAll('.opcion').forEach(el => el.style.borderColor = '#ddd');
        // Marcar la nueva
        elemento.style.borderColor = '#27ae60';
        opcionSeleccionada = index;
    }

    function verificarRespuesta() {
        const mensaje = document.getElementById('mensaje');
        if (opcionSeleccionada === null) {
            mensaje.innerText = "Por favor, elige una opción";
            return;
        }

        if (opcionSeleccionada === datosExamen.correcta) {
            mensaje.innerText = "¡Correcto! Excelente operador.";
            mensaje.className = "resultado correcto";
        } else {
            mensaje.innerText = "Incorrecto. Repasa el módulo de Termodinámica.";
            mensaje.className = "resultado incorrecto";
        }
    }

    // Iniciar
    cargarPregunta();
</script>

</body>
</html>
