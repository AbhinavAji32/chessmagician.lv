
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Web Chess Game</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/chessboardjs@1.0.0/dist/chessboard.min.css">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Chess Game</h1>
  <div id="board" style="width: 400px"></div>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/chess.js/0.13.4/chess.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chessboardjs@1.0.0/dist/chessboard.min.js"></script>
  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 40px;
  background-color: #f0f0f0;
}
const game = new Chess();

const board = Chessboard('board', {
  draggable: true,
  position: 'start',
  onDrop: function (source, target) {
    const move = game.move({
      from: source,
      to: target,
      promotion: 'q' // Always promote to a queen for simplicity
    });

    if (move === null) return 'snapback';
  },
  onSnapEnd: function () {
    board.position(game.fen());
  }
});
