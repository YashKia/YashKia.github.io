---
permalink: /play/
title: "Play"
author_profile: true
---

<div class="play-container">
  <h1>Let's Play a Game!</h1>
  
  <div class="game-wrapper">
    <div id="game-container">
      <div id="box" class="box"></div>
      <div id="score-display">Score: <span id="score">0</span></div>
      <div id="timer-display">Time: <span id="time">30</span>s</div>
      <button id="start-btn" class="game-btn">Start Game</button>
      <div id="instructions">
        <p>Click or tap on the moving square as many times as you can before time runs out!</p>
        <p>You have 30 seconds. Each successful click gives you 1 point.</p>
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
  
  #game-container {
    position: relative;
    width: 100%;
    height: 400px;
    border: 2px solid var(--darker-purple);
    border-radius: 8px;
    background-color: white;
    overflow: hidden;
  }
  
  .box {
    position: absolute;
    width: 50px;
    height: 50px;
    background-color: var(--darker-purple);
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    cursor: pointer;
    border-radius: 8px;
    display: none;
  }
  
  #score-display, #timer-display {
    position: absolute;
    font-size: 18px;
    font-weight: bold;
    padding: 5px 10px;
    background-color: rgba(255, 255, 255, 0.8);
    border-radius: 5px;
  }
  
  #score-display {
    top: 10px;
    right: 10px;
  }
  
  #timer-display {
    top: 10px;
    left: 10px;
  }
  
  .game-btn {
    margin-top: 20px;
    padding: 10px 20px;
    background-color: var(--darker-purple);
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
    position: absolute;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
  }
  
  .game-btn:hover {
    background-color: var(--darkest-purple);
  }
  
  #instructions {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 80%;
    text-align: center;
  }
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const box = document.getElementById('box');
  const startBtn = document.getElementById('start-btn');
  const scoreDisplay = document.getElementById('score');
  const timeDisplay = document.getElementById('time');
  const gameContainer = document.getElementById('game-container');
  const instructions = document.getElementById('instructions');
  
  let score = 0;
  let timer;
  let gameRunning = false;
  let timeLeft = 30;
  
  function moveBox() {
    const containerWidth = gameContainer.offsetWidth;
    const containerHeight = gameContainer.offsetHeight;
    const boxSize = 50;
    
    // Calculate random position within the container boundaries
    const maxX = containerWidth - boxSize;
    const maxY = containerHeight - boxSize;
    
    const newX = Math.floor(Math.random() * maxX);
    const newY = Math.floor(Math.random() * maxY);
    
    box.style.left = newX + 'px';
    box.style.top = newY + 'px';
  }
  
  function updateTimer() {
    timeLeft--;
    timeDisplay.textContent = timeLeft;
    if (timeLeft <= 0) {
      endGame();
    }
  }
  
  function startGame() {
    score = 0;
    timeLeft = 30;
    scoreDisplay.textContent = score;
    timeDisplay.textContent = timeLeft;
    startBtn.style.display = 'none';
    instructions.style.display = 'none';
    box.style.display = 'block';
    gameRunning = true;
    
    // Set initial box position
    moveBox();
    
    // Setup timer
    timer = setInterval(updateTimer, 1000);
  }
  
  function endGame() {
    clearInterval(timer);
    gameRunning = false;
    box.style.display = 'none';
    startBtn.textContent = 'Play Again';
    startBtn.style.display = 'block';
    instructions.innerHTML = `<h2>Game Over!</h2><p>Your score: ${score}</p>`;
    instructions.style.display = 'block';
  }
  
  box.addEventListener('click', function() {
    if (gameRunning) {
      score++;
      scoreDisplay.textContent = score;
      moveBox();
    }
  });
  
  startBtn.addEventListener('click', function() {
    startGame();
  });
});
</script> 