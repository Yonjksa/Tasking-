<!DOCTYPE html>
<html lang="es">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lista de tareas</title>

<style>

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #f4f7fb, #e9eef7);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

.contenedor {
    width: 100%;
    max-width: 520px;
    background: white;
    border-radius: 18px;
    padding: 28px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.10);
}

h1 {
    margin-top: 0;
    text-align: center;
    color: #1f3b73;
    font-size: 28px;
}

.fila {
    display: flex;
    gap: 10px;
    margin-top: 18px;
}

input {
    flex: 1;
    padding: 12px 14px;
    border: 1px solid #cdd6e5;
    border-radius: 10px;
    outline: none;
    font-size: 15px;
}

input:focus {
    border-color: #1f3b73;
    box-shadow: 0 0 0 3px rgba(31, 59, 115, 0.10);
}

.btn-agregar {
    border: none;
    background: #1f3b73;
    color: white;
    padding: 12px 18px;
    border-radius: 10px;
    cursor: pointer;
    font-weight: bold;
}

.btn-agregar:hover {
    background: #16305f;
}

ul {
    padding: 0;
    margin: 22px 0 0;
}

li {
    list-style: none;
    background: #f7f9fc;
    border: 1px solid #e3e8f2;
    padding: 12px 14px;
    border-radius: 12px;
    margin-bottom: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 12px;
}

.tarea-texto {
    flex: 1;
    word-break: break-word;
}

.acciones {
    display: flex;
    gap: 8px;
}

.btn {
    border: none;
    padding: 8px 10px;
    border-radius: 8px;
    cursor: pointer;
    font-weight: bold;
}

.ok {
    background: #e7f7ec;
    color: #1e7a3f;
}

.eliminar {
    background: #fdeaea;
    color: #b02a2a;
}

.completada .tarea-texto {
    text-decoration: line-through;
    color: #7a7a7a;
}

</style>

</head>

<body>

<div class="contenedor">
    <h1>Lista de tareas</h1>

    <div class="fila">
        <input type="text" id="texto" placeholder="Escribe una tarea">
        <button class="btn-agregar" id="agregar">Agregar</button>
    </div>

    <ul id="lista"></ul>
</div>

<script>
const boton = document.getElementById("agregar");
const texto = document.getElementById("texto");
const lista = document.getElementById("lista");

boton.addEventListener("click", function () {
    const tarea = texto.value.trim();

    if (tarea === "") {
        alert("Escribe una tarea");
        return;
    }

    const nueva = document.createElement("li");
    nueva.innerHTML = `
        <span class="tarea-texto">${tarea}</span>
        <div class="acciones">
            <button class="btn ok">Hecho</button>
            <button class="btn eliminar">Eliminar</button>
        </div>
    `;

    lista.appendChild(nueva);
    texto.value = "";
    texto.focus();

    const btnCompletar = nueva.querySelector(".ok");
    const btnEliminar = nueva.querySelector(".eliminar");

    btnCompletar.addEventListener("click", function () {
        nueva.classList.toggle("completada");
    });

    btnEliminar.addEventListener("click", function () {
        nueva.remove();
    });
});

texto.addEventListener("keydown", function (evento) {
    if (evento.key === "Enter") {
        boton.click();
    }
});
</script>

</body>
</html># Tasking-