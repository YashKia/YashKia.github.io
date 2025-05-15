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
        <div id="dice" class="dice">
          <div class="face front">1</div>
          <div class="face back">6</div>
          <div class="face top">2</div>
          <div class="face bottom">5</div>
          <div class="face right">3</div>
          <div class="face left">4</div>
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
    perspective: 600px;
    margin-bottom: 20px;
  }
  
  .dice {
    position: relative;
    width: 100px;
    height: 100px;
    transform-style: preserve-3d;
    transition: transform 1s;
  }
  
  .face {
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: white;
    border: 2px solid var(--darker-purple);
    border-radius: 10px;
    font-size: 3em;
    font-weight: bold;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: inset 0 0 15px rgba(0,0,0,0.1);
  }
  
  .front {
    transform: translateZ(50px);
  }
  
  .back {
    transform: translateZ(-50px) rotateY(180deg);
  }
  
  .top {
    transform: rotateX(-90deg) translateZ(50px);
  }
  
  .bottom {
    transform: rotateX(90deg) translateZ(50px);
  }
  
  .right {
    transform: rotateY(90deg) translateZ(50px);
  }
  
  .left {
    transform: rotateY(-90deg) translateZ(50px);
  }
  
  #game-info {
    margin: 20px 0;
    font-size: 1.2em;
  }
  
  #roll-result {
    font-weight: bold;
    font-size: 1.5em;
    color: var(--darker-purple);
  }
  
  #game-controls {
    margin: 20px 0;
  }
  
  .game-btn {
    margin: 10px;
    padding: 10px 20px;
    background-color: var(--darker-purple);
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
    transition: background-color 0.3s;
  }
  
  .game-btn:hover {
    background-color: var(--darkest-purple);
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
  console.log('Dice game loaded');
  
  // DOM elements
  const dice = document.getElementById('dice');
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
    console.log('Initializing new game');
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
    console.log('Rolled:', currentRoll);
    
    // Animate dice
    const rotX = Math.floor(Math.random() * 4) * 90;
    const rotY = Math.floor(Math.random() * 4) * 90;
    const rotZ = Math.floor(Math.random() * 4) * 90;
    
    dice.style.transform = `rotateX(${rotX}deg) rotateY(${rotY}deg) rotateZ(${rotZ}deg)`;
    
    // Update displays after roll
    rollResult.textContent = `You rolled: ${currentRoll}`;
    
    // Update score based on whose turn it is
    if (isPlayerTurn) {
      playerScore += currentRoll;
      scoreDisplay.textContent = `Your score: ${playerScore}`;
      
      // Check if player went over
      if (playerScore > targetScore) {
        endGame('player-bust');
      } else if (playerScore === targetScore) {
        endGame('player-win');
      }
    } else {
      computerScore += currentRoll;
      rollResult.textContent = `Computer rolled: ${currentRoll}`;
      
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
    
    console.log('Game ended:', result);
  }
  
  // Event listeners
  rollBtn.addEventListener('click', function() {
    console.log('Roll button clicked');
    if (isPlayerTurn && !gameOver) {
      rollDice();
    }
  });
  
  holdBtn.addEventListener('click', function() {
    console.log('Hold button clicked');
    if (isPlayerTurn && !gameOver) {
      hold();
    }
  });
  
  newGameBtn.addEventListener('click', function() {
    console.log('New game button clicked');
    initGame();
  });
  
  // Initialize game on load
  initGame();
});
</script>