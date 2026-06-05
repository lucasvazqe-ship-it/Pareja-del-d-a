<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>❤️ Manel & Julia Torrado ❤️</title>

<meta name="description" content="Web romántica interactiva con Manel y Julia Torrado: amor, juegos, chat y efectos visuales.">

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600;700&family=Dancing+Script:wght@700&display=swap" rel="stylesheet">

<style>

*{margin:0;padding:0;box-sizing:border-box;}

body{
font-family:Poppins,sans-serif;
background:linear-gradient(-45deg,#ff4d6d,#ff758f,#ffb3c1,#ffd6e0);
background-size:400% 400%;
animation:bg 10s ease infinite;
color:white;
overflow-x:hidden;
}

@keyframes bg{
0%{background-position:0% 50%}
50%{background-position:100% 50%}
100%{background-position:0% 50%}
}

/* LOGIN */
#login{
position:fixed;
inset:0;
background:black;
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
z-index:9999;
}

#login h1{
font-family:Dancing Script;
font-size:3rem;
}

#login input{
padding:12px;
margin:10px;
border:none;
border-radius:10px;
}

#login button{
padding:12px 20px;
border:none;
border-radius:20px;
background:#ff2d75;
color:white;
cursor:pointer;
}

/* HEADER */
header{
height:100vh;
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
text-align:center;
}

header h1{
font-family:Dancing Script;
font-size:5rem;
text-shadow:0 0 20px white;
}

/* SECCIONES */
section{
padding:60px 10%;
}

.card{
background:rgba(255,255,255,.15);
backdrop-filter:blur(10px);
padding:25px;
border-radius:20px;
margin:20px auto;
max-width:900px;
}

/* INPUTS */
input, textarea{
width:100%;
padding:10px;
margin:5px 0;
border:none;
border-radius:10px;
}

/* BOTONES */
button{
padding:10px 15px;
border:none;
border-radius:20px;
background:#ff2d75;
color:white;
cursor:pointer;
margin-top:5px;
}

/* CORAZONES */
.heart{
position:fixed;
top:-10px;
animation:fall linear forwards;
pointer-events:none;
}

@keyframes fall{
to{transform:translateY(110vh);}
}

/* CURSOR */
.cursor{
position:fixed;
pointer-events:none;
animation:fade 1s forwards;
}

@keyframes fade{
to{opacity:0;transform:translateY(-40px);}
}

/* CANVAS */
canvas{
position:fixed;
inset:0;
z-index:-1;
}

</style>
</head>

<body>

<canvas id="stars"></canvas>

<!-- LOGIN -->
<div id="login">
<h1>❤️ Bienvenido ❤️</h1>
<input id="user" placeholder="Tu nombre">
<button onclick="start()">Entrar 💖</button>
</div>

<header>
<h1>Manel ❤️ Julia Torrado</h1>
<p>Una web de amor interactiva</p>
</header>

<!-- PAREJA -->
<section class="card">
<h2>💖 Pareja del día</h2>
<div id="pair"></div>
</section>

<!-- CALCULADORA -->
<section class="card">
<h2>💘 Calculadora del amor</h2>
<input id="a" placeholder="Nombre 1">
<input id="b" placeholder="Nombre 2">
<button onclick="love()">Calcular</button>
<div id="loveRes"></div>
</section>

<!-- CHAT -->
<section class="card">
<h2>💬 Chat</h2>
<div id="chat"></div>
<input id="msg" placeholder="Mensaje">
<button onclick="send()">Enviar</button>
</section>

<!-- RANKING -->
<section class="card">
<h2>🏆 Ranking</h2>
<div id="rank"></div>
</section>

<!-- RECUERDOS -->
<section class="card">
<h2>📖 Recuerdos</h2>
<textarea id="rec"></textarea>
<button onclick="save()">Guardar</button>
<div id="list"></div>
</section>

<!-- NIVEL -->
<section class="card">
<h2>💘 Nivel de amor</h2>
<div id="level"></div>
</section>

<!-- MUSIC -->
<audio id="music" loop>
<source src="https://cdn.pixabay.com/audio/2022/03/15/audio_c8b8b1.mp3">
</audio>

<button style="position:fixed;bottom:20px;right:20px;border-radius:50%;padding:15px" onclick="document.getElementById('music').play()">🎵</button>

<script>

/* LOGIN */
function start(){
document.getElementById("login").style.display="none";
}

/* PAREJA DEL DÍA */
const boys=["Manel","Lucas","Hugo","Pablo","Leo","David"];
const girls=["Julia Torrado","Sofía","Lucía","Paula","Martina","Sara"];

let d=Math.floor((new Date()-new Date(new Date().getFullYear(),0,0))/86400000);

document.getElementById("pair").innerHTML=
"❤️ "+boys[d%boys.length]+" & "+girls[(d*7)%girls.length]+" ❤️";

/* LOVE */
function love(){
let x=document.getElementById("a").value;
let y=document.getElementById("b").value;

let s=0;
for(let i=0;i<(x+y).length;i++)s+=(x+y).charCodeAt(i);

document.getElementById("loveRes").innerHTML="💖 "+(s%101)+"%";
}

/* CHAT */
function send(){
let m=document.getElementById("msg").value;
if(!m)return;

let d=document.createElement("div");
d.innerHTML="💌 "+m;
document.getElementById("chat").appendChild(d);

document.getElementById("msg").value="";
}

/* RANK */
const rank=[
{n:"Manel",v:100},
{n:"Julia Torrado",v:100},
{n:"Lucas",v:80},
{n:"Sofía",v:85}
];

document.getElementById("rank").innerHTML=
rank.map(r=>"❤️ "+r.n+" "+r.v+"%").join("<br>");

/* LEVEL */
document.getElementById("level").innerHTML=
"🔥 "+(90+Math.floor(Math.random()*10))+"% infinito";

/* HEARTS */
setInterval(()=>{
let h=document.createElement("div");
h.className="heart";
h.innerHTML="❤️";
h.style.left=Math.random()*100+"vw";
h.style.fontSize=(10+Math.random()*30)+"px";
h.style.animationDuration=(5+Math.random()*5)+"s";
document.body.appendChild(h);
setTimeout(()=>h.remove(),10000);
},200);

/* CURSOR */
document.addEventListener("mousemove",e=>{
let c=document.createElement("div");
c.className="cursor";
c.innerHTML="💖";
c.style.left=e.clientX+"px";
c.style.top=e.clientY+"px";
document.body.appendChild(c);
setTimeout(()=>c.remove(),1000);
});

/* STARS */
let canvas=document.getElementById("stars");
let ctx=canvas.getContext("2d");

canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

let stars=[];
for(let i=0;i<120;i++){
stars.push({x:Math.random()*canvas.width,y:Math.random()*canvas.height,r:Math.random()*2});
}

function draw(){
ctx.clearRect(0,0,canvas.width,canvas.height);
ctx.fillStyle="white";

stars.forEach(s=>{
ctx.beginPath();
ctx.arc(s.x,s.y,s.r,0,Math.PI*2);
ctx.fill();
s.y+=0.3;
if(s.y>canvas.height)s.y=0;
});

requestAnimationFrame(draw);
}
draw();

</script>

</body>
</html>
