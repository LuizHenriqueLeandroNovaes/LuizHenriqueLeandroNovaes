### Oi, sou Luiz Novaes 👋


- 🔭Dev Full Stack

<div align-item=center>
 <a href="https://github.com/LuizHenriqueLeandroNovaes">
  <img width="450em" height="180em" src="https://github-readme-stats-sigma-five.vercel.app/api?username=LuizHenriqueLeandroNovaes&show_icons=true&theme=nightowl&include_all_commits=true&count_private=true&custom_title=LuizHenriqueLeandroNovaes%20Roza%20%27s%20GitHub%20Stats"/>
  
</div>
 
 ##
 
 [![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=LuizHenriqueLeandroNovaes)](https://github.com/anuraghazra/github-readme-stats)

##
 
 <h1 align="center"><b>Linguagens de programação</b></h1> <br>

<div align="center">
            <img  height="70em"src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-plain.svg" />
           <img height="70em" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" />
           <img height="70em" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg" />
           <img height="70em" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg" />

</div>
 
 <h1 align="center">Linguagens de marcação</h1> <br>
 
<div align="center">
            <img height="70em" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" />
            <img height="70em" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" />
  </div>
 
 <h1 align="center">Outras tecnologias</h1> <br>
 
 <div align="center">
            <img height="90em"src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original-wordmark.svg" />
            <img height="80em" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/npm/npm-original-wordmark.svg" />
             <img height="60em"src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original-wordmark.svg" />
            <img height="60em" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original-wordmark.svg" />
             <img height="60em" src="https://cdn.iconscout.com/icon/free/png-512/figma-3521426-2944870.png?f=avif&w=256" />  
            <img height="80em" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/arduino/arduino-original-wordmark.svg" />
            <img height="60em" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/canva/canva-original.svg" />
            <img height="60em" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" />
            <img height="60em" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" />
            <img height="60em" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/heroku/heroku-plain-wordmark.svg" />      
</div>

 ##
 
 <h1 align="center">Contato</h1> <br>
 
<div align="center">
    <a href="mailto:henrique.novaes93@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"></a>
    <a href="https://www.linkedin.com/in/luizhnovaes/" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
    <a href="https://www.youtube.com/@magnavideotecaderesolucoes6445/playlists" target="_blank"><img src="https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="YouTube"></a>
    <a href="https://wa.me/5581984418086"><img src="https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp"></a>
</div>

<div style="text-align: center;">
  <canvas id="snakeCanvas" width="400" height="400"></canvas>
</div>

<style>
  body {
    background-color: #1abc9c;
  }
</style>

<script>
  const canvas = document.getElementById('snakeCanvas');
  const ctx = canvas.getContext('2d');

  const squareSize = 20;

  let snake = [{x: 10, y: 10}];
  let direction = 'right';

  let food = {x: Math.floor(Math.random() * 20), y: Math.floor(Math.random() * 20)};

  function drawSnake() {
    ctx.fillStyle = '#2c3e50';
    snake.forEach(square => {
      ctx.fillRect(square.x * squareSize, square.y * squareSize, squareSize, squareSize);
    });
  }

  function moveSnake() {
    const head = {x: snake[0].x, y: snake[0].y};
    switch (direction) {
      case 'right':
        head.x++;
        break;
      case 'left':
        head.x--;
        break;
      case 'up':
        head.y--;
        break;
      case 'down':
        head.y++;
        break;
    }
    snake.unshift(head);
    if (head.x === food.x && head.y === food.y) {
      food = {x: Math.floor(Math.random() * 20), y: Math.floor(Math.random() * 20)};
    } else {
      snake.pop();
    }
  }

  function drawFood() {
    ctx.fillStyle = '#e74c3c';
    ctx.fillRect(food.x * squareSize, food.y * squareSize, squareSize, squareSize);
  }

  function changeDirection(event) {
    const key = event.keyCode;
    switch (key) {
      case 37:
        direction = 'left';
        break;
      case 38:
        direction = 'up';
        break;
      case 39:
        direction = 'right';
        break;
      case 40:
        direction = 'down';
        break;
    }
  }

  function gameOver() {
    clearInterval(gameInterval);
    ctx.fillStyle = '#ffffff';
    ctx.font = '30px Arial';
    ctx.fillText('Game Over', canvas.width/2 - 80, canvas.height/2 - 10);
  }

  function collisionDetection() {
    const head = snake[0];
    if (head.x < 0 || head.x >= canvas.width/squareSize || head.y < 0 || head.y >= canvas.height/squareSize) {
      gameOver();
    }
    for (let i = 1; i < snake.length; i++) {
      if (head.x === snake[i].x && head.y === snake[i].y) {
        gameOver();
      }
    }
  }

  function gameLoop() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawSnake();
    drawFood();
    moveSnake();
    collisionDetection();
  }

  document.addEventListener('keydown', changeDirection);

  const gameInterval = setInterval(gameLoop, 100);
</script>




 
            



