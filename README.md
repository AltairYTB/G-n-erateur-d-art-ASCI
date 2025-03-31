<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Générateur d'Art ASCII</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f5f5;
        }
        header {
            background-color: #333;
            color: white;
            padding: 15px 0;
            text-align: center;
        }
        .container {
            max-width: 800px;
            margin: 30px auto;
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
        }
        .ascii-box {
            width: 100%;
            height: 300px;
            background-color: #222;
            color: white;
            font-size: 18px;
            line-height: 1.5;
            padding: 10px;
            border-radius: 10px;
            font-family: "Courier New", monospace;
            resize: none;
            white-space: pre-wrap;
            overflow: auto;
            margin-top: 20px;
        }
        .controls {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        .color-picker {
            padding: 5px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .button {
            background-color: #007bff;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .button:hover {
            background-color: #0056b3;
        }
        footer {
            text-align: center;
            margin-top: 40px;
            font-size: 14px;
            color: #777;
        }
    </style>
</head>
<body>

    <header>
        <h1>Générateur d'Art ASCII</h1>
    </header>

    <div class="container">
        <h2>Crée ton Art ASCII</h2>
        <textarea id="asciiBox" class="ascii-box" placeholder="Commence à dessiner avec des caractères..."></textarea>

        <div class="controls">
            <div>
                <label for="drawColor">Couleur du dessin: </label>
                <input id="drawColor" type="color" class="color-picker" value="#ffffff">
            </div>
            <div>
                <label for="bgColor">Couleur de fond: </label>
                <input id="bgColor" type="color" class="color-picker" value="#222222">
            </div>
        </div>

        <button class="button" onclick="applyColors()">Appliquer les couleurs</button>

        <h3>Option de Sauvegarde</h3>
        <button class="button" onclick="saveArt()">Sauvegarder mon Art ASCII</button>
    </div>

    <footer>
        <p>Créé avec ♥ par toi-même !</p>
    </footer>

    <script>
        // Fonction pour appliquer les couleurs de fond et du dessin
        function applyColors() {
            const drawColor = document.getElementById('drawColor').value;
            const bgColor = document.getElementById('bgColor').value;
            const asciiBox = document.getElementById('asciiBox');

            // Appliquer les couleurs
            asciiBox.style.color = drawColor;
            asciiBox.style.backgroundColor = bgColor;
        }

        // Fonction pour sauvegarder l'art ASCII dans un fichier texte
        function saveArt() {
            const asciiContent = document.getElementById('asciiBox').value;
            const blob = new Blob([asciiContent], { type: 'text/plain' });
            const link = document.createElement('a');
            link.href = URL.createObjectURL(blob);
            link.download = 'art_ascii.txt';
            link.click();
        }
    </script>

</body>
</html>
