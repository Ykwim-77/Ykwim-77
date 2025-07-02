# olá, bem vindo ao meu perfil


## **Faço parte do aprender e crescer 2025**


Linguagens que eu já trabalhei:

- **Python**


- **HTML**


- **C**


- **CSS**


- **Java Script**'


### Estudo no colégio civíco militar leonardo da vinci

# META DE VIDA
## deixar o gustavo sem opala

<!-- Snake Game - Dev Languages Edition -->
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Snake Game - Dev Languages Edition</title>
    <style>
        /* Layout básico */
        body {
            margin: 0;
            background: #111;
            color: #fff;
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        h1 {
            margin-top: 20px;
            font-size: 1.8rem;
            text-align: center;
        }
        canvas {
            background: #000;
            border: 3px solid #444;
            margin-top: 20px;
        }
        #score {
            margin-top: 10px;
            font-size: 1.2rem;
        }
        p {
            margin-top: 10px;
            text-align: center;
            line-height: 1.4;
            max-width: 320px;
        }
    </style>
</head>
<body>
    <h1>Snake 🍝 Dev Languages Edition</h1>
    <canvas id="game" width="400" height="400"></canvas>
    <div id="score">Score: 0</div>

    <script>
    // --- Configurações ---
    const canvas = document.getElementById('game');
    const ctx = canvas.getContext('2d');
    const gridSize = 20; // tamanho de cada bloco em pixels
    const tileCount = canvas.width / gridSize; // 20x20

    let snake = [{ x: 10, y: 10 }];
    let velocity = { x: 0, y: 0 };
    let score = 0;

    // Ícones das linguagens (emoji ou símbolos simples)
    const foods = [
        { label: '🐍', name: 'Python' },
        { label: '📄', name: 'HTML' },
        { label: '🎨', name: 'CSS' },
        { label: '🅲', name: 'C' },
        { label: '🟨', name: 'JS' }
    ];

    let food = randomFood();

    // Gera uma posição aleatória para a comida
    function randomFood() {
        const pos = {
            x: Math.floor(Math.random() * tileCount),
            y: Math.floor(Math.random() * tileCount)
        };
        const item = foods[Math.floor(Math.random() * foods.length)];
        return { ...pos, ...item }; // {x, y, label, name}
    }

    // Controle pelo teclado
    document.addEventListener('keydown', (e) => {
        switch (e.key) {
            case 'ArrowUp':
                if (velocity.y === 0) velocity = { x: 0, y: -1 };
                break;
            case 'ArrowDown':
                if (velocity.y === 0) velocity = { x: 0, y: 1 };
                break;
            case 'ArrowLeft':
                if (velocity.x === 0) velocity = { x: -1, y: 0 };
                break;
            case 'ArrowRight':
                if (velocity.x === 0) velocity = { x: 1, y: 0 };
                break;
        }
    });

    let frame = 0; // para desacelerar o jogo

    function gameLoop() {
        requestAnimationFrame(gameLoop);

        if (++frame % 6 !== 0) return; // ajusta velocidade

        // --- Atualiza posição ---
        const head = {
            x: (snake[0].x + velocity.x + tileCount) % tileCount,
            y: (snake[0].y + velocity.y + tileCount) % tileCount
        };
        snake.unshift(head);

        // --- Comeu a comida? ---
        if (head.x === food.x && head.y === food.y) {
            score++;
            document.getElementById('score').innerText = 'Score: ' + score;
            food = randomFood();
        } else {
            snake.pop(); // remove o último segmento se não comer
        }

        // --- Colisão com o corpo ---
        for (let i = 1; i < snake.length; i++) {
            if (snake[i].x === head.x && snake[i].y === head.y) {
                // Reinicia o jogo
                snake = [{ x: 10, y: 10 }];
                velocity = { x: 0, y: 0 };
                score = 0;
                document.getElementById('score').innerText = 'Score: 0';
                break;
            }
        }

        // --- Renderização ---
        ctx.fillStyle = '#000';
        ctx.fillRect(0, 0, canvas.width, canvas.height);

        // Cobra
        ctx.fillStyle = '#0f0';
        snake.forEach(seg => {
            ctx.fillRect(seg.x * gridSize, seg.y * gridSize, gridSize - 2, gridSize - 2);
        });

        // Comida (emoji)
        ctx.font = gridSize + 'px Arial';
        ctx.textAlign = 'center';
        ctx.textBaseline = 'middle';
        ctx.fillStyle = '#fff';
        ctx.fillText(food.label, food.x * gridSize + gridSize / 2, food.y * gridSize + gridSize / 2);
    }

    gameLoop();
    </script>

    <p>
        Use as <strong>setas do teclado</strong> para mover a cobrinha.<br>
        Coma todas as linguagens! 🐍📄🎨🅲🟨
    </p>
</body>
</html>
