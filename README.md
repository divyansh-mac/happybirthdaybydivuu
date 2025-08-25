<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Happy Birthday Cutuu 💖</title>
<!-- GSAP CDN -->
<script src="https://cdn.jsdelivr.net/npm/gsap@3.12.5/dist/gsap.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3.12.5/dist/MotionPathPlugin.min.js"></script>
<style>
/* ===== Basic Reset ===== */
body, html { margin:0; padding:0; overflow:hidden; width:100%; height:100%; font-family: "Segoe UI", sans-serif; color:white; background: radial-gradient(circle at top, #0a0a2e, #000010);} 
canvas#stars { position:absolute; top:0; left:0; width:100%; height:100%; z-index:0; }
/* ===== Overlay ===== */
#overlay { position:fixed; top:0; left:0; right:0; bottom:0; background:rgba(0,0,0,0.85); display:flex; align-items:center; justify-content:center; color:white; font-size:2em; z-index:9999; cursor:pointer; }
/* ===== Floating Hearts ===== */
.heart { position:absolute; font-size:20px; color:rgba(255,100,150,0.7); animation: floatUp 8s linear infinite; }
@keyframes floatUp { 0% { transform: translateY(0) scale(1); opacity:1; } 100% { transform: translateY(-120vh) scale(0.5); opacity:0; }}
/* ===== Wishes Text ===== */
.wishes { position:absolute; top:15%; width:100%; z-index:5; text-align:center; }
.wishes h1 { font-size:3em; text-shadow:0 0 15px hotpink; animation: glow 3s ease-in-out infinite alternate; }
.wishes h2 { font-size:1.5em; opacity:0.9; }
.wishes p { font-size:1.2em; opacity:0.7; }
@keyframes glow { from { text-shadow:0 0 10px hotpink,0 0 20px pink;} to { text-shadow:0 0 20px deeppink,0 0 40px violet; }}
/* ===== Cake ===== */
.cake { position:absolute; bottom:120px; left:50%; transform:translateX(-50%); z-index:6; }
.cake svg { width:200px; }
.cake button { margin-top:10px; padding:8px 16px; background:hotpink; border:none; border-radius:8px; color:white; font-size:1em; cursor:pointer; box-shadow:0 0 10px deeppink; }
/* ===== Cats ===== */
.cats { position:absolute; bottom:40px; left:50%; transform:translateX(-50%); z-index:5; }
.cats svg { width:200px; }
/* ===== Confetti ===== */
.confetti { position:absolute; width:8px; height:8px; background:hotpink; opacity:0.8; border-radius:50%; pointer-events:none; }
/* ===== Butterflies ===== */
.butterfly { position:absolute; width:40px; height:20px; pointer-events:none; }
</style>
</head>
<body>

<canvas id="stars"></canvas>
<div id="overlay">Tap to Begin 💖</div>

<div class="wishes">
  <h1>Happy Birthday, Cutuu 🎂</h1>
  <h2>— from your pretty little baby —</h2>
  <p>Forever in my sky ✨</p>
</div>

<div class="cats">
  <svg viewBox="0 0 200 150">
    <path d="M60 130 C55 100 65 80 60 60 Q55 40 70 30 Q85 20 95 30 Q105 40 100 60 Q95 80 105 100 C110 120 80 130 60 130Z" fill="black"/>
    <path d="M140 130 C135 100 145 80 140 60 Q135 40 150 30 Q165 20 175 30 Q185 40 180 60 Q175 80 185 100 C190 120 160 130 140 130Z" fill="black"/>
    <path d="M95 130 Q100 110 105 130 Q100 120 95 130Z" stroke="deeppink" stroke-width="3" fill="none"/>
  </svg>
</div>

<div class="cake">
  <svg viewBox="0 0 200 200">
    <rect x="40" y="120" width="120" height="40" fill="pink" stroke="deeppink" stroke-width="3"/>
    <rect x="60" y="80" width="80" height="40" fill="lightpink" stroke="deeppink" stroke-width="3"/>
    <rect x="70" y="60" width="10" height="20" fill="white"/>
    <rect x="100" y="60" width="10" height="20" fill="white"/>
    <rect x="120" y="60" width="10" height="20" fill="white"/>
    <circle class="flame" cx="75" cy="55" r="5" fill="orange"/>
    <circle class="flame" cx="105" cy="55" r="5" fill="orange"/>
    <circle class="flame" cx="125" cy="55" r="5" fill="orange"/>
  </svg>
  <button id="cutBtn">Cut the Cake 🎉</button>
</div>

<audio id="bgm" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" loop></audio>

<script>
// ===== Overlay Tap =====
const overlay=document.getElementById('overlay');
const bgm=document.getElementById('bgm');
overlay.addEventListener('click',()=>{ overlay.style.display='none'; bgm.play(); });

// ===== Stars =====
const canvas=document.getElementById('stars');
const ctx=canvas.getContext('2d');
let stars=[];
function resize(){ canvas.width=innerWidth; canvas.height=innerHeight; stars=Array.from({length:300},()=>({x:Math.random()*canvas.width, y:Math.random()*canvas.height, r:Math.random()*1.5+0.5, o:Math.random()}));}
window.addEventListener('resize',resize);
resize();
function animateStars(){ ctx.clearRect(0,0,canvas.width,canvas.height); stars.forEach(s=>{ ctx.beginPath(); ctx.arc(s.x,s.y,s.r,0,Math.PI*2); ctx.fillStyle=`rgba(255,255,255,${s.o})`; ctx.fill(); s.o+=(Math.random()-0.5)*0.05; if(s.o<0)s.o=0; if(s.o>1)s.o=1; }); requestAnimationFrame(animateStars); }
animateStars();

// ===== Floating Hearts =====
setInterval(()=>{ const h=document.createElement('div'); h.className='heart'; h.style.left=Math.random()*100+'vw'; h.style.fontSize=(10+Math.random()*20)+'px'; h.style.color=`rgba(255,${50+Math.random()*200},${100+Math.random()*155},0.8)`; h.textContent='❤'; document.body.appendChild(h); setTimeout(()=>h.remove(),9000); },600);

// ===== Butterflies =====
gsap.registerPlugin(MotionPathPlugin);
function makeButterfly(){ const b=document.createElementNS("http://www.w3.org/2000/svg","svg"); b.setAttribute("viewBox","0 0 40 20"); b.classList.add('butterfly'); b.innerHTML=`<path d="M10 10 Q0 0 0 20Z" fill="purple"/><path d="M30 10 Q40 0 40 20Z" fill="violet"/>`; document.body.appendChild(b);
const startX=Math.random()*innerWidth, startY=Math.random()*innerHeight;
const endX=Math.random()*innerWidth, endY=Math.random()*innerHeight;
gsap.to(b,{duration:8+Math.random()*4, repeat:-1, motionPath:{path:[{x:startX,y:startY},{x:endX,y:endY}], curviness:1.5}, ease:'power1.inOut'});
gsap.to(b.querySelectorAll('path'),{scaleY:0.7, yoyo:true, repeat:-1, duration:0.3, transformOrigin:'center'});}
for(let i=0;i<8;i++) makeButterfly();

// ===== Cake Flames Animation =====
function flickerFlames(){ document.querySelectorAll('.flame').forEach(f=>{ gsap.to(f,{attr:{r:3+Math.random()*3}, duration:0.2, yoyo:true, repeat:-1}); });}
flickerFlames();

// ===== Cake Cut =====
document.getElementById('cutBtn').addEventListener('click',()=>{
  const cake=document.querySelector('.cake svg');
  gsap.to(cake,{rotationY:180, duration:1, ease:'power2.inOut'});
  // Confetti
  for(let i=0;i<50;i++){
    const c=document.createElement('div'); c.className='confetti';
    c.style.left=Math.random()*innerWidth+'px';
    c.style.top='0px';
    c.style.background=`hsl(${Math.random()*360},80%,60%)`;
    document.body.appendChild(c);
    gsap.to(c,{y:innerHeight+50, x:'+='+Math.random()*200-100, rotation:Math.random()*360, duration:3+Math.random()*2, ease:'power2.out', onComplete:()=>c.remove()});
  }
  alert('Cake Cut! 🎂💖');
});

</script>
</body>
</html>
# happybirthdaybydivuu
