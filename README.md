# Cr<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Crypt Game</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <h1>Crypt Game</h1>
    <p>Choose a crypt to open and see what's inside!</p>

    <!-- Crypt Buttons (3 crypts to choose from) -->
    <div class="crypts">
      <button class="crypt-btn" id="crypt1">Crypt 1</button>
      <button class="crypt-btn" id="crypt2">Crypt 2</button>
      <button class="crypt-btn" id="crypt3">Crypt 3</button>
    </div>

    <p id="message"></p>
    <p>Credits: <span id="credits">100</span></p>
  </div>

  <script src="crypt.js"></script>
</body>
</html>
