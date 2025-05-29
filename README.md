<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Dashboard con GitHub</title>
    <style>
        * {
            box-sizing: border-box;
        }
        body {
            font-family: Arial, Helvetica, sans-serif;
            background-color: rgb(234, 179, 179);
            margin: 0;
            padding: 20px;
            display: flex;
        }
        .sidebar {
            width: 200px;
            background-color: rgb(223, 28, 28);
            color: white;
            height: 100vh;
            padding: 20px;
            position: fixed;
        }
        .sidebar h2 {
            margin-top: 0;
            text-align: center;
        }
        .sidebar ul {
            list-style: none;
            padding: 0;
        }
        .sidebar ul li a {
            display: block;
            padding: 10px;
            margin-bottom: 10px;
            color: white;
            text-decoration: none;
            border-radius: 5px;
        }
        .sidebar ul li a:hover {
            background-color: rgba(0, 0, 0, 0.3);
        }
        .sidebar ul li a.active {
            background-color: rgb(0, 6, 6);
        }

        .main-content {
            margin-left: 220px;
            padding: 0px;
            width: 100%;
        }

        h1 {
            text-align: center;
            color: rgb(0, 0, 0);
        }

        .dashboard {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }

        .card {
            background-color: rgb(254, 254, 254);
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 4px 8px rgb(12, 12, 12);
            text-align: center;
            transition: background-color 0.3s;
        }

        .card h2 {
            margin: 10px 0;
            color: rgb(16, 16, 16);
        }

        .card p {
            font-size: 18px;
            color: rgb(46, 2, 2);
        }

        /* NUEVA CLASE PARA RESALTAR LA TARJETA */
        .card.highlight {
            background-color: #b0b0b0 !important; /* plomo más fuerte */
            color: #222;
        }

        html {
            scroll-behavior: smooth;
        }
    </style>
</head>
<body>
    <div class="sidebar">
        <h2>Menú de Opciones</h2>
        <ul>
            <li><a href="#inicio" class="active" onclick="setActive(this, 'inicio')">Inicio</a></li>
            <li><a href="#trabajadores" onclick="setActive(this, 'trabajadores')">Lista de trabajadores</a></li>
            <li><a href="#cuotas" onclick="setActive(this, 'cuotas')">Cuota mensual por trabajador</a></li>
            <li><a href="#ranking" onclick="setActive(this, 'ranking')">Ranking mensual</a></li>
        </ul>
    </div>

    <div class="main-content">
        <h1 id="inicio">Dashboard - Financiera "EDIFICAR"</h1>
        <div class="dashboard">
            <div class="card" id="trabajadores" >
                <h2>Lista de trabajadores</h2>
                <p>Avalos Alban, Luisa</p>
                <p>Moreno Valdez, Josh</p>
                <p>Romani Ramirez, Ana</p>
                <p>Zenozain Deza, Dafne</p>
            </div>
            <div class="card" id="cuotas">
                <h2>Cuota mensual por trabajador</h2>
                <p>Avalos Alban, Luisa = 20 clientes</p>
                <p>Moreno Valdez, Josh = 20 clientes</p>
                <p>Romani Ramirez, Ana = 20 clientes</p>
                <p>Zenozain Deza, Dafne = 20 clientes</p>
            </div>
            <div class="card" id="ranking">
                <h2>Ranking mensual</h2>
                <p>Avalos Alban, Luisa = 18 clientes</p>
                <p>Moreno Valdez, Josh = 15 clientes</p>
                <p>Romani Ramirez, Ana = 14 clientes</p>
                <p>Zenozain Deza, Dafne = 10 clientes</p>
            </div>
        </div>
    </div>

    <script>
        function setActive(element, sectionId) {
            // Quitar el resaltado del menú
            const links = document.querySelectorAll('.sidebar ul li a');
            links.forEach(link => link.classList.remove('active'));
            element.classList.add('active');

            // Quitar el resaltado de todas las tarjetas
            const cards = document.querySelectorAll('.card');
            cards.forEach(card => card.classList.remove('highlight'));

            // Resaltar la tarjeta correspondiente (si existe)
            if (sectionId && sectionId !== 'inicio') {
                const card = document.getElementById(sectionId);
                if (card) {
                    card.classList.add('highlight');
                }
            }
        }
    </script>
</body>
</html>
