<h1>Car Racing Game</h1>
<br>
<h2>Overview</h2>
<br>
<p>This is a simple car racing game implemented using HTML, CSS, and JavaScript. The player controls a car and must avoid colliding with enemy cars while collecting points. The game increases in difficulty as the player's speed increases over time.</p>
<h2>Features</h2>
<ul>
  <li>Control the car using arrow keys</li>
  <li>Score increases by 10 for every enemy car crossed without collision</li>
  <li>Speed increases by 1 point every 5 seconds, starting from 5 and up to a maximum of 10</li>
  <li>Pause and resume functionality</li>
  </ul>

<h2>How to Play</h2>
<ol>
  <li><strong>Start the Game</strong>: Click on the start screen to begin the game.</li>
  <li><strong>Control the Car</strong>: Use the arrow keys to move your car:</li>
  <ul>
    <li>Up Arrow: Move up</li>
    <li>Down Arrow: Move down</li>
    <li>Left Arrow: Move left</li>
    <li>Right Arrow: Move right</li>
  </ul>
  <li><strong>Avoid Collisions</strong>: Navigate your car to avoid colliding with enemy cars.</li>
  <li><strong>Score Points</strong>: Each time you pass an enemy car without collision, your score increases by 10 points.</li>
  <li><strong>Pause and Resume</strong>: Use the "Pause" button to pause the game and the "Resume" button to continue.</li>
</ol>

<h2>Project Structure</h2>
<ul>
  <li><strong>index.html</strong>: The main HTML file containing the game structure.</li>
  <li><strong>style.css</strong>: The CSS file for styling the game elements.</li>
  <li><strong>script.js</strong>: The JavaScript file containing the game logic.</li>
</ul>

<h2>Code Explanation</h2>
<h3>HTML</h3>
    <p>The main elements include:</p>
    <ul>
        <li>A container for the game with the class <code>carGame</code>.</li>
        <li>A <code>startScreen</code> div that displays the start instructions.</li>
        <li>A <code>gameArea</code> div where the game action takes place.</li>
        <li>A <code>score</code> div that shows the current score and speed.</li>
        <li>Control buttons for pausing and resuming the game.</li>
    </ul>
    <h3>CSS</h3>
    <p>Basic styling for the game area, cars, and control elements to provide a visually appealing interface.</p>

  <h3>JavaScript</h3>
  <p>Main game logic, including:</p>
  <ul>
      <li>Initializing the game with <code>initializeGame</code>.</li>
      <li>Handling key presses for car movement.</li>
      <li>Moving the enemy cars and lines.</li>
      <li>Increasing the score when passing enemy cars.</li>
      <li>Incrementing the speed every 5 seconds.</li>
      <li>Pausing and resuming the game.</li>
  </ul>
  <h3>Code Snippet</h3>
    <h4>Initialize Game</h4>
    <pre><code>function initializeGame() {
    startScreen.classList.add('hide');
    gameArea.innerHTML = '';

    player.start = true;
    player.score = 0;
    player.speed = 5;
    player.paused = false;

    clearInterval(speedInterval);

    speedInterval = setInterval(function () {
        if (player.speed < 10) {
            player.speed++;
        }
    }, 5000);

    window.requestAnimationFrame(runGame);

    for (let x = 0; x < 5; x++) {
        let roadLine = document.createElement('div');
        roadLine.setAttribute('class', 'lines');
        roadLine.y = (x * 150);
        roadLine.style.top = roadLine.y + "px";
        gameArea.appendChild(roadLine);
    }

    let car = document.createElement('div');
    car.setAttribute('class', 'myCar');
    gameArea.appendChild(car);

    player.x = car.offsetLeft;
    player.y = car.offsetTop;

    for (let x = 0; x < 3; x++) {
        let enemyCar = document.createElement('div');
        enemyCar.setAttribute('class', 'enemyCar');
        enemyCar.y = ((x + 1) * 350) * -1;
        enemyCar.style.top = enemyCar.y + "px";
        enemyCar.style.left = Math.floor(Math.random() * 350) + "px";
        gameArea.appendChild(enemyCar);
    }
}
</code></pre>
<h2>Installation</h2>
    <ol>
        <li>Clone the repository or download the files.</li>
        <li>Open <code>index.html</code> in your web browser to start the game.</li>
    </ol>
