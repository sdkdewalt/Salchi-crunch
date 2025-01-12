<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pedido a WhatsApp</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            text-align: center;
        }
        .form-group {
            margin-bottom: 15px;
        }
        button {
            background-color: #25D366;
            color: white;
            border: none;
            padding: 10px 20px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: #1B954A;
        }
        .mensaje-confirmacion {
            margin-top: 20px;
            font-size: 18px;
            color: #25D366;
            font-weight: bold;
        }
        img.logo {
            max-width: 150px;
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <!-- Logo del negocio -->
    <img src="logo.png" alt="Logo del negocio" class="logo">

    <h1>Haz tu pedido</h1>
    <div class="form-group">
        <label for="producto">Producto:</label>
        <select id="producto" onchange="actualizarTotal()">
            <option value="Hamburguesa" data-precio="15000">Hamburguesa - $15,000</option>
            <option value="Salchipapas" data-precio="12000">Salchipapas - $12,000</option>
            <option value="Perro Caliente" data-precio="10000">Perro Caliente - $10,000</option>
        </select>
    </div>
    <div class="form-group" id="ingredientes">
        <label>Ingredientes adicionales:</label><br>
        <input type="checkbox" value="Queso" data-precio="2000" onchange="actualizarTotal()"> Queso (+$2,000)<br>
        <input type="checkbox" value="Tocineta" data-precio="3000" onchange="actualizarTotal()"> Tocineta (+$3,000)<br>
        <input type="checkbox" value="Huevo" data-precio="1500" onchange="actualizarTotal()"> Huevo (+$1,500)
    </div>
    <div class="form-group" id="salsas">
        <label>Salsas:</label><br>
        <input type="checkbox" value="Mayonesa" data-precio="500" onchange="actualizarTotal()"> Mayonesa (+$500)<br>
        <input type="checkbox" value="Salsa de tomate" data-precio="500" onchange="actualizarTotal()"> Salsa de tomate (+$500)<br>
        <input type="checkbox" value="Mostaza" data-precio="500" onchange="actualizarTotal()"> Mostaza (+$500)
    </div>
    <h3>Total: $<span id="total">0</span></h3>
    <button onclick="enviarPedido()">Hacer Pedido</button>

    <p id="mensaje-confirmacion" class="mensaje-confirmacion" style="display: none;">¡Gracias! En un momento será procesado tu pedido.</p>

    <script>
        function actualizarTotal() {
            // Obtener el precio del producto seleccionado
            const productoSelect = document.getElementById("producto");
            const precioProducto = parseInt(productoSelect.options[productoSelect.selectedIndex].dataset.precio);

            // Sumar precios de ingredientes seleccionados
            const preciosIngredientes = Array.from(document.querySelectorAll("#ingredientes input:checked"))
                .map(checkbox => parseInt(checkbox.dataset.precio));

            // Sumar precios de salsas seleccionadas
            const preciosSalsas = Array.from(document.querySelectorAll("#salsas input:checked"))
                .map(checkbox => parseInt(checkbox.dataset.precio));

            // Calcular total
            const total = precioProducto + preciosIngredientes.reduce((a, b) => a + b, 0) + preciosSalsas.reduce((a, b) => a + b, 0);

            // Actualizar el total en pantalla
            document.getElementById("total").textContent = total.toLocaleString();
        }

        function enviarPedido() {
            // Obtener producto seleccionado
            const producto = document.getElementById("producto").value;

            // Obtener ingredientes seleccionados
            const ingredientesSeleccionados = Array.from(document.querySelectorAll("#ingredientes input:checked"))
                .map(checkbox => checkbox.value);

            const ingredientes = ingredientesSeleccionados.length > 0 
                ? ingredientesSeleccionados.join(", ") 
                : "Ninguno";

            // Obtener salsas seleccionadas
            const salsasSeleccionadas = Array.from(document.querySelectorAll("#salsas input:checked"))
                .map(checkbox => checkbox.value);

            const salsas = salsasSeleccionadas.length > 0 
                ? salsasSeleccionadas.join(", ") 
                : "Ninguna";

            // Obtener el total
            const total = document.getElementById("total").textContent;

            // Crear mensaje
            let mensaje = `Hola, quiero pedir:\n- Producto: ${producto}\n- Ingredientes adicionales: ${ingredientes}\n- Salsas: ${salsas}\n- Total: $${total}`;

            // Reemplazar espacios y saltos de línea con codificación de URL
            mensaje = encodeURIComponent(mensaje);

            // Tu número de WhatsApp (sin '+')
            const numero = "573194500736";

            // Redirigir a WhatsApp
            window.open(`https://wa.me/${numero}?text=${mensaje}`, "_blank");

            // Mostrar mensaje de confirmación
            document.getElementById("mensaje-confirmacion").style.display = "block";
        }
    </script>
</body>
</html>
