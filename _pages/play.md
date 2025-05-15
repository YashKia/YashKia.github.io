---
permalink: /play/
title: "Play"
author_profile: true
---

<div class="play-container">
  <h1>Simple Dice Game</h1>
  
  <div class="game-wrapper">
    <div id="dice-game">
      <div id="dice-container">
        <div id="dice">
          <span id="dice-value">1</span>
        </div>
      </div>
      
      <div id="game-info">
        <p id="score-display">Your score: <span id="score">0</span></p>
        <p id="message">Roll the dice to start!</p>
      </div>
      
      <div id="game-controls">
        <button id="roll-button" onclick="rollDice()">Roll Dice</button>
        <button id="reset-button" onclick="resetGame()">New Game</button>
      </div>
      
      <div id="game-rules">
        <h3>Rules:</h3>
        <ul>
          <li>Roll the dice to add to your score</li>
          <li>Try to get as close to 21 as possible</li>
          <li>If you go over 21, you lose!</li>
          <li>Click "New Game" to start over</li>
        </ul>
      </div>
    </div>
  </div>
</div>

<style>
  .play-container {
    max-width: 800px;
    margin: 0 auto;
    text-align: center;
  }
  
  .game-wrapper {
    margin: 30px auto;
    border-radius: 8px;
    background-color: #f8f8f8;
    padding: 20px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  }
  
  #dice-container {
    margin: 20px auto;
  }
  
  #dice {
    width: 100px;
    height: 100px;
    background-color: white;
    border: 2px solid #7D6E96;
    border-radius: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 3em;
    font-weight: bold;
    margin: 0 auto;
  }
  
  #game-info {
    margin: 20px 0;
    font-size: 1.2em;
  }
  
  #message {
    font-weight: bold;
    font-size: 1.2em;
    color: #7D6E96;
    min-height: 30px;
  }
  
  #game-controls {
    margin: 20px 0;
  }
  
  #game-controls button {
    margin: 10px;
    padding: 10px 20px;
    background-color: #7D6E96;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
  }
  
  #game-controls button:hover {
    background-color: #4A3A69;
  }
  
  #game-rules {
    margin: 30px 0;
    text-align: left;
    padding: 15px;
    border-radius: 8px;
    background-color: #f0f0f0;
  }
</style>

<script>
  // Game variables
  var score = 0;
  var gameOver = false;
  
  // DOM elements
  var diceElement = document.getElementById('dice-value');
  var scoreElement = document.getElementById('score');
  var messageElement = document.getElementById('message');
  var rollButton = document.getElementById('roll-button');
  
  // Roll the dice function
  function rollDice() {
    if (gameOver) {
      return;
    }
    
    // Generate random number between 1 and 6
    var roll = Math.floor(Math.random() * 6) + 1;
    
    // Update dice display
    diceElement.textContent = roll;
    
    // Add to score
    score += roll;
    scoreElement.textContent = score;
    
    // Check win/lose conditions
    if (score === 21) {
      messageElement.textContent = "You win! Perfect 21!";
      messageElement.style.color = "green";
      gameOver = true;
    } else if (score > 21) {
      messageElement.textContent = "You went over 21! Game over.";
      messageElement.style.color = "red";
      gameOver = true;
    } else {
      messageElement.textContent = "You rolled a " + roll + ". Roll again or start a new game.";
    }
  }
  
  // Reset game function
  function resetGame() {
    score = 0;
    gameOver = false;
    diceElement.textContent = "1";
    scoreElement.textContent = "0";
    messageElement.textContent = "Roll the dice to start!";
    messageElement.style.color = "#7D6E96";
  }
  
  // Initialize game when page loads
  window.onload = function() {
    resetGame();
  };
</script>