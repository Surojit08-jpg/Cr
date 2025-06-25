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
body {
  font-family: Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  background-color: #f4f4f4;
}

.container {
  text-align: center;
}

.crypts {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.crypt-btn {
  background-color: #007bff;
  color: white;
  font-size: 20px;
  padding: 15px 30px;
  margin: 0 10px;
  border: none;
  cursor: pointer;
  border-radius: 5px;
}

.crypt-btn:hover {
  background-color: #0056b3;
}

button:active {
  background-color: #003f73;
}

#message {
  font-size: 18px;
  margin-top: 20px;
  font-weight: bold;
}

p {
  font-size: 18px;
}// Get references to the elements
const cryptBtns = document.querySelectorAll('.crypt-btn');
const creditsDisplay = document.getElementById('credits');
const messageDisplay = document.getElementById('message');

let credits = 100; // Starting credits

// Function to open a crypt
function openCrypt(cryptId) {
  if (credits <= 0) {
    messageDisplay.textContent = "Out of Credits! Refresh to restart.";
    return;
  }

  // Deduct 10 credits for each crypt opened
  credits -= 10;
  creditsDisplay.textContent = credits;

  // Randomize the outcome for the selected crypt
  const outcome = getCryptOutcome();

  // Display outcome
  messageDisplay.textContent = outcome.message;

  // Update credits based on outcome
  credits += outcome.change;
  creditsDisplay.textContent = credits;
}

// Function to randomize the outcome of a crypt
function getCryptOutcome() {
  // Randomly decide the outcome: +20, -10, or 0
  const rand = Math.random();

  if (rand < 0.33) {
    // +20 credits (reward)
    return {
      message: "You found treasure! +20 Credits!",
      change: 20,
    };
  } else if (rand < 0.66) {
    // -10 credits (penalty)
    return {
      message: "Oh no! You lost 10 credits!",
      change: -10,
    };
  } else {
    // 0 credits (nothing found)
    return {
      message: "Nothing found... Try again!",
      change: 0,
    };
  }
}

// Event listeners for crypt buttons
cryptBtns.forEach((btn) => {
  btn.addEventListener('click', () => openCrypt(btn.id));
});
