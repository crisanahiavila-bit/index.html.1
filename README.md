<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Control de Acceso por Matrícula</title>

<script src="https://unpkg.com/html5-qrcode"></script>

<style>
body {
    font-family: Arial;
    text-align: center;
    background: #f4f6f8;
}

input {
    padding: 10px;
    font-size: 16px;
    margin-top: 10px;
}

button {
    padding: 10px;
    margin: 5px;
    font-size: 16px;
}

#reader {
    width: 300px;
    margin: auto;
}

#resultado {
    margin-top: 20px;
    font-size: 20px;
    font-weight: bold;
}

.ok { color: green; }
.error { color: red; }

#registro {
    margin-top: 20px;
    font-size: 14px;
}
</style>
</head>

<body>

<h2>Control de Acceso (Matrícula)</h2>

<input type="text" id="matricula" placeholder="Ingresa matrícula">
<br>

<button onclick="verificar()">Verificar</button>
<button onclick="iniciarEscaner()">Escanear</button>

<div id="reader"></div>

<div id="resultado">Esperando...</div>

<div id="registro"></div>

<script>

// 📚 Base de datos simulada
const baseDatos = [
    { matricula: "2023001", nombre: "Juan Pérez" },
    { matricula: "2023002", nombre: "Ana López" },
    { matricula: "2023003", nombre: "Luis García" }
];

// 📝 Registro de accesos
let historial = [];

// 🔍 Verificar acceso
function verificar(codigo) {
    let matricula = codigo || document.getElementById("matricula").value;
    const alumno = baseDatos.find(a => a.matricula === matricula);

    const resultado = document.getElementById("resultado");

    let mensaje = "";
    let estado = "";

    if (alumno) {
        mensaje = `✅ Acceso permitido: ${alumno.nombre}`;
        estado = "ok";
    } else {
        mensaje = "❌ Acceso denegado";
        estado = "error";
    }

    resultado.innerHTML = mensaje;
    resultado.className = estado;

    // Guardar registro
    let fecha = new Date().toLocaleString();
    historial.push(`${fecha} - ${matricula} - ${mensaje}`);

    mostrarRegistro();
}

// 📋 Mostrar historial
function mostrarRegistro() {
    document.getElementById("registro").innerHTML =
        "<b>Historial:</b><br>" + historial.join("<br>");
}

// 📷 Escáner
let scanner;

function iniciarEscaner() {
    scanner = new Html5QrcodeScanner("reader", {
        fps: 10,
        qrbox: 250
    });

    scanner.render((texto) => {
        verificar(texto);
        scanner.clear();
    });
}

</script>

</body>
</html>
