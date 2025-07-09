<!DOCTYPE html>
<html>
<head>
  <title>Tap the Color!</title>
  <style>
    body { text-align: center; font-family: sans-serif; }
    #colorBox {
      width: 200px; height: 200px;
      margin: 30px auto;
      background-color: red;
      border-radius: 15px;
      transition: background-color 0.3s;
    }
    button {
      font-size: 20px;
      padding: 10px 20px;
      margin-top: 20px;
    }
  </style>
</head>
<body>

<h1>🎨 Tap the Color!</h1>
<p>Tap the box when it turns green!</p>
<div id="colorBox"></div>
<button onclick="startGame()">Start</button>
<p id="result"></p>

<script>
  let colorBox = document.getElementById('colorBox');
  let resultText = document.getElementById('result');
  let startTime, endTime;

  function startGame() {
    resultText.innerText = '';
    colorBox.style.backgroundColor = 'red';
    let delay = Math.random() * 3000 + 1000;

    setTimeout(() => {
      colorBox.style.backgroundColor = 'green';
      startTime = new Date().getTime();
    }, delay);

    colorBox.onclick = function () {
      endTime = new Date().getTime();
      if (colorBox.style.backgroundColor === 'green') {
        let reactionTime = (endTime - startTime) / 1000;
        resultText.innerText = `⏱ Good job! Your time: ${reactionTime}s`;
      } else {
        resultText.innerText = "❌ Too early! Wait for green.";
      }
    }
  }
</script>

</body>
</html>
