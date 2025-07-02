# olá, bem vindo ao meu perfil


## **Faço parte do aprender e crescer 2025**


Linguagens que eu já trabalhei:

- **Python**


- **HTML**


- **C**


- **CSS**


- **Java Script**'


### Estudo no colégio civíco militar leonardo da vinci
<!-- Snake Game - Dev Languages Edition -->
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>Snake Game - Dev Languages Edition</title>
  <style>
    body{
      margin:0;
      background:#111;
      color:#fff;
      font-family:Arial, sans-serif;
      display:flex;
      flex-direction:column;
      align-items:center;
    }
    h1{margin-top:20px;font-size:1.8rem;text-align:center;}
    canvas{background:#000;border:3px solid #444;margin-top:20px;}
    #score{margin-top:10px;font-size:1.2rem;}
    p{margin-top:10px;text-align:center;line-height:1.4;max-width:320px;}
  </style>
</head>
<body>
  <h1>Snake 🐍 Dev Languages Edition</h1>
  <canvas id="game" width="400" height="400"></canvas>
  <div id="score">Score: 0</div>

  <script>
  const canvas=document.getElementById('game');
  const ctx=canvas.getContext('2d');
  const gridSize=20;
  const tile=canvas.width/gridSize;
  let snake=[{x:10,y:10}],vel={x:0,y:0},score=0;

  const foods=[
    {label:'🐍',name:'Python'},
    {label:'📄',name:'HTML'},
    {label:'🎨',name:'CSS'},
    {label:'🅲',name:'C'},
    {label:'🟨',name:'JS'}
  ];
  let food=randomFood();

  function randomFood(){
    return{
      x:Math.floor(Math.random()*tile),
      y:Math.floor(Math.random()*tile),
      ...foods[Math.floor(Math.random()*foods.length)]
    };
  }

  document.addEventListener('keydown',e=>{
    if(e.key==='ArrowUp'   && vel.y===0)vel={x:0,y:-1};
    if(e.key==='ArrowDown' && vel.y===0)vel={x:0,y: 1};
    if(e.key==='ArrowLeft' && vel.x===0)vel={x:-1,y:0};
    if(e.key==='ArrowRight'&& vel.x===0)vel={x: 1,y:0};
  });

  let frame=0;
  function loop(){
    requestAnimationFrame(loop);
    if(++frame%6) return;

    const head={x:(snake[0].x+vel.x+tile)%tile,
                y:(snake[0].y+vel.y+tile)%tile};
    snake.unshift(head);

    if(head.x===food.x&&head.y===food.y){
      score++;
      document.getElementById('score').textContent='Score: '+score;
      food=randomFood();
    }else snake.pop();

    for(let i=1;i<snake.length;i++){
      if(snake[i].x===head.x&&snake[i].y===head.y){
        snake=[{x:10,y:10}];vel={x:0,y:0};score=0;
        document.getElementById('score').textContent='Score: 0';
      }
    }

    ctx.fillStyle='#000';ctx.fillRect(0,0,canvas.width,canvas.height);

    ctx.fillStyle='#0f0';
    snake.forEach(s=>ctx.fillRect(s.x*gridSize,s.y*gridSize,gridSize-2,gridSize-2));

    ctx.font=gridSize+'px Arial';
    ctx.textAlign='center';ctx.textBaseline='middle';ctx.fillStyle='#fff';
    ctx.fillText(food.label,food.x*gridSize+gridSize/2,food.y*gridSize+gridSize/2);
  }
  loop();
  </script>

  <p>Use as <strong>setas</strong> do teclado para mover a cobrinha.<br>
     Coma todas as linguagens! 🐍📄🎨🅲🟨</p>
</body>
</html>
