
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Surprise 🎉</title>

<style>
body{
    margin:0;
    font-family:'Segoe UI', sans-serif;
    background:linear-gradient(135deg,#ff758c,#ff7eb3);
    text-align:center;
    color:white;
    overflow:hidden;
}

/* Heading Glow */
h1{
    margin-top:60px;
    font-size:50px;
    animation:glow 1.5s infinite alternate;
}
@keyframes glow{
    from{ text-shadow:0 0 10px #fff;}
    to{ text-shadow:0 0 25px yellow;}
}

/* Card */
.card{
    background:rgba(255,255,255,0.2);
    margin:30px auto;
    padding:30px;
    width:400px;
    border-radius:20px;
    backdrop-filter:blur(10px);
}

/* Button */
button{
    padding:12px 20px;
    border:none;
    border-radius:25px;
    font-size:16px;
    cursor:pointer;
    margin:10px;
    background:#ff4081;
    color:white;
    transition:0.3s;
}
button:hover{
    transform:scale(1.1);
    background:#f50057;
}

/* Hidden Sections */
.hidden{
    display:none;
    margin-top:20px;
    font-size:18px;
    animation:fadeIn 1.5s forwards;
}
@keyframes fadeIn{
    from{opacity:0;}
    to{opacity:1;}
}

/* Cake */
.cake{
    margin:30px auto;
    position:relative;
    width:200px;
    height:150px;
}
.layer{
    background:#ffb347;
    height:50px;
    border-radius:10px;
    margin-top:5px;
}
.candle{
    width:10px;
    height:40px;
    background:white;
    position:absolute;
    top:-40px;
    left:95px;
}
.flame{
    width:15px;
    height:15px;
    background:orange;
    border-radius:50%;
    position:absolute;
    top:-55px;
    left:92px;
    animation:flicker 0.2s infinite alternate;
}
@keyframes flicker{
    from{transform:scale(1);}
    to{transform:scale(1.2);}
}

/* Canvas */
canvas{
    position:fixed;
    top:0;
    left:0;
    pointer-events:none;
}
</style>
</head>

<body>

<h1>🎉 Happy Birthday RUHINA! 🎂</h1>

<div class="card">
    <p>Today is your day. Let’s make it unforgettable!</p>

    <button onclick="playMusic()">🎵 Play Music</button>
    <button onclick="showRomantic()">🎉 Message</button>
    <button onclick="showFunny()">😂 Funny Roast</button>
    <button onclick="blowCandle()">🎂 Blow Candle</button>

    <div id="romantic" class="hidden">
        💖 You are not just a year older, but a year more amazing, inspiring, and unforgettable. The world shines brighter because you're in it.
    </div>

    <div id="funny" class="hidden">
        😂 Congrats! You're now officially at the age where your back goes out more than you do. But hey… at least you're still younger than next year!
    </div>
</div>

<!-- Cake -->
<div class="cake">
    <div class="flame" id="flame"></div>
    <div class="candle"></div>
    <div class="layer"></div>
    <div class="layer"></div>
    <div class="layer"></div>
</div>

<!-- Background Music -->
<audio id="music" loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<!-- Confetti Canvas -->
<canvas id="confetti"></canvas>

<script>
/* Music */
function playMusic(){
    document.getElementById("music").play();
}

/* Messages */
function showRomantic(){
    document.getElementById("romantic").style.display="block";
}
function showFunny(){
    document.getElementById("funny").style.display="block";
}

/* Blow Candle */
function blowCandle(){
    document.getElementById("flame").style.display="none";
}

/* Confetti */
const canvas=document.getElementById("confetti");
const ctx=canvas.getContext("2d");
canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

let pieces=[];
for(let i=0;i<120;i++){
    pieces.push({
        x:Math.random()*canvas.width,
        y:Math.random()*canvas.height,
        size:Math.random()*8+2,
        speed:Math.random()*3+1,
        color:`hsl(${Math.random()*360},100%,50%)`
    });
}

function drawConfetti(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    pieces.forEach(p=>{
        ctx.fillStyle=p.color;
        ctx.fillRect(p.x,p.y,p.size,p.size);
        p.y+=p.speed;
        if(p.y>canvas.height){p.y=0;}
    });
    requestAnimationFrame(drawConfetti);
}
drawConfetti();
</script>

</body>
</html>
