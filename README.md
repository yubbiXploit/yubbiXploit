<!doctype html>

<html lang="id">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>yubbiXploit · Sakura Cyber</title>
<style>
:root{
  --neon-pink:#ff0048;
  --sakura:#ffb7c5;
  --cyber:#00ffe0;
  --bg-dark:#080510;
  --bg-light:#fdf6f8;
  --glass-dark:rgba(255,255,255,0.05);
  --glass-light:rgba(255,255,255,0.3);
  --font: 'Poppins', 'Noto Sans JP', sans-serif;
}
body{
  margin:0;overflow:hidden;height:100vh;
  display:flex;align-items:center;justify-content:center;
  font-family:var(--font);
  background:linear-gradient(160deg,var(--bg-dark),#120818);
  color:white;transition:background 2s,color 2s;
}
.card{
  position:relative;width:90%;max-width:900px;padding:30px;border-radius:20px;
  backdrop-filter:blur(12px);background:var(--glass-dark);
  border:1px solid rgba(255,255,255,0.1);
  box-shadow:0 0 40px rgba(255,0,68,0.2),0 0 80px rgba(255,255,255,0.05) inset;
  text-align:center;animation:floaty 8s ease-in-out infinite alternate;
}
@keyframes floaty{from{transform:translateY(0)}to{transform:translateY(-10px)}}
h1{
  font-size:2.5em;
  background:linear-gradient(90deg,var(--sakura),var(--cyber));
  -webkit-background-clip:text;color:transparent;
  text-shadow:0 0 25px rgba(255,0,100,0.4);
}
p{opacity:0.8;font-size:1.1em}.btn{ background:linear-gradient(90deg,var(--neon-pink),var(--cyber)); color:white;border:none;border-radius:10px;padding:10px 20px;font-weight:600; box-shadow:0 0 20px rgba(255,0,80,0.5); cursor:pointer;transition:transform .2s, box-shadow .2s; } .btn:hover{transform:scale(1.1);box-shadow:0 0 30px rgba(255,100,200,0.8)}

/* Sakura petals */ .petal{ position:fixed;width:15px;height:15px;background:radial-gradient(circle,var(--sakura),transparent 70%); border-radius:50%;pointer-events:none;animation:fall 10s linear infinite; } @keyframes fall{ 0%{transform:translateY(-10vh) rotate(0deg) scale(1)} 100%{transform:translateY(110vh) rotate(720deg) scale(0.8);opacity:0} }

/* Grid cyber lines */ canvas#grid{position:absolute;top:0;left:0;width:100%;height:100%;z-index:-1;}

/* Dark-light mode auto switch */ body.day{background:linear-gradient(160deg,var(--bg-light),#ffd6e0);color:#111;} body.day .card{background:var(--glass-light);box-shadow:0 0 20px rgba(255,182,193,0.3)} body.day h1{color:var(--neon-pink);-webkit-background-clip:unset;} </style>

</head>
<body>
<canvas id="grid"></canvas>
<div class="card">
  <h1>🌸 yubbiXploit 🌸</h1>
  <p>Fusion of Sakura Aesthetics × Cyber Security Elegance</p>
  <button class="btn">Explore Repositories</button>
</div>
<script>
// cyber grid
const c=document.getElementById('grid');const x=c.getContext('2d');
function r(){c.width=innerWidth;c.height=innerHeight}
function d(t){r();x.clearRect(0,0,c.width,c.height);x.strokeStyle='rgba(255,0,100,0.1)';x.lineWidth=1;
const g=40;for(let i=0;i<c.width;i+=g){x.beginPath();x.moveTo(i,0);x.lineTo(i,c.height);x.stroke();}
for(let j=0;j<c.height;j+=g){x.beginPath();x.moveTo(0,j);x.lineTo(c.width,j);x.stroke();}
requestAnimationFrame(d);}requestAnimationFrame(d);// sakura petals for(let i=0;i<30;i++){ let p=document.createElement('div');p.className='petal'; p.style.left=Math.random()*100+'vw'; p.style.animationDuration=8+Math.random()*5+'s'; p.style.animationDelay=Math.random()*5+'s'; document.body.appendChild(p); }

// auto mode (day/night) function mode(){const h=new Date().getHours();if(h>6&&h<18){document.body.classList.add('day');}else{document.body.classList.remove('day');}} mode();setInterval(mode,60000); </script>

</body>
</html>
