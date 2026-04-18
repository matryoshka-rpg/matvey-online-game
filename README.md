Моя первая игра
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>Matvey Online Game</title>
  <style>
    body {
      margin: 0;
      background: #111;
      color: white;
      font-family: Arial;
      overflow: hidden;
    }

    #menu {
      position: absolute;
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }

    button {
      padding: 15px 30px;
      font-size: 20px;
      cursor: pointer;
    }

    #game {
      display: none;
    }

    canvas {
      background: #222;
      display: block;
      margin: auto;
    }
  </style>
</head>
<body>

<div id="menu">
  <h1>🎮 Моя первая игра</h1>
  <button onclick="startGame()">Играть</button>
</div>

<div id="game">
  <canvas id="canvas" width="800" height="500"></canvas>
</div>

<script>
let canvas, ctx;
let x = 100;
let y = 100;
let speed = 5;

function startGame() {
  document.getElementById("menu").style.display = "none";
  document.getElementById("game").style.display = "block";

  canvas = document.getElementById("canvas");
  ctx = canvas.getContext("2d");

  document.addEventListener("keydown", move);

  gameLoop();
}

function move(e) {
  if (e.key === "w") y -= speed;
  if (e.key === "s") y += speed;
  if (e.key === "a") x -= speed;
  if (e.key === "d") x += speed;
}

function gameLoop() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  // игрок
  ctx.fillStyle = "red";
  ctx.fillRect(x, y, 30, 30);

  requestAnimationFrame(gameLoop);
}
</script>

</body>
</html>