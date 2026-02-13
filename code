<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Game Hub</title>
    <style>
        /* CSS Styles */
        body { 
            font-family: Arial, sans-serif; 
            margin: 0; 
            padding: 0; 
            background: #f0f0f0; 
        }
        header { 
            text-align: center; 
            padding: 20px; 
            background: #4CAF50; 
            color: white; 
        }
        .game-grid { 
            display: grid; 
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); 
            gap: 20px; 
            padding: 20px; 
        }
        .game-card { 
            background: white; 
            border-radius: 8px; 
            padding: 10px; 
            text-align: center; 
            cursor: pointer; 
            box-shadow: 0 2px 5px rgba(0,0,0,0.1); 
            transition: transform 0.2s;
        }
        .game-card:hover {
            transform: scale(1.05);
        }
        .game-card img { 
            width: 100%; 
            height: 150px; 
            object-fit: cover; 
            border-radius: 4px;
        }
        #game-container { 
            text-align: center; 
            padding: 20px; 
        }
        canvas { 
            border: 2px solid #333; 
            background: #fff;
            display: block;
            margin: 20px auto;
            cursor: crosshair;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            background: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            margin-bottom: 10px;
        }
        button:hover {
            background: #45a049;
        }
    </style>
</head>
<body>

    <header id="main-header">
        <h1>Welcome to Game Hub</h1>
        <p>Play different types of games!</p>
    </header>

    <main>
        <div class="game-grid">
            <div class="game-card" onclick="loadGame('tictactoe')">
                <img src="https://via.placeholder.com/200x150?text=Tic-Tac-Toe" alt="Tic-Tac-Toe">
                <h3>Tic-Tac-Toe</h3>
            </div>
            <div class="game-card" onclick="loadGame('snake')">
                <img src="https://via.placeholder.com/200x150?text=Snake" alt="Snake">
                <h3>Snake</h3>
            </div>
        </div>

        <div id="game-container" style="display: none;">
            <button onclick="backToMenu()">Back to Menu</button>
            <canvas id="game-canvas"></canvas>
        </div>
    </main>

    <script>
        function loadGame(gameType) {
            // UI Transitions
            document.querySelector('.game-grid').style.display = 'none';
            document.getElementById('main-header').style.display = 'none';
            document.getElementById('game-container').style.display = 'block';

            const canvas = document.getElementById('game-canvas');
            const ctx = canvas.getContext('2d');
            canvas.width = 300;
            canvas.height = 300;

            if (gameType === 'tictactoe') {
                let board = Array(9).fill(null);
                let currentPlayer = 'X';

                // Handle Clicks
                canvas.onclick = (e) => {
                    const rect = canvas.getBoundingClientRect();
                    const x = Math.floor((e.clientX - rect.left) / 100);
                    const y = Math.floor((e.clientY - rect.top) / 100);
                    const index = y * 3 + x;

                    if (index >= 0 && index < 9 && !board[index]) {
                        board[index] = currentPlayer;
                        drawBoard();
                        currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
                    }
                };

                function drawBoard() {
                    ctx.clearRect(0, 0, 300, 300);
                    
                    // Draw Grid Lines
                    ctx.strokeStyle = '#333';
                    ctx.lineWidth = 2;
                    ctx.beginPath();
                    for (let i = 1; i < 3; i++) {
                        ctx.moveTo(i * 100, 0);
                        ctx.lineTo(i * 100, 300);
                        ctx.moveTo(0, i * 100);
                        ctx.lineTo(300, i * 100);
                    }
                    ctx.stroke();

                    // Draw X and O
                    ctx.font = 'bold 48px Arial';
                    ctx.textAlign = 'center';
                    ctx.textBaseline = 'middle';
                    
                    board.forEach((mark, i) => {
                        if (mark) {
                            const x = (i % 3) * 100 + 50;
                            const y = Math.floor(i / 3) * 100 + 50;
                            ctx.fillStyle = mark === 'X' ? '#e74c3c' : '#3498db';
                            ctx.fillText(mark, x, y);
                        }
                    });
                }
                drawBoard();

            } else if (gameType === 'snake') {
                // Placeholder for Snake logic
                ctx.fillStyle = "#333";
                ctx.textAlign = "center";
                ctx.fillText("Snake Game Coming Soon!", 150, 150);
            }
        }

        function backToMenu() {
            document.getElementById('game-container').style.display = 'none';
            document.getElementById('main-header').style.display = 'block';
            document.querySelector('.game-grid').style.display = 'grid';
            
            // Clear the canvas when leaving
            const canvas = document.getElementById('game-canvas');
            canvas.onclick = null; 
        }
    </script>
</body>
</html>
