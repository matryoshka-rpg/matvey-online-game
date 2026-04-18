Моя первая игра
<script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>

<script>
const socket = io("URL_СЕРВЕРА");

let players = {};

socket.on("players", (data) => {
  players = data;
});

function sendMove(x, y) {
  socket.emit("move", { x, y });
}
</script>

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

  sendMove(x, y); // 👈 ВАЖНО ДЛЯ ОНЛАЙНА
}

function gameLoop() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  ctx.fillStyle = "red";
  ctx.fillRect(x, y, 30, 30);

  requestAnimationFrame(gameLoop);
}
</script>
