---
permalink: /interactive/
title: "Dice Game"
author_profile: true
---

<div class="interactive-container">
  <h1>Dice Probability Game</h1>
  
  <div class="section">
    <p>Test your understanding of probability with this simple dice game:</p>
    
    <div class="game-container">
      <div class="dice-container">
        <div class="dice" id="dice1">1</div>
        <div class="dice" id="dice2">1</div>
      </div>
      
      <div class="game-controls">
        <div class="score-display">Score: <span id="score">0</span></div>
      </div>
      
      <div class="prediction-container">
        <p>Make your prediction, then roll:</p>
        <div class="prediction-options">
          <button onclick="playGame('higher')">Higher than 7</button>
          <button onclick="playGame('equal')">Equal to 7</button>
          <button onclick="playGame('lower')">Lower than 7</button>
        </div>
      </div>
      
      <div id="result" class="result"></div>
    </div>
  </div>
</div>

<style>
  .interactive-container {
    max-width: 900px;
    margin: 0 auto;
  }
  
  .section {
    margin: 40px 0;
    padding: 20px;
    background-color: #f9f9f9;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  }
  
  .game-container {
    text-align: center;
    padding: 20px;
  }
  
  .dice-container {
    display: flex;
    justify-content: center;
    margin: 20px 0;
    gap: 20px;
  }
  
  .dice {
    width: 80px;
    height: 80px;
    background-color: white;
    border-radius: 10px;
    border: 2px solid #333;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 32px;
    font-weight: bold;
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
  }
  
  .game-controls {
    margin: 20px 0;
  }
  
  .score-display {
    font-size: 18px;
    font-weight: bold;
  }
  
  .prediction-container {
    margin: 20px 0;
  }
  
  .prediction-options {
    display: flex;
    justify-content: center;
    gap: 10px;
  }
  
  .prediction-options button {
    padding: 8px 15px;
    background-color: #2196F3;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .prediction-options button:hover {
    background-color: #0b7dda;
  }
  
  .result {
    margin-top: 20px;
    font-size: 18px;
    font-weight: bold;
    min-height: 27px;
  }
  
  .correct {
    color: green;
  }
  
  .incorrect {
    color: red;
  }
</style>

<script>
  var score = 0;
  
  function playGame(prediction) {
    // Generate random numbers for dice
    var dieValue1 = Math.floor(Math.random() * 6) + 1;
    var dieValue2 = Math.floor(Math.random() * 6) + 1;
    var sum = dieValue1 + dieValue2;
    
    // Update dice display
    document.getElementById('dice1').textContent = dieValue1;
    document.getElementById('dice2').textContent = dieValue2;
    
    // Check if prediction was correct
    var isCorrect = false;
    
    if (prediction === 'higher' && sum > 7) {
      isCorrect = true;
    } else if (prediction === 'equal' && sum === 7) {
      isCorrect = true;
    } else if (prediction === 'lower' && sum < 7) {
      isCorrect = true;
    }
    
    // Update score and display result
    var resultElement = document.getElementById('result');
    
    if (isCorrect) {
      score++;
      resultElement.textContent = "Correct! The sum is " + sum;
      resultElement.className = "result correct";
    } else {
      resultElement.textContent = "Incorrect! The sum is " + sum;
      resultElement.className = "result incorrect";
    }
    
    document.getElementById('score').textContent = score;
  }
</script> 