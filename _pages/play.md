---
permalink: /play/
title: "Play"
author_profile: true
---

<div class="play-container">
  <h1>Dice Rolling Game</h1>
  
  <div class="game-wrapper">
    <div id="dice-game">
      <div id="dice-container">
        <div id="dice">
          <span id="dice-value">1</span>
        </div>
      </div>
      
      <div id="game-info">
        <p id="roll-result">Roll the dice to start</p>
        <p id="score">Your score: 0</p>
        <p id="target-score">Target score: 21</p>
        <p id="roll-count">Rolls: 0</p>
      </div>
      
      <div id="game-controls">
        <button id="roll-btn" class="game-btn">Roll Dice</button>
        <button id="hold-btn" class="game-btn">Hold</button>
        <button id="new-game-btn" class="game-btn">New Game</button>
      </div>
      
      <div id="game-rules">
        <h3>Rules:</h3>
        <ul>
          <li>Roll the dice to accumulate points</li>
          <li>Your goal is to reach exactly 21 points</li>
          <li>If you go over 21, you lose!</li>
          <li>Use the "Hold" button to keep your current score and end your turn</li>
          <li>The computer will then take its turn</li>
          <li>Whoever gets closest to 21 without going over wins!</li>
        </ul>
      </div>
      
      <div id="message" class="hidden"></div>
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
  
  #dice-game {
    position: relative;
    width: 100%;
    padding: 20px;
  }
  
  #dice-container {
    width: 100%;
    height: 150px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 20px;
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
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    transition: transform 0.3s ease;
  }
  
  #dice.rolling {
    animation: roll-dice 0.5s ease;
  }
  
  @keyframes roll-dice {
    0% { transform: rotate(0deg) scale(1); }
    50% { transform: rotate(180deg) scale(1.2); }
    100% { transform: rotate(360deg) scale(1); }
  }
  
  #game-info {
    margin: 20px 0;
    font-size: 1.2em;
  }
  
  #roll-result {
    font-weight: bold;
    font-size: 1.5em;
    color: #7D6E96;
  }
  
  #game-controls {
    margin: 20px 0;
  }
  
  .game-btn {
    margin: 10px;
    padding: 10px 20px;
    background-color: #7D6E96;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
    transition: background-color 0.3s;
  }
  
  .game-btn:hover {
    background-color: #4A3A69;
  }
  
  .game-btn:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }
  
  #game-rules {
    margin: 30px 0;
    text-align: left;
    padding: 15px;
    border-radius: 8px;
    background-color: #f0f0f0;
  }
  
  #message {
    padding: 15px;
    margin: 20px 0;
    border-radius: 8px;
    font-weight: bold;
    font-size: 1.2em;
  }
  
  .win {
    background-color: #d4edda;
    color: #155724;
  }
  
  .lose {
    background-color: #f8d7da;
    color: #721c24;
  }
  
  .draw {
    background-color: #fff3cd;
    color: #856404;
  }
  
  .hidden {
    display: none;
  }
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
  // DOM elements
  const dice = document.getElementById('dice');
  const diceValue = document.getElementById('dice-value');
  const rollResult = document.getElementById('roll-result');
  const scoreDisplay = document.getElementById('score');
  const targetScoreDisplay = document.getElementById('target-score');
  const rollCountDisplay = document.getElementById('roll-count');
  const rollBtn = document.getElementById('roll-btn');
  const holdBtn = document.getElementById('hold-btn');
  const newGameBtn = document.getElementById('new-game-btn');
  const messageDisplay = document.getElementById('message');
  
  // Game state
  let playerScore = 0;
  let computerScore = 0;
  let currentRoll = 0;
  let rollCount = 0;
  let isPlayerTurn = true;
  let gameOver = false;
  
  // Target score
  const targetScore = 21;
  
  // Initialize the game
  function initGame() {
    playerScore = 0;
    computerScore = 0;
    rollCount = 0;
    isPlayerTurn = true;
    gameOver = false;
    
    updateDisplays();
    rollResult.textContent = 'Roll the dice to start';
    messageDisplay.className = 'hidden';
    
    rollBtn.disabled = false;
    holdBtn.disabled = false;
  }
  
  // Update all displays
  function updateDisplays() {
    scoreDisplay.textContent = `Your score: ${playerScore}`;
    targetScoreDisplay.textContent = `Target score: ${targetScore}`;
    rollCountDisplay.textContent = `Rolls: ${rollCount}`;
  }
  
  // Roll the dice
  function rollDice() {
    if (gameOver) return;
    
    rollCount++;
    
    // Generate random number 1-6
    currentRoll = Math.floor(Math.random() * 6) + 1;
    
    // Animate dice
    dice.classList.add('rolling');
    
    // Update dice value after animation
    setTimeout(() => {
      dice.classList.remove('rolling');
      diceValue.textContent = currentRoll;
      
      // Update displays after roll
      if (isPlayerTurn) {
        rollResult.textContent = `You rolled: ${currentRoll}`;
        playerScore += currentRoll;
        scoreDisplay.textContent = `Your score: ${playerScore}`;
        
        // Check if player went over
        if (playerScore > targetScore) {
          endGame('player-bust');
        } else if (playerScore === targetScore) {
          endGame('player-win');
        }
      } else {
        rollResult.textContent = `Computer rolled: ${currentRoll}`;
        computerScore += currentRoll;
        
        // Check if computer went over
        if (computerScore > targetScore) {
          endGame('computer-bust');
        } else if (computerScore === targetScore) {
          endGame('computer-win');
        } else if (computerScore >= playerScore || computerScore >= 17) {
          // Computer holds at 17 or higher, or if they're beating the player
          compareScores();
        } else {
          // Computer decides to roll again
          setTimeout(rollDice, 1000);
        }
      }
      
      updateDisplays();
    }, 500);
  }
  
  // Player holds their score
  function hold() {
    if (gameOver || !isPlayerTurn) return;
    
    isPlayerTurn = false;
    rollResult.textContent = 'Computer\'s turn';
    
    // Disable player buttons during computer's turn
    rollBtn.disabled = true;
    holdBtn.disabled = true;
    
    // Computer takes turn after a delay
    setTimeout(() => {
      computerTurn();
    }, 1000);
  }
  
  // Computer's turn
  function computerTurn() {
    computerScore = 0;
    rollResult.textContent = 'Computer is rolling...';
    
    // First roll
    setTimeout(rollDice, 1000);
  }
  
  // Compare scores to determine winner
  function compareScores() {
    if (playerScore > targetScore) {
      endGame('player-bust');
    } else if (computerScore > targetScore) {
      endGame('computer-bust');
    } else if (playerScore > computerScore) {
      endGame('player-win');
    } else if (computerScore > playerScore) {
      endGame('computer-win');
    } else {
      endGame('draw');
    }
  }
  
  // End the game
  function endGame(result) {
    gameOver = true;
    rollBtn.disabled = true;
    holdBtn.disabled = true;
    
    messageDisplay.classList.remove('hidden', 'win', 'lose', 'draw');
    
    switch (result) {
      case 'player-win':
        messageDisplay.textContent = 'You win! 🎉';
        messageDisplay.classList.add('win');
        break;
      case 'player-bust':
        messageDisplay.textContent = `You went over ${targetScore}! Computer wins.`;
        messageDisplay.classList.add('lose');
        break;
      case 'computer-win':
        messageDisplay.textContent = 'Computer wins!';
        messageDisplay.classList.add('lose');
        break;
      case 'computer-bust':
        messageDisplay.textContent = `Computer went over ${targetScore}! You win! 🎉`;
        messageDisplay.classList.add('win');
        break;
      case 'draw':
        messageDisplay.textContent = 'It\'s a draw!';
        messageDisplay.classList.add('draw');
        break;
    }
  }
  
  // Add event listeners
  if (rollBtn) {
    rollBtn.addEventListener('click', function() {
      if (isPlayerTurn && !gameOver) {
        rollDice();
      }
    });
  }
  
  if (holdBtn) {
    holdBtn.addEventListener('click', function() {
      if (isPlayerTurn && !gameOver) {
        hold();
      }
    });
  }
  
  if (newGameBtn) {
    newGameBtn.addEventListener('click', function() {
      initGame();
    });
  }
  
  // Initialize game on load
  initGame();
});
</script>