<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Endless Runner Game</title>
    <style>
        /* CSS will go here */
    </style>
</head>
<body>
    <div id="gameArea">
        <div id="player"></div>
        <div id="obstacle"></div>
    </div>
    <script>
        // JavaScript will go here
    </script>
</body>
</html>
body {
    margin: 0;
    overflow: hidden;
    background-color: #f0f0f0;
}

#gameArea {
    width: 100%;
    height: 100vh;
    position: relative;
    background-color: #87CEEB;
}

#player {
    width: 50px;
    height: 50px;
    background-color: red;
    position: absolute;
    bottom: 20px;
    left: 50px;
    border-radius: 10px;
}

#obstacle {
    width: 50px;
    height: 50px;
    background-color: green;
    position: absolute;
    bottom: 20px;
    right: 0;
    animation: moveObstacle 2s linear infinite;
}

@keyframes moveObstacle {
    from {
        right: 0;
    }
    to {
        right: 100%;
    }
}
let player = document.getElementById('player');
let obstacle = document.getElementById('obstacle');
let gameArea = document.getElementById('gameArea');

document.addEventListener('keydown', function(event) {
    if (event.key === 'ArrowUp') {
        jump();
    }
});

function jump() {
    if (player.classList != 'jump') {
        player.classList.add('jump');
    }
    setTimeout(function() {
        player.classList.remove('jump');
    }, 500);
}

let isAlive = setInterval(function() {
    let playerTop = parseInt(window.getComputedStyle(player).getPropertyValue('top'));
    let obstacleLeft = parseInt(window.getComputedStyle(obstacle).getPropertyValue('left'));

    if (obstacleLeft < 100 && obstacleLeft > 0 && playerTop >= 130) {
        alert('Game Over!');
    }
}, 10);

#player.jump {
    animation: jump 0.5s;
}

@keyframes jump {
    0% {
        bottom: 20px;
    }
    50% {
        bottom: 150px;
    }
    100% {
        bottom: 20px;
    }
}
