<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Reducción de Matriz 3x4</title>

<style>
    body {
        margin: 0;
        font-family: Arial;
        text-align: center;
        background: black;
        color: white;
        overflow-x: hidden;
    }

    canvas {
        position: fixed;
        top: 0;
        left: 0;
        z-index: -1;
    }

    table {
        margin: 10px auto;
        border-collapse: collapse;
        background: rgba(0,0,0,0.7);
    }

    td {
        border: 1px solid #00ffcc;
        padding: 5px;
    }

    input {
        width: 60px;
        text-align: center;
        background: black;
        color: #00ffcc;
        border: none;
    }

    button {
        padding: 10px;
        margin: 10px;
        background: #00ffcc;
        border: none;
        cursor: pointer;
        font-weight: bold;
    }

    .paso {
        background: rgba(0,0,0,0.8);
        padding: 10px;
        margin: 10px auto;
        width: fit-content;
        border: 1px solid #00ffcc;
    }
</style>
</head>

<body>

<canvas id="matrixCanvas"></canvas>

<h2>Matriz 3x4 (Sistema de ecuaciones)</h2>

<table>
<tbody>
<script>
for (let i = 0; i < 3; i++) {
    document.write("<tr>");
    for (let j = 0; j < 4; j++) {
        document.write(`<td><input type="number" id="c${i}${j}" value="0"></td>`);
    }
    document.write("</tr>");
}
</script>
</tbody>
</table>

<button onclick="resolver()">Resolver</button>

<h3>Pasos:</h3>
<div id="pasos"></div>

<script>
// ================= MATRIX BACKGROUND =================
const canvas = document.getElementById("matrixCanvas");
const ctx = canvas.getContext("2d");

canvas.height = window.innerHeight;
canvas.width = window.innerWidth;

const letras = "0123456789ABCDEF";
const fontSize = 14;
const columnas = canvas.width / fontSize;

const drops = [];
for (let i = 0; i < columnas; i++) {
    drops[i] = 1;
}

function draw() {
    ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    ctx.fillStyle = "#00ffcc";
    ctx.font = fontSize + "px monospace";

    for (let i = 0; i < drops.length; i++) {
        const text = letras[Math.floor(Math.random() * letras.length)];
        ctx.fillText(text, i * fontSize, drops[i] * fontSize);

        if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
            drops[i] = 0;
        }

        drops[i]++;
    }
}

setInterval(draw, 35);

window.addEventListener("resize", () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
});

// ================= MATRIZ =================
function obtenerMatriz() {
    let m = [];
    for (let i = 0; i < 3; i++) {
        m[i] = [];
        for (let j = 0; j < 4; j++) {
            m[i][j] = parseFloat(document.getElementById(`c${i}${j}`).value) || 0;
        }
    }
    return m;
}

function mostrarMatriz(m, titulo) {
    let html = `<div class="paso"><strong>${titulo}</strong><br><table>`;
    for (let i = 0; i < 3; i++) {
        html += "<tr>";
        for (let j = 0; j < 4; j++) {
            html += `<td>${m[i][j].toFixed(2)}</td>`;
        }
        html += "</tr>";
    }
    html += "</table></div>";
    document.getElementById("pasos").innerHTML += html;
}

function resolver() {
    let m = obtenerMatriz();
    document.getElementById("pasos").innerHTML = "";

    mostrarMatriz(m, "Matriz inicial");

    let pivote = m[0][0];
    for (let j = 0; j < 4; j++) m[0][j] /= pivote;
    mostrarMatriz(m, "R1");

    for (let i = 1; i < 3; i++) {
        let factor = m[i][0];
        for (let j = 0; j < 4; j++) {
            m[i][j] -= factor * m[0][j];
        }
    }
    mostrarMatriz(m, "Ceros en columna 1");

    pivote = m[1][1];
    for (let j = 0; j < 4; j++) m[1][j] /= pivote;
    mostrarMatriz(m, "R2");

    for (let i = 0; i < 3; i++) {
        if (i !== 1) {
            let factor = m[i][1];
            for (let j = 0; j < 4; j++) {
                m[i][j] -= factor * m[1][j];
            }
        }
    }
    mostrarMatriz(m, "Columna 2 limpia");

    pivote = m[2][2];
    for (let j = 0; j < 4; j++) m[2][j] /= pivote;
    mostrarMatriz(m, "R3");

    for (let i = 0; i < 3; i++) {
        if (i !== 2) {
            let factor = m[i][2];
            for (let j = 0; j < 4; j++) {
                m[i][j] -= factor * m[2][j];
            }
        }
    }
    mostrarMatriz(m, "Resultado final");

    let a = m[0][3];
    let b = m[1][3];
    let c = m[2][3];

    document.getElementById("pasos").innerHTML += `
        <div class="paso">
            <strong>Solución:</strong><br>
            a = ${a.toFixed(2)}<br>
            b = ${b.toFixed(2)}<br>
            c = ${c.toFixed(2)}
        </div>
    `;
}
</script>

</body>
</html>