<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Acceso CONALEP</title>

<style>
body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.box {
    background: rgba(255,255,255,0.1);
    backdrop-filter: blur(10px);
    padding: 30px;
    border-radius: 20px;
    width: 320px;
    text-align: center;
    color: white;
    box-shadow: 0 10px 30px rgba(0,0,0,0.5);
}

h2 {
    margin-bottom: 10px;
}

input {
    width: 90%;
    padding: 12px;
    margin: 10px 0;
    border-radius: 10px;
    border: none;
    outline: none;
}

button {
    width: 95%;
    padding: 12px;
    border: none;
    border-radius: 25px;
    background: linear-gradient(135deg, #00f2fe, #4facfe);
    font-weight: bold;
    cursor: pointer;
}

#resultado {
    margin-top: 15px;
    font-weight: bold;
}
</style>
</head>

<body>

<div class="box">
    <h2>🔐 Acceso CONALEP</h2>
    <p>Ingresa tu matrícula</p>

    <input type="text" id="matricula" placeholder="Ej: 23012345">

    <button onclick="verificar()">Ingresar</button>

    <div id="resultado"></div>
</div>

<script>
function verificar() {
    let matricula = document.getElementById("matricula").value;

    // Ejemplo de validación
    if (matricula.length >= 8) {
        document.getElementById("resultado").innerText = "✅ Acceso permitido";
    } else {
        document.getElementById("resultado").innerText = "❌ Acceso denegado";
    }
}
</script>

</body>
</html>
