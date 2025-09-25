<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Interactive Vocabulary Exercises</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      padding: 20px;
      background-color: #f9f9f9;
      color: #333;
    }
    h1, h2 {
      color: #222;
    }
    .exercise {
      background: #fff;
      border: 1px solid #ddd;
      border-radius: 8px;
      padding: 15px;
      margin-bottom: 20px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.05);
    }
    ol {
      padding-left: 20px;
    }
    li {
      margin-bottom: 10px;
    }
    input, select {
      padding: 5px;
      margin-left: 5px;
    }
    button {
      margin-top: 10px;
      padding: 8px 15px;
      border: none;
      border-radius: 6px;
      background-color: #0056b3;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background-color: #003d80;
    }
    .correct {
      color: green;
      font-weight: bold;
    }
    .wrong {
      color: red;
      font-weight: bold;
    }
    #score {
      font-size: 1.2em;
      font-weight: bold;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>Interactive Vocabulary Exercises</h1>

  <!-- Exercise 1 -->
  <div class="exercise">
    <h2>Exercise 1: Fill in the Blanks</h2>
    <ol id="fill-blanks">
      <li>The building in the city center is <input type="text" data-answer="huge"></li>
      <li><input type="text" data-answer="as far as I know">, the meeting starts at 10 a.m.</li>
      <li>The movie was over two hours in <input type="text" data-answer="length"></li>
      <li>She ate the entire pizza <input type="text" data-answer="all in one go"></li>
      <li>Citizens have the <input type="text" data-answer="rights"> to vote in elections.</li>
      <li>The concert will take place at a new <input type="text" data-answer="venue"> downtown.</li>
      <li>Different cultures have different <input type="text" data-answer="beliefs"></li>
    </ol>
    <button onclick="checkBlanks()">Check Answers</button>
  </div>

  <!-- Exercise 2 -->
  <div class="exercise">
    <h2>Exercise 2: Match the Words</h2>
    <ol id="match-words">
      <li>Huge 
        <select data-answer="a">
          <option value="">--Choose--</option>
          <option value="a">Very large</option>
          <option value="b">Based on what I understand</option>
          <option value="c">Measurement from beginning to end</option>
        </select>
      </li>
      <li>As far as I know 
        <select data-answer="b">
          <option value="">--Choose--</option>
          <option value="a">Very large</option>
          <option value="b">Based on what I understand</option>
          <option value="c">Measurement from beginning to end</option>
        </select>
      </li>
      <li>Length 
        <select data-answer="c">
          <option value="">--Choose--</option>
          <option value="c">Measurement from beginning to end</option>
          <option value="d">Without stopping</option>
          <option value="e">Things people are legally or morally allowed to do</option>
        </select>
      </li>
      <li>All in one go 
        <select data-answer="d">
          <option value="">--Choose--</option>
          <option value="d">Without stopping</option>
          <option value="f">Place where an event happens</option>
          <option value="g">Ideas or convictions people accept as true</option>
        </select>
      </li>
      <li>Rights 
        <select data-answer="e">
          <option value="">--Choose--</option>
          <option value="e">Things people are legally or morally allowed to do</option>
          <option value="a">Very large</option>
          <option value="b">Based on what I understand</option>
        </select>
      </li>
      <li>Venue 
        <select data-answer="f">
          <option value="">--Choose--</option>
          <option value="f">Place where an event happens</option>
          <option value="g">Ideas or convictions people accept as true</option>
          <option value="c">Measurement from beginning to end</option>
        </select>
      </li>
      <li>Beliefs 
        <select data-answer="g">
          <option value="">--Choose--</option>
          <option value="g">Ideas or convictions people accept as true</option>
          <option value="d">Without stopping</option>
          <option value="f">Place where an event happens</option>
        </select>
      </li>
    </ol>
    <button onclick="checkMatches()">Check Matches</button>
  </div>

  <!-- Exercise 3 -->
  <div class="exercise">
    <h2>Exercise 3: Translate</h2>
    <p>Translate these words into your native language (self-check):</p>
    <ol>
      <li>Huge</li>
      <li>As far as I know</li>
      <li>Length</li>
      <li>All in one go</li>
      <li>Rights</li>
      <li>Venue</li>
      <li>Beliefs</li>
    </ol>
  </div>

  <p id="score">Score: 0 / 14</p>

  <script>
    let totalScore = 0;
    const maxScore = 14;

    function normalize(str) {
      return str.trim().toLowerCase();
    }

    function checkBlanks() {
      let blanks = document.querySelectorAll("#fill-blanks input");
      let score = 0;
      blanks.forEach(input => {
        let user = normalize(input.value);
        let ans = normalize(input.dataset.answer);
        if (user === ans) {
          input.style.borderColor = "green";
          score++;
        } else {
          input.style.borderColor = "red";
        }
      });
      updateScore(score, blanks.length);
    }

    function checkMatches() {
      let selects = document.querySelectorAll("#match-words select");
      let score = 0;
      selects.forEach(sel => {
        let user = sel.value;
        let ans = sel.dataset.answer;
        if (user === ans) {
          sel.style.borderColor = "green";
          score++;
        } else {
          sel.style.borderColor = "red";
        }
      });
      updateScore(score, selects.length);
    }

    function updateScore(sectionScore, sectionMax) {
      totalScore += sectionScore;
      document.getElementById("score").textContent = 
        `Score: ${totalScore} / ${maxScore}`;
    }
  </script>
</body>
</html>
