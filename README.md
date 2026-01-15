<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#820ad1">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<title>Discord</title>

<link rel="icon" href="https://logodownload.org/wp-content/uploads/2017/11/discord-logo-4-1.png">
<link rel="apple-touch-icon" href="https://logodownload.org/wp-content/uploads/2017/11/discord-logo-4-1.png

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family: Arial, Helvetica, sans-serif;
}

html,body{
  width:100%;
  height:100%;
  background:#000;
  overflow:hidden;
}

canvas{
  position:fixed;
  inset:0;
  z-index:0;
}

.container{
  position:relative;
  z-index:2;
  width:100%;
  height:100%;
  display:flex;
  justify-content:center;
  align-items:center;
}

.panel{
  width:94%;
  max-width:460px;
}

.card{
  position:relative;
  display:flex;
  align-items:center;
  justify-content:space-between;
  background:#000;
  border-radius:14px;
  padding:14px;
  margin-bottom:14px;
}

.card::before{
  content:"";
  position:absolute;
  left:0;
  top:0;
  bottom:0;
  width:3px;
  background:#1e8bff;
  border-radius:14px 0 0 14px;
  box-shadow:0 0 10px rgba(30,139,255,0.9);
}

.left{
  display:flex;
  align-items:center;
  gap:12px;
}

.icon{
  width:38px;
  height:38px;
  border-radius:9px;
  background:#020202;
  display:flex;
  align-items:center;
  justify-content:center;
}

.icon img{
  width:100%;
  height:100%;
  object-fit:contain;
}

.text{
  color:#eaeaea;
}

.text b{
  font-size:14px;
  display:block;
}

.text span{
  font-size:11px;
  opacity:0.75;
}

.switch{
  position:relative;
  width:46px;
  height:24px;
}

.switch input{
  display:none;
}

.slider{
  position:absolute;
  inset:0;
  background:#000;
  border-radius:20px;
  border:1px solid #111;
  transition:.25s;
}

.slider:before{
  content:"";
  position:absolute;
  width:18px;
  height:18px;
  left:3px;
  bottom:3px;
  background:#222;
  border-radius:50%;
  transition:.25s;
}

input:checked + .slider{
  border-color:#1e8bff;
}

input:checked + .slider:before{
  transform:translateX(22px);
  background:#1e8bff;
  box-shadow:0 0 10px rgba(30,139,255,1);
}

.btn{
  width:100%;
  margin-top:10px;
  padding:14px;
  border:none;
  border-radius:14px;
  background:#1e8bff;
  color:#fff;
  font-size:15px;
  font-weight:bold;
  box-shadow:0 0 18px rgba(30,139,255,0.7);
}

.btn:active{
  transform:scale(0.97);
}
</style>
</head>

<body>

<canvas id="bg"></canvas>

<div class="container">
  <div class="panel">

    <!-- Precisão Full (SEGUNDO LINK) -->
    <div class="card">
      <div class="left">
        <div class="icon">
          <img src="https://i.ibb.co/8DQK6j3G/image.png">
        </div>
        <div class="text">
          <b>Precisão Full</b>
          <span>Aumenta a precisão de sua mira em até 5x.</span>
        </div>
      </div>
      <label class="switch">
        <input type="checkbox">
        <span class="slider"></span>
      </label>
    </div>

    <!-- Reduzir Recuo (PRIMEIRO LINK) -->
    <div class="card">
      <div class="left">
        <div class="icon">
          <img src="https://i.ibb.co/8DM6hbBc/image.png">
        </div>
        <div class="text">
          <b>Reduzir Recuo</b>
          <span>Remove 60% do recuo de armas AR e SMG</span>
        </div>
      </div>
      <label class="switch">
        <input type="checkbox">
        <span class="slider"></span>
      </label>
    </div>

    <!-- Remover Input Lag (ÚLTIMO LINK) -->
    <div class="card">
      <div class="left">
        <div class="icon">
          <img src="https://i.ibb.co/5xx3fVND/image.png">
        </div>
        <div class="text">
          <b>Remover Input Lag</b>
          <span>Retira todos os pequenos lags e travamentos do jogo</span>
        </div>
      </div>
      <label class="switch">
        <input type="checkbox">
        <span class="slider"></span>
      </label>
    </div>

    <button class="btn" onclick="abrirFF()">ABRIR O FREE FIRE</button>

  </div>
</div>

<script>
function abrirFF() {
  window.location.href =
  "intent://#Intent;package=com.dts.freefireth;scheme=freefire;S.browser_fallback_url=https://play.google.com/store/apps/details?id=com.dts.freefireth;end";
}

const c = document.getElementById("bg");
const ctx = c.getContext("2d");
c.width = innerWidth;
c.height = innerHeight;

let p=[];
for(let i=0;i<70;i++){
  p.push({
    x:Math.random()*c.width,
    y:Math.random()*c.height,
    r:Math.random()*2+1,
    dx:(Math.random()-0.5)*0.25,
    dy:(Math.random()-0.5)*0.25
  });
}

function anim(){
  ctx.clearRect(0,0,c.width,c.height);
  ctx.fillStyle="#1e8bff";
  p.forEach(o=>{
    o.x+=o.dx;
    o.y+=o.dy;
    if(o.x<0||o.x>c.width) o.dx*=-1;
    if(o.y<0||o.y>c.height) o.dy*=-1;
    ctx.beginPath();
    ctx.arc(o.x,o.y,o.r,0,Math.PI*2);
    ctx.fill();
  });
  requestAnimationFrame(anim);
}
anim();

onresize=()=>{
  c.width=innerWidth;
  c.height=innerHeight;
};
</script>

</body>
</html>
