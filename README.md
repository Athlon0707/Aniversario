# Aniversario
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flores para ti 🌻❤️</title>
    <style>
        body {
            /* Fondo rosa degradado */
            background: linear-gradient(180deg, rgba(255,105,180,1) 0%, rgba(255,20,147,1) 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: 'Courier New', Courier, monospace; /* Fuente de estilo código */
            overflow: hidden;
        }

        .contenedor-principal {
            text-align: center;
            color: #4a4a4a;
            position: relative;
            z-index: 2;
        }

        /* Título superior (simulando "ALEX DEV") */
        .cabecera {
            position: absolute;
            top: -50px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 14px;
            font-weight: bold;
            color: rgba(255, 255, 255, 0.7);
        }

        /* Caja de contenido beige */
        .caja-carta {
            background-color: #f6ebd8;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0px 10px 20px rgba(0,0,0,0.2);
            width: 300px;
            height: 400px;
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            align-items: center;
            border: 2px solid white;
        }

        /* Imagen del árbol de girasoles */
        .arbol-girasoles {
            max-width: 100%;
            height: auto;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        /* Estilos del contador de tiempo */
        .contador {
            margin-top: auto;
            font-size: 14px;
            color: #4a4a4a;
        }

        .tiempo-grande {
            display: block;
            font-size: 24px;
            font-weight: bold;
            margin-top: 5px;
        }

        /* Estilo para los corazones de fondo flotantes */
        .corazon {
            color: #ffb6c1; /* Rosa claro */
            position: fixed;
            top: -20px;
            font-size: 1.5rem;
            z-index: 1;
            animation: caer linear infinite;
        }

        @keyframes caer {
            to {
                transform: translateY(105vh);
            }
        }
    </style>
</head>
<body>

    <div id="contenedor-corazones"></div>

    <div class="contenedor-principal">
        <div class="cabecera">NUESTRO AMOR</div>

        <div class="caja-carta">
            <img src="https://i.imgur.com/gallery/iooo-1wTWId5.jpg" alt="Árbol de Girasoles" class="arbol-girasoles">
            
            <p>Flores Amarillas para el amor de mi vida</p>
            <p>🌻❤️</p>

            <div class="contador">
                <p>Mi amor por ti comenzó hace...</p>
                <span class="tiempo-grande" id="reloj"></span>
            </div>
        </div>
    </div>

    <script>
        // --- CONFIGURACIÓN DE TU FECHA DE ANIVERSARIO ---
        // Año, Mes (0=Enero, 11=Diciembre), Día
        const fechaInicio = new Date(2026, 2, 14); // 1 de Noviembre de 2023

        function actualizarContador() {
            const ahora = new Date();
            const diferencia = ahora - fechaInicio;

            if (diferencia < 0) {
                document.getElementById('reloj').innerText = "¡Aún no empezamos!";
                return;
            }

            const dias = Math.floor(diferencia / (1000 * 60 * 60 * 24));
            const horas = Math.floor((diferencia % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutos = Math.floor((diferencia % (1000 * 60 * 60)) / (1000 * 60));
            const segundos = Math.floor((diferencia % (1000 * 60)) / 1000);

            const textoTiempo = `${dias} días ${horas} horas ${minutos} minutos ${segundos} segundos`;
            document.getElementById('reloj').innerText = textoTiempo;
        }

        // Actualizar cada segundo
        setInterval(actualizarContador, 1000);
        actualizarContador(); // Carga inicial

        // --- LÓGICA PARA LOS CORAZONES DE FONDO ---
        function crearCorazon() {
            const corazon = document.createElement('div');
            corazon.innerHTML = '❤️';
            corazon.classList.add('corazon');
            corazon.style.left = Math.random() * 100 + 'vw';
            corazon.style.animationDuration = Math.random() * 3 + 2 + 's'; // Duración entre 2 y 5 segundos
            corazon.style.opacity = Math.random();
            corazon.style.fontSize = Math.random() * 1.5 + 0.5 + 'rem';
            
            document.getElementById('contenedor-corazones').appendChild(corazon);

            setTimeout(() => {
                corazon.remove();
            }, 5000); // Eliminar después de 5 segundos para no saturar
        }

        // Crear corazones continuamente
        setInterval(crearCorazon, 300);
    </script>
</body>
</html>
