<!DOCYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Teddy Bear</title>
        <style>
            body{background-color: #004d00}
            canvas{display: block; margin: auto}
        </style>
    </head>
    <body>
        <canvas id="myCanvas" width="1200" height="600"></canvas>
        <script>
            const c = document.getElementById('myCanvas');
            const ctx = c.getContext('2d');
            ctx.scale(4,4);
            
            let dropCounter = 0;
            let dropInterval = 1000;
            let lastTime = 0;
            
            var imageDemonObj = new Image();
            imageDemonObj.src = 'gamesImages/demon.png'
            
            var imageLifeObj = new Image();
            imageLifeObj.src = 'gamesImages/heartlife.png'
            
            var demonWidth = 24;
            var demonHeight = 24;
            var demonXpos = 50;
            var demonYpos = 2;
            var demonXSpeed = 0;
            var demonArray = [];
            
            var lifeWidth = 24;
            var lifeHeight = 24;
            var lifeXpos = 170;
            var lifeYpos = 0;
            var counter = 0;
            var lifeArray = [];
            
            var stop = true;
            
            var hard = prompt("Which difficult do you want? \n Press 1 for easy \n Press 2 for medium \n Press 3 for hard \n Press 4 for impossible");
            
            if(hard == '1'){
                demonXSpeed = 0.5;
            } else if(hard == '2'){
                demonXSpeed = 0.75;
            } else if(hard == '3'){
                demonXSpeed = 1;
            } else if(hard == '4'){
                demonXSpeed = 1.5;
            } else {
                alert("Press F5 and give an acceptable value");
            }
            
            for(i=0; i<2; i++){
                demonArray.push(randDemon());
            }
            
            for(i=0; i<3; i++){
                    lifeArray.push(randLife());
            }
            
            function demonRender(){
                demonArray.forEach(function(demon,index){
                    ctx.drawImage(imageDemonObj,demon.demonXpos,demon.demonYpos-4,demon.demonWidth+8,demon.demonHeight+8);
                });
            }
            
            function lifeRender(){
                lifeArray.forEach(function(life,index){
                    ctx.drawImage(imageLifeObj,life.lifeXpos,life.lifeYpos,life.lifeWidth,life.lifeHeight);
                });
            }  
            
            function randDemon(){
                demonWidth = demonWidth;
                demonHeight = demonHeight;
                demonXSpeed = demonXSpeed;
                demonYpos += 60;
                var randDemonObject = {
                    demonWidth: demonWidth,
                    demonHeight: demonHeight,
                    demonXpos: Math.floor(Math.random() * (132) + 72),
                    demonYpos: demonYpos,
                    demonXSpeed: demonXSpeed,
                }
                return randDemonObject;
            }
            
            function randLife(){
                lifeWidth = 24;
                lifeHeight = 24;
                lifeXpos += 30;
                lifeYpos = 3;
                var randLifeObject = {
                    lifeWidth: lifeWidth,
                    lifeHeight: lifeHeight,
                    lifeXpos: lifeXpos,
                    lifeYpos: lifeYpos,
                }
                return randLifeObject;
            }
            
            function demonMove(){
                demonArray.forEach(function(demon,index){ 
                    demon.demonXpos += demon.demonXSpeed;
                    
                    if(demon.demonXpos > 258 - demon.demonWidth){
                        demon.demonXSpeed *= -1;
                    }
                    if(demon.demonXpos < 42){
                        demon.demonXSpeed *= -1;
                    }
                    if(demon.demonXpos > player.pos.x - 24 && demon.demonXpos < player.pos.x + 24 && demon.demonYpos > player.pos.y - 24 && demon.demonYpos < player.pos.y + 24){
                        counter += 1;
                        console.log(counter);
                        player.pos.x = 4;
                        player.pos.y = 124;
                    }
                });
            }
            
            document.addEventListener('keydown', event => {
                //Movement y axis
                
                if(player.pos.x < 16 && player.pos.y > 86){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 100){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 22 && player.pos.x >= 16 && player.pos.y > 86){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 88){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 64 && player.pos.x >= 22 && player.pos.y > 86){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 100){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 70 && player.pos.x >= 64 && player.pos.y > 86){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 88){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 112 && player.pos.x >= 70 && player.pos.y > 86){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 100){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 118 && player.pos.x >= 112 && player.pos.y > 86){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 88){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 160 && player.pos.x >= 118 && player.pos.y > 86){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 100){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 166 && player.pos.x >= 160 && player.pos.y > 86){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 88){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 208 && player.pos.x >= 166 && player.pos.y > 86){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 100){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 214 && player.pos.x >= 208 && player.pos.y > 86){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 88){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 256 && player.pos.x >= 214 && player.pos.y > 86){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 100){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 262 && player.pos.x >= 256 && player.pos.y > 66){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 30){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 300 && player.pos.x >= 262 && player.pos.y >= 100){
                    if(event.keyCode == 83 && player.pos.y < 126){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 100){
                        player.pos.y -= 2;
                    }
                }
                
                // Second Movement y axis
                
                if(player.pos.x < 16 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 40){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 22 && player.pos.x >= 16 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 2){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 64 && player.pos.x >= 22 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 40){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 70 && player.pos.x >= 64 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 30){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 112 && player.pos.x >= 70 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 40){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 118 && player.pos.x >= 112 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 30){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 160 && player.pos.x >= 118 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 40){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 166 && player.pos.x >= 160 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 30){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 208 && player.pos.x >= 166 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 40){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 214 && player.pos.x >= 208 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 30){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 256 && player.pos.x >= 214 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 40){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 262 && player.pos.x >= 256 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 30){
                        player.pos.y -= 2;
                    }
                }
                if(player.pos.x < 300 && player.pos.x >= 262 && player.pos.y <= 66 && player.pos.y > 6){
                    if(event.keyCode == 83 && player.pos.y < 66){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 40){
                        player.pos.y -= 2;
                    }
                }
                
                // Movement x axis
                
                if(player.pos.y > 98){
                    if(event.keyCode == 65 && player.pos.x > 2){
                        player.pos.x -= 2;
                    } else if(event.keyCode == 68 && player.pos.x < 274){
                        player.pos.x += 2;
                    }
                }
                if(player.pos.y <= 66 && player.pos.y > 38){
                    if(event.keyCode == 65 && player.pos.x > 2){
                        player.pos.x -= 2;
                    } else if(event.keyCode == 68 && player.pos.x < 274){
                        player.pos.x += 2;
                    }
                }
                if(player.pos.y <= 6){
                    if(event.keyCode == 65 && player.pos.x > 2){
                        player.pos.x -= 2;
                    } else if(event.keyCode == 68 && player.pos.x < 164){
                        player.pos.x += 2;
                    } else if(event.keyCode == 83 && player.pos.y < 6){
                        player.pos.y += 2;
                    } else if(event.keyCode == 87 && player.pos.y > 2){
                        player.pos.y -= 2;
                    }
                }
            });
            
            function drawWalls(){
                if(player.pos.y <= 6){
                    ctx.beginPath();
                    ctx.rect(18,30,24,12);
                    ctx.fillStyle = '#802b00';
                    ctx.fill();
                    ctx.closePath();
                    ctx.beginPath();
                    ctx.rect(18,48,24,12);
                    ctx.fillStyle = '#00b300';
                    ctx.fill();
                    ctx.closePath();
                }
                if(player.pos.y > 6 && player.pos.y < 68){
                    ctx.beginPath();
                    ctx.rect(258,90,24,12);
                    ctx.fillStyle = '#802b00';
                    ctx.fill();
                    ctx.closePath();
                    ctx.beginPath();
                    ctx.rect(258,108,24,12);
                    ctx.fillStyle = '#00b300';
                    ctx.fill();
                    ctx.closePath();
                }
            }
            
            function win(){
                if(player.pos.y <= 6 && player.pos.x >= 150){
                    ctx.font = "40px Verdana";
                    ctx.fillStyle = "white";
                    ctx.fillText("YOU WON!",40,89.5);
                }
            }
            
            var mapHeight = 25;
            var mapWidth = 50;
            var tileHeight = 6;
            var tileWidth = 6;
            
            var gameMap = [
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,5,4,5,4,5,4,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,4,5,4,5,4,5,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,5,4,5,4,5,4,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,4,5,4,5,4,5,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,5,4,5,4,5,4,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                1,1,1,0,0,0,0,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,
                1,1,1,0,0,0,0,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,
                1,1,1,0,0,0,0,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,
                2,2,2,3,3,3,3,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,
                2,2,2,3,3,3,3,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,0,0,0,0,1,1,1,
                1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,0,0,0,0,1,1,1,
                1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,2,2,2,2,1,1,1,1,0,0,0,0,1,1,1,
                2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,3,3,3,3,2,2,2,
                2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,0,0,0,0,2,2,2,2,3,3,3,3,2,2,2,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
            ]
            
            function drawBase(){
                for(var y = 0; y < mapHeight; y++){
                    for(var x = 0; x < mapWidth; x++){
                        switch(gameMap[((y*mapWidth)+x)]){
                            case 0:
                                ctx.fillStyle = '#00b300';
                                break
                            case 1:
                                ctx.fillStyle = '#004d00';
                                break
                            case 2:
                                ctx.fillStyle = '#003300';
                                break
                            case 3:
                                ctx.fillStyle = '#802b00';
                                break  
                            case 4:
                                ctx.fillStyle = 'white';
                                break
                            case 5:
                                ctx.fillStyle = 'black';
                                break
                        }
                        ctx.fillRect(x*tileWidth,y*tileHeight,tileWidth,tileHeight);
                    }
                }
            }
            
            const matrix = [
                [0,1,1,1,0,0,0,0,1,1,1,1,1,1,1,1,0,0,0,0,1,1,1,0,],
                [1,1,2,2,1,0,1,1,2,2,2,2,2,2,2,2,1,1,0,1,2,2,1,1,],
                [1,3,1,2,2,1,2,2,2,2,2,2,2,2,2,2,2,2,1,2,2,1,3,1,],
                [1,3,3,1,1,2,2,2,2,2,2,2,2,2,2,2,2,2,2,1,1,3,3,1,],
                [1,3,3,1,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,1,3,3,1,],
                [0,1,1,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,1,1,0,],
                [0,0,1,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,1,0,0,],
                [0,0,1,2,2,1,4,2,2,3,3,3,3,3,3,2,2,4,1,2,2,1,0,0,],
                [0,0,1,2,2,1,1,2,3,3,1,1,1,1,3,3,2,1,1,2,2,1,0,0,],
                [0,0,1,2,2,2,2,2,3,3,3,3,3,3,3,3,2,2,2,2,2,1,0,0,],
                [0,0,0,1,2,2,2,2,3,3,3,3,3,3,3,3,2,2,2,2,1,0,0,0,],
                [0,0,0,0,1,2,2,2,2,3,3,3,3,3,3,2,2,2,2,1,0,0,0,0,],
                [0,0,0,0,0,1,1,1,1,1,1,1,1,1,1,1,1,1,1,0,0,0,0,0,],
                [0,0,0,1,1,2,2,2,2,2,2,2,2,2,2,2,2,2,2,1,1,0,0,0,],
                [0,0,1,2,2,2,2,2,2,3,3,3,3,3,3,2,2,2,2,2,2,1,0,0,],
                [0,0,1,2,2,1,2,2,3,3,3,3,3,3,3,3,2,2,1,2,2,1,0,0,],
                [0,0,0,1,1,1,2,2,3,3,3,3,3,3,3,3,2,2,1,1,1,0,0,0,],
                [0,0,0,0,0,1,2,2,3,3,3,3,3,3,3,3,2,2,1,0,0,0,0,0,],
                [0,0,0,0,0,1,2,2,2,3,3,3,3,3,3,2,2,2,1,0,0,0,0,0,],
                [0,0,0,0,0,1,2,2,2,2,2,2,2,2,2,2,2,2,1,0,0,0,0,0,],
                [0,0,0,0,0,1,2,2,1,1,1,1,1,1,1,1,2,2,1,0,0,0,0,0,],
                [0,0,0,0,0,0,1,1,1,0,0,0,0,0,0,1,1,1,0,0,0,0,0,0,],
                [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,],
                [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,],
            ]
            
            function drawMatrix(matrix,offset){
                matrix.forEach((row,y) => {
                    row.forEach((value,x) => {
                        if(value == 1){
                            ctx.fillStyle = 'black';
                            ctx.fillRect(x + offset.x,y + offset.y,1,1);
                        }
                        if(value == 2){
                            ctx.fillStyle = '#663300';
                            ctx.fillRect(x + offset.x,y + offset.y,1,1);
                        }
                        if(value == 3){
                            ctx.fillStyle = '#b37700';
                            ctx.fillRect(x + offset.x,y + offset.y,1,1);
                        }
                        if(value == 4){
                            ctx.fillStyle = 'white';
                            ctx.fillRect(x + offset.x,y + offset.y,1,1);
                        }
                    });
                }); 
            }
            
            function deleteLife(){
                if(counter >= 1){
                    ctx.beginPath();
                    ctx.rect(260,3,24,24);
                    ctx.fillStyle = '#00b300';
                    ctx.fill();
                    ctx.closePath();
                }
                if(counter >= 2){
                    ctx.beginPath();
                    ctx.rect(230,3,24,24);
                    ctx.fillStyle = '#00b300';
                    ctx.fill();
                    ctx.closePath();
                }
                if(counter >= 3){
                    ctx.beginPath();
                    ctx.rect(200,3,24,24);
                    ctx.fillStyle = '#00b300';
                    ctx.fill();
                    ctx.closePath();
                }
                if(counter >= 4){
                    ctx.font = "40px Verdana";
                    ctx.fillStyle = "white";
                    ctx.fillText("YOU LOST!",36,89.5);
                    stop = false;
                }
            }
            
            function update(time = 0){
                const deltaTime = time - lastTime;
                lastTime = time;
                dropCounter += deltaTime;
                if(dropCounter > dropInterval){
                    dropCounter = 0;
                }
                draw();
                requestAnimationFrame(update);
            }
            
            function draw(){
                if(stop){
                    ctx.clearRect(0,0,c.width,c.height);
                    drawBase();
                    drawMatrix(player.matrix,player.pos);
                    demonRender();
                    randDemon();
                    demonMove();
                    lifeRender();
                    randLife();
                    deleteLife();
                    drawWalls();
                    win();
                }
             }
            
            const player = {
                pos: {x:4,y:124},
                matrix: matrix,   
            }
            
            update();
        </script>
    </body>
</html>
