<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Examen</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            margin: 20px;
        }
        .container {
            max-width: 600px;
            margin: auto;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }
        .title {
            text-align: center;
            font-size: 24px;
            margin-bottom: 20px;
        }
        .input-group {
            margin-bottom: 15px;
        }
        .input-group label {
            display: block;
            margin-bottom: 5px;
        }
        .input-group input {
            width: 100%;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        .result {
            margin-top: 20px;
            padding: 15px;
            background-color: #eef;
            border: 1px solid #aac;
            border-radius: 4px;
            font-size: 18px;
            text-align: center;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="title">Calculadora de Examen</div>

        <!-- Bloque 1 -->
        <h3>Bloque 1: 100 preguntas (1 punto por correcta)</h3>
        <div class="input-group">
            <label for="bloque1-correctas">Correctas:</label>
            <input id="bloque1-correctas" type="number" placeholder="0" />
        </div>
        <div class="input-group">
            <label for="bloque1-incorrectas">Incorrectas:</label>
            <input id="bloque1-incorrectas" type="number" placeholder="0" />
        </div>
        <div class="input-group">
            <label for="bloque1-blanco">No contestadas:</label>
            <input id="bloque1-blanco" type="number" placeholder="0" />
        </div>

        <!-- Bloque 2 -->
        <h3>Bloque 2: 50 preguntas prácticas (2 puntos por correcta)</h3>
        <div class="input-group">
            <label for="bloque2-correctas">Correctas:</label>
            <input id="bloque2-correctas" type="number" placeholder="0" />
        </div>
        <div class="input-group">
            <label for="bloque2-incorrectas">Incorrectas:</label>
            <input id="bloque2-incorrectas" type="number" placeholder="0" />
        </div>
        <div class="input-group">
            <label for="bloque2-blanco">No contestadas:</label>
            <input id="bloque2-blanco" type="number" placeholder="0" />
        </div>

        <button onclick="calcularNota()">Calcular Nota Final</button>

        <div class="result" id="resultado"></div>
    </div>

    <script>
        function calcularNota() {
            // Bloque 1
            const b1_correctas = parseInt(document.getElementById('bloque1-correctas').value) || 0;
            const b1_incorrectas = parseInt(document.getElementById('bloque1-incorrectas').value) || 0;
            const b1_blanco = parseInt(document.getElementById('bloque1-blanco').value) || 0;

            // Bloque 2
            const b2_correctas = parseInt(document.getElementById('bloque2-correctas').value) || 0;
            const b2_incorrectas = parseInt(document.getElementById('bloque2-incorrectas').value) || 0;
            const b2_blanco = parseInt(document.getElementById('bloque2-blanco').value) || 0;

            // Validar que los totales no excedan el número de preguntas
            if (b1_correctas + b1_incorrectas + b1_blanco > 100) {
                document.getElementById('resultado').innerText = 'El Bloque 1 no puede tener más de 100 preguntas.';
                return;
            }

            if (b2_correctas + b2_incorrectas + b2_blanco > 50) {
                document.getElementById('resultado').innerText = 'El Bloque 2 no puede tener más de 50 preguntas.';
                return;
            }

            // Cálculo de notas
            const nota_bloque1 = b1_correctas - (b1_incorrectas * (1 / 3));
            const nota_bloque2 = (b2_correctas * 2) - (b2_incorrectas * (2 / 3));

            // Suma total
            const nota_total = nota_bloque1 + nota_bloque2;

            // Mostrar el resultado
            document.getElementById('resultado').innerText = `Nota final: ${nota_total.toFixed(2)} / 200 puntos.`;
        }
    </script>
</body>
</html>
