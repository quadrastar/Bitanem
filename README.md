[Bitanem.html](https://github.com/user-attachments/files/22348867/Bitanem.html)
<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bitanem 💖</title>
<style>
:root{
  --accent:#ff5c8a;
  --accent2:#ff99bb;
}
body, html{
  margin:0;
  padding:0;
  width:100%;
  height:100%;
  font-family:sans-serif;
  overflow:hidden;
  position:relative;
  background-color:hsl(330,80%,85%);
  transition: background-color 2s linear;
}
.card{
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  height:100%;
  text-align:center;
  z-index:2;
  position:relative;
}
button{
  padding:16px 28px;
  font-size:22px;
  border:none;
  border-radius:12px;
  cursor:pointer;
  margin:10px;
  position:relative;
  z-index:2;
}
.yesBtn{
  background:linear-gradient(135deg,var(--accent),var(--accent2));
  color:white;
  transition: transform 0.3s ease;
}
#no{
  background:white;
  color:#cc0066;
  border:2px dashed #ff99bb;
  position:absolute;
  transition: top 0.3s ease, left 0.3s ease;
  cursor:pointer;
}
#meriContainer{
  display:flex;
  align-items:center;
  font-size:50px;
  margin:20px;
}
#meri span{transition: transform 0.3s ease;}
.heart{
  font-size:36px;
  margin-left:4px;
}
.float{
  position:absolute;
  font-size:28px;
  user-select:none;
  pointer-events:none;
  transform-origin: center;
}
#soNsuza{
  position:absolute;
  top:50%;
  left:50%;
  transform: translate(-50%, -50%) scale(0);
  font-size:48px;
  color:white;
  text-align:center;
  font-weight:bold;
  text-shadow: 0 0 12px #ff69b4;
  transition: transform 0.8s cubic-bezier(.2,.9,.2,1), opacity 0.8s;
  z-index:5;
  opacity:0;
  pointer-events:none;
}
/* hafif parıltı animasyonu */
@keyframes glow {
  0% { text-shadow: 0 0 8px rgba(255,105,180,0.6); transform: translate(-50%, -50%) scale(1); }
  50% { text-shadow: 0 0 20px rgba(255,105,180,0.95); transform: translate(-50%, -50%) scale(1.06); }
  100% { text-shadow: 0 0 8px rgba(255,105,180,0.6); transform: translate(-50%, -50%) scale(1); }
}
.corner{
  position:fixed;
  font-size:16px;
  color: rgba(255,255,255,0.8);
  font-style:italic;
  text-shadow:0 0 3px rgba(0,0,0,0.2);
}
#bottomRight{bottom:12px; right:12px;}
#topLeft{top:12px; left:12px; font-size:18px;}
#bottomLeft{bottom:12px; left:12px; font-size:18px;}
#topRight{
  position:fixed;
  top:20px;
  right:20px;
  text-align:right;
  line-height:1.6em;
  z-index:2;
  color: rgba(255,255,255,0.8);
  text-shadow: 0 0 4px rgba(0,0,0,0.2);
}
#topRight span{display:block; font-size:20px; font-weight:bold;}
</style>
</head>
<body>
<div class="card">
  <div id="meriContainer">
    <div id="meri">
      <span style="color:#ff69b4;">M</span><span style="color:#ff69b4;">e</span><span style="color:purple;">Rİ</span>
      <span class="heart">💗</span><span class="heart">💖</span><span class="heart">💗</span><span class="heart">💖</span>
    </div>
  </div>

  <h1 style="font-size:40px;color: rgba(255,255,255,0.9);text-shadow:0 0 8px rgba(255,255,255,0.4);">
    It Takes Two oynamak ister misin? 🎮💕
  </h1>
  <p id="subtitle" style="font-size:22px;color: rgba(255,255,255,0.7);">😔</p>
  <div>
    <button class="yesBtn">Evet 💕</button>
    <button id="no">Hayır 🙈</button>
  </div>

  <!-- Güncel mesaj -->
  <div id="soNsuza">İyi ki varsın 💖🥰💞</div>
</div>

<div id="topRight">
  <span style="color:#ff99bb;">bekle</span>
  <span style="color:white;">bekle</span>
  <span style="color:black;">bekle</span>
</div>
<div id="bottomRight" class="corner">Dünyanın en iyi Yuumi 🐾</div>
<div id="topLeft" class="corner">Zıpla zıpla zıpla</div>
<div id="bottomLeft" class="corner">Sivir adc</div>

<script>
const yesBtn = document.querySelector('.yesBtn');
const noBtn = document.getElementById('no');
const soNsuza = document.getElementById('soNsuza');
const subtitle = document.getElementById('subtitle');
let yesScale = 1;
let noClickCount = 0;
const maxFloats = 100;

const noMessages = [
  "Emin misin? 🤔",
  "Yapma 😡",
  "Kızıyorum 😠",
  "Alistar mı? 🐮",
  "Alistar mı? 🐮",
  "Alistar mı? 🐮",
  "Gerçekten 😳"
];

function rnd(min,max){ return Math.random()*(max-min)+min; }

function spawnFloat(char, x, y=null, scale=1){
  if(document.querySelectorAll('.float').length >= maxFloats) return;
  const div = document.createElement('div');
  div.className = 'float';
  div.textContent = char;
  div.style.left = x + 'px';
  div.style.top = (y !== null ? y : -50) + 'px';
  div.style.fontSize = rnd(18,40)*scale + 'px';
  document.body.appendChild(div);

  let startX = parseFloat(div.style.left);
  let startY = parseFloat(div.style.top);
  let rotation = 0;

  const anim = ()=>{
    startY += 1 + rnd(0,1);
    rotation += 2;
    div.style.top = startY + 'px';
    div.style.left = startX + 'px';
    div.style.transform = `rotate(${rotation}deg)`;
    div.style.opacity = 1 - startY/window.innerHeight;
    if(startY < window.innerHeight + 50) requestAnimationFrame(anim);
    else div.remove();
  }
  anim();
}

// Kalp yağmurları
setInterval(()=>{ spawnFloat(Math.random()>0.5?'💖':'💗', 0); }, 500);
setInterval(()=>{ spawnFloat(Math.random()>0.5?'💖':'💗', window.innerWidth-40); }, 500);

// Tıklama patlaması
document.body.addEventListener('click',(e)=>{
  for(let i=0;i<10;i++){
    spawnFloat(Math.random()>0.5?'💖':'💗', e.clientX + rnd(-30,30), e.clientY + rnd(-30,30), rnd(0.5,1));
  }
});

// Evet butonu: kalıcı mesaj gösterme + hafif animasyon + küçük kutlama efekti
yesBtn.addEventListener('click',()=>{
  // küçük kutlama kalpleri
  for(let i=0;i<50;i++){ spawnFloat(Math.random()>0.5?'💖':'💗'); }

  // soNsuza'yı görünür ve kalıcı yap
  soNsuza.style.opacity = '1';
  soNsuza.style.transform = 'translate(-50%, -50%) scale(1)';
  soNsuza.style.animation = 'glow 1.6s ease-in-out infinite';

  // başlık altındaki küçük emojiyi değiştir
  subtitle.textContent = 'Hemen başlayalım mı? 🎮';

  // Evet butonunu hafifçe sabitle/ölçeklendir (görsel feedback)
  yesScale = 1.12;
  yesBtn.style.transform = `scale(${yesScale})`;
});

// Hayır butonu kaçma davranışı
function moveNoBtn(){
  const margin = 60;
  const maxLeft = Math.max(60, window.innerWidth - noBtn.offsetWidth - margin);
  const maxTop = Math.max(60, window.innerHeight - noBtn.offsetHeight - margin);
  noBtn.style.top = rnd(margin, maxTop) + 'px';
  noBtn.style.left = rnd(margin, maxLeft) + 'px';
}
noBtn.addEventListener('mouseenter',()=>{ 
  moveNoBtn(); 
  yesScale += 0.15; 
  yesBtn.style.transform = `scale(${yesScale})`; 
});
noBtn.addEventListener('click',()=>{
  noBtn.innerText = noMessages[noClickCount % noMessages.length];
  noClickCount++;
  moveNoBtn();
});
window.addEventListener('resize', moveNoBtn);

// Arka plan renk değişimi
let hue = 330;
setInterval(()=>{ hue += 0.1; if(hue > 360) hue = 0; document.body.style.backgroundColor = `hsl(${hue},80%,85%)`; }, 50);
</script>
</body>
</html>
