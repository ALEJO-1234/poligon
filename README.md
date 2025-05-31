<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Paletas de Colores | VENESOL</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Generador de Paletas</h1>
        <p>Haz clic en cualquier color para copiar su código HEX.</p>
        
        <div class="color-palette" id="palette"></div>
        
        <button id="generate-btn">Generar Nueva Paleta</button>
    </div>

    <script src="script.js"></script>
</body>
</html>
/* Estilos generales */
body {
    font-family: 'Arial', sans-serif;
    background: #f5f5f5;
    margin: 0;
    padding: 20px;
    text-align: center;
}

.container {
    max-width: 800px;
    margin: 0 auto;
    background: white;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

h1 {
    color: #333;
}

/* Paleta de colores */
.color-palette {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin: 30px 0;
    justify-content: center;
}

.color-box {
    width: 100px;
    height: 100px;
    border-radius: 8px;
    cursor: pointer;
    transition: transform 0.2s;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    padding-bottom: 10px;
    font-size: 12px;
    color: white;
    text-shadow: 0 1px 3px rgba(0, 0, 0, 0.5);
}

.color-box:hover {
    transform: scale(1.05);
}

/* Botón */
button {
    background: #8247e5;
    color: white;
    border: none;
    padding: 12px 25px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 16px;
    transition: background 0.3s;
}

button:hover {
    background: #6a3bb5;
}
document.addEventListener('DOMContentLoaded', () => {
    const palette = document.getElementById('palette');
    const generateBtn = document.getElementById('generate-btn');
    
    // Generar paleta inicial
    generatePalette();
    
    // Botón para generar nueva paleta
    generateBtn.addEventListener('click', generatePalette);
    
    // Función principal
    function generatePalette() {
        palette.innerHTML = '';
        for (let i = 0; i < 5; i++) {
            const color = getRandomColor();
            const colorBox = document.createElement('div');
            colorBox.className = 'color-box';
            colorBox.style.backgroundColor = color;
            colorBox.textContent = color;
            
            // Copiar código HEX al hacer clic
            colorBox.addEventListener('click', () => {
                navigator.clipboard.writeText(color);
                colorBox.textContent = '¡Copiado!';
                setTimeout(() => colorBox.textContent = color, 1000);
            });
            
            palette.appendChild(colorBox);
        }
    }
    
    // Generar color HEX aleatorio
    function getRandomColor() {
        const letters = '0123456789ABCDEF';
        let color = '#';
        for (let i = 0; i < 6; i++) {
            color += letters[Math.floor(Math.random() * 16)];
        }
        return color;
    }
});

