---
permalink: /play/
title: "Play"
author_profile: true
---

<div class="play-container">
  <h1>Probability Challenge</h1>
  
  <div class="game-wrapper">
    <div id="game-container">
      <div id="game-board">
        <div id="coin-container">
          <div id="coin">
            <div class="heads"></div>
            <div class="tails"></div>
          </div>
        </div>
        
        <div id="dice-container">
          <div id="dice">
            <div class="dice-face" id="dice-face"></div>
          </div>
        </div>
        
        <div id="card-container">
          <div id="card">
            <div class="card-inner">
              <div class="card-front"></div>
              <div class="card-back"></div>
            </div>
          </div>
        </div>
      </div>
      
      <div id="challenge-display"></div>
      <div id="score-display">Score: <span id="score">0</span> / <span id="total-rounds">0</span></div>
      
      <div id="controls">
        <div id="options-container"></div>
        <button id="start-btn" class="game-btn">Start Game</button>
        <button id="next-btn" class="game-btn" style="display: none;">Next Challenge</button>
      </div>
      
      <div id="instructions">
        <h2>How to Play</h2>
        <p>Test your understanding of probability with fun challenges!</p>
        <p>You'll face 10 probability-based scenarios with coins, dice, and cards.</p>
        <p>Make predictions based on probability theory and see how many you get right.</p>
      </div>
      
      <div id="result" style="display: none;"></div>
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
    height: 500px;
    border: 2px solid var(--darker-purple);
    border-radius: 8px;
    background-color: white;
    overflow: hidden;
    padding: 20px;
  }
  
  #game-board {
    display: flex;
    justify-content: space-around;
    align-items: center;
    height: 200px;
    margin-bottom: 20px;
    display: none;
  }
  
  /* Coin styling */
  #coin-container {
    width: 100px;
    height: 100px;
    perspective: 1000px;
  }
  
  #coin {
    width: 100%;
    height: 100%;
    position: relative;
    transition: transform 1s;
    transform-style: preserve-3d;
  }
  
  .heads, .tails {
    position: absolute;
    width: 100%;
    height: 100%;
    border-radius: 50%;
    backface-visibility: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    font-size: 1.5em;
    border: 2px solid #ccc;
  }
  
  .heads {
    background-color: gold;
    color: #333;
  }
  
  .heads:after {
    content: 'H';
  }
  
  .tails {
    background-color: silver;
    color: #333;
    transform: rotateY(180deg);
  }
  
  .tails:after {
    content: 'T';
  }
  
  /* Dice styling */
  #dice-container {
    width: 100px;
    height: 100px;
    perspective: 1000px;
  }
  
  #dice {
    width: 100%;
    height: 100%;
    position: relative;
    transform-style: preserve-3d;
    transition: transform 1s;
  }
  
  .dice-face {
    width: 100%;
    height: 100%;
    border-radius: 10px;
    background-color: white;
    border: 2px solid #333;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2.5em;
    font-weight: bold;
  }
  
  /* Card styling */
  #card-container {
    width: 80px;
    height: 120px;
    perspective: 1000px;
  }
  
  #card {
    width: 100%;
    height: 100%;
    position: relative;
    transition: transform 0.8s;
    transform-style: preserve-3d;
  }
  
  .card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.8s;
    transform-style: preserve-3d;
  }
  
  .card-front, .card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    border-radius: 8px;
    border: 1px solid #333;
  }
  
  .card-front {
    background-color: white;
    color: black;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    font-size: 1.5em;
  }
  
  .card-back {
    background-color: var(--darker-purple);
    background-image: repeating-linear-gradient(
      45deg, 
      var(--darker-purple), 
      var(--darker-purple) 10px, 
      var(--darkest-purple) 10px, 
      var(--darkest-purple) 20px
    );
    transform: rotateY(180deg);
  }
  
  #challenge-display {
    background-color: #f5f0f5;
    padding: 15px;
    border-radius: 8px;
    margin: 15px 0;
    font-size: 1.1em;
    border-left: 4px solid var(--darker-purple);
    text-align: left;
    min-height: 60px;
  }
  
  #score-display {
    font-size: 18px;
    font-weight: bold;
    padding: 5px 10px;
    background-color: rgba(255, 255, 255, 0.8);
    border-radius: 5px;
    margin: 10px 0;
    text-align: right;
  }
  
  #controls {
    margin: 20px 0;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  #options-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
    margin-bottom: 15px;
    width: 100%;
  }
  
  .option-btn {
    padding: 8px 15px;
    background-color: white;
    border: 2px solid var(--darker-purple);
    color: var(--darker-purple);
    border-radius: 5px;
    cursor: pointer;
    font-weight: bold;
    transition: all 0.3s ease;
  }
  
  .option-btn:hover {
    background-color: var(--light-purple);
  }
  
  .option-btn.selected {
    background-color: var(--darker-purple);
    color: white;
  }
  
  .game-btn {
    margin: 10px 5px;
    padding: 10px 20px;
    background-color: var(--darker-purple);
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
  }
  
  .game-btn:hover {
    background-color: var(--darkest-purple);
  }
  
  #instructions {
    padding: 15px;
    margin-top: 20px;
    text-align: center;
  }
  
  #result {
    margin-top: 20px;
    padding: 15px;
    border-radius: 8px;
    font-weight: bold;
    text-align: center;
  }
  
  .correct {
    background-color: #d4edda;
    color: #155724;
    border: 1px solid #c3e6cb;
  }
  
  .incorrect {
    background-color: #f8d7da;
    color: #721c24;
    border: 1px solid #f5c6cb;
  }
  
  .final-result {
    margin-top: 30px;
    padding: 20px;
    background-color: #f5f0f5;
    border-radius: 8px;
    text-align: center;
  }
  
  @media (max-width: 600px) {
    #game-board {
      flex-direction: column;
      height: auto;
      gap: 20px;
    }
    
    #options-container {
      flex-direction: column;
    }
  }
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
  // DOM elements
  const gameBoard = document.getElementById('game-board');
  const coin = document.getElementById('coin');
  const dice = document.getElementById('dice');
  const diceFace = document.getElementById('dice-face');
  const card = document.querySelector('.card-inner');
  const cardFront = document.querySelector('.card-front');
  const challengeDisplay = document.getElementById('challenge-display');
  const scoreDisplay = document.getElementById('score');
  const totalRoundsDisplay = document.getElementById('total-rounds');
  const optionsContainer = document.getElementById('options-container');
  const startBtn = document.getElementById('start-btn');
  const nextBtn = document.getElementById('next-btn');
  const instructions = document.getElementById('instructions');
  const resultDisplay = document.getElementById('result');
  
  // Game state
  let score = 0;
  let currentRound = 0;
  let totalRounds = 10;
  let selectedOption = null;
  let correctAnswer = null;
  let gameActive = false;
  let currentChallenge = null;
  
  // Challenge types
  const challengeTypes = [
    'coin_flip',
    'coin_sequence',
    'dice_roll',
    'dice_sum',
    'card_color',
    'card_suit',
    'card_value',
    'combined_probability'
  ];
  
  // Card values and suits
  const cardValues = ['A', '2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K'];
  const cardSuits = ['♥', '♦', '♣', '♠'];
  const redSuits = ['♥', '♦'];
  
  // Initialize the game
  function initGame() {
    score = 0;
    currentRound = 0;
    gameActive = true;
    scoreDisplay.textContent = score;
    totalRoundsDisplay.textContent = totalRounds;
    
    startBtn.style.display = 'none';
    instructions.style.display = 'none';
    gameBoard.style.display = 'flex';
    
    nextChallenge();
  }
  
  // Generate the next challenge
  function nextChallenge() {
    if (currentRound >= totalRounds) {
      endGame();
      return;
    }
    
    currentRound++;
    resultDisplay.style.display = 'none';
    nextBtn.style.display = 'none';
    
    // Reset all animations and displays
    coin.style.transform = '';
    dice.style.transform = '';
    card.style.transform = '';
    
    // Randomly select a challenge type
    const challengeType = challengeTypes[Math.floor(Math.random() * challengeTypes.length)];
    generateChallenge(challengeType);
  }
  
  // Generate a specific challenge
  function generateChallenge(type) {
    optionsContainer.innerHTML = '';
    currentChallenge = type;
    
    switch(type) {
      case 'coin_flip':
        createCoinFlipChallenge();
        break;
      case 'coin_sequence':
        createCoinSequenceChallenge();
        break;
      case 'dice_roll':
        createDiceRollChallenge();
        break;
      case 'dice_sum':
        createDiceSumChallenge();
        break;
      case 'card_color':
        createCardColorChallenge();
        break;
      case 'card_suit':
        createCardSuitChallenge();
        break;
      case 'card_value':
        createCardValueChallenge();
        break;
      case 'combined_probability':
        createCombinedProbabilityChallenge();
        break;
    }
  }
  
  // Challenge creators
  function createCoinFlipChallenge() {
    challengeDisplay.innerHTML = "What is the probability of flipping a coin and getting heads?";
    
    const options = ["1/2 (50%)", "1/3 (33.3%)", "2/3 (66.7%)"];
    correctAnswer = "1/2 (50%)";
    
    createOptions(options);
  }
  
  function createCoinSequenceChallenge() {
    challengeDisplay.innerHTML = "What is the probability of flipping a coin 3 times and getting all heads?";
    
    const options = ["1/8 (12.5%)", "1/4 (25%)", "3/8 (37.5%)", "1/2 (50%)"];
    correctAnswer = "1/8 (12.5%)";
    
    createOptions(options);
  }
  
  function createDiceRollChallenge() {
    challengeDisplay.innerHTML = "What is the probability of rolling a 6 on a standard six-sided die?";
    
    const options = ["1/6 (16.7%)", "1/3 (33.3%)", "1/2 (50%)"];
    correctAnswer = "1/6 (16.7%)";
    
    createOptions(options);
  }
  
  function createDiceSumChallenge() {
    challengeDisplay.innerHTML = "When rolling two six-sided dice, what is the probability of getting a sum of 7?";
    
    const options = ["1/6 (16.7%)", "5/36 (13.9%)", "1/12 (8.3%)", "6/36 (16.7%)"];
    correctAnswer = "6/36 (16.7%)";
    
    createOptions(options);
  }
  
  function createCardColorChallenge() {
    challengeDisplay.innerHTML = "What is the probability of drawing a red card (hearts or diamonds) from a standard 52-card deck?";
    
    const options = ["1/4 (25%)", "1/2 (50%)", "3/4 (75%)"];
    correctAnswer = "1/2 (50%)";
    
    createOptions(options);
  }
  
  function createCardSuitChallenge() {
    challengeDisplay.innerHTML = "What is the probability of drawing a club from a standard 52-card deck?";
    
    const options = ["1/4 (25%)", "1/3 (33.3%)", "1/2 (50%)"];
    correctAnswer = "1/4 (25%)";
    
    createOptions(options);
  }
  
  function createCardValueChallenge() {
    challengeDisplay.innerHTML = "What is the probability of drawing a face card (Jack, Queen, or King) from a standard 52-card deck?";
    
    const options = ["3/13 (23.1%)", "1/4 (25%)", "3/26 (11.5%)"];
    correctAnswer = "3/13 (23.1%)";
    
    createOptions(options);
  }
  
  function createCombinedProbabilityChallenge() {
    challengeDisplay.innerHTML = "What is the probability of rolling a six-sided die and flipping a coin, and getting both a 3 and heads?";
    
    const options = ["1/12 (8.3%)", "1/6 (16.7%)", "1/3 (33.3%)"];
    correctAnswer = "1/12 (8.3%)";
    
    createOptions(options);
  }
  
  // Create option buttons
  function createOptions(options) {
    options.forEach(option => {
      const button = document.createElement('button');
      button.className = 'option-btn';
      button.textContent = option;
      button.addEventListener('click', () => selectOption(option, button));
      optionsContainer.appendChild(button);
    });
  }
  
  // Handle option selection
  function selectOption(option, button) {
    // Reset all buttons
    document.querySelectorAll('.option-btn').forEach(btn => {
      btn.classList.remove('selected');
    });
    
    // Select the clicked button
    button.classList.add('selected');
    selectedOption = option;
    
    // Show animation based on challenge type
    if (currentChallenge.includes('coin')) {
      flipCoin();
    } else if (currentChallenge.includes('dice')) {
      rollDice();
    } else if (currentChallenge.includes('card')) {
      drawCard();
    } else {
      // For combined challenges, show both animations
      flipCoin();
      setTimeout(rollDice, 300);
    }
    
    // After a delay, check the answer
    setTimeout(checkAnswer, 1500);
  }
  
  // Animation functions
  function flipCoin() {
    const random = Math.random();
    coin.style.transform = `rotateY(${random < 0.5 ? 0 : 180}deg)`;
  }
  
  function rollDice() {
    const random = Math.floor(Math.random() * 6) + 1;
    dice.style.transform = `rotateX(${random * 60}deg) rotateY(${random * 90}deg)`;
    diceFace.textContent = random;
  }
  
  function drawCard() {
    const randomValue = cardValues[Math.floor(Math.random() * cardValues.length)];
    const randomSuit = cardSuits[Math.floor(Math.random() * cardSuits.length)];
    const color = redSuits.includes(randomSuit) ? 'red' : 'black';
    
    cardFront.textContent = `${randomValue}${randomSuit}`;
    cardFront.style.color = color;
    card.style.transform = 'rotateY(180deg)';
  }
  
  // Check the selected answer
  function checkAnswer() {
    if (selectedOption === correctAnswer) {
      score++;
      scoreDisplay.textContent = score;
      resultDisplay.innerHTML = "Correct! 🎉";
      resultDisplay.className = "correct";
    } else {
      resultDisplay.innerHTML = `Incorrect. The correct answer is ${correctAnswer}.`;
      resultDisplay.className = "incorrect";
    }
    
    resultDisplay.style.display = 'block';
    nextBtn.style.display = 'block';
  }
  
  // End the game and show results
  function endGame() {
    gameActive = false;
    gameBoard.style.display = 'none';
    optionsContainer.innerHTML = '';
    challengeDisplay.innerHTML = '';
    nextBtn.style.display = 'none';
    
    const percentage = Math.round((score / totalRounds) * 100);
    let message;
    
    if (percentage >= 90) {
      message = "Excellent! You're a probability master!";
    } else if (percentage >= 70) {
      message = "Great job! You have a solid understanding of probability.";
    } else if (percentage >= 50) {
      message = "Good effort! Keep practicing probability concepts.";
    } else {
      message = "Keep learning! Probability can be tricky, but you'll get better with practice.";
    }
    
    instructions.innerHTML = `
      <div class="final-result">
        <h2>Game Complete!</h2>
        <p>Your score: ${score} out of ${totalRounds} (${percentage}%)</p>
        <p>${message}</p>
      </div>
    `;
    
    instructions.style.display = 'block';
    startBtn.textContent = 'Play Again';
    startBtn.style.display = 'block';
  }
  
  // Event listeners
  startBtn.addEventListener('click', initGame);
  nextBtn.addEventListener('click', nextChallenge);
});
</script>