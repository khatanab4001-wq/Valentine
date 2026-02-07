<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Valentine 💖</title>

<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Poppins:wght@400;700;900&display=swap" rel="stylesheet">

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:'Poppins',sans-serif;
}
body{
  min-height:100vh;
  background:radial-gradient(circle at top,#2a0036,#050008);
  display:flex;
  justify-content:center;
  align-items:center;
  color:white;
  overflow:hidden;
}

/* HEART BACKGROUND */
.heart{
  position:absolute;
  font-size:16px;
  opacity:0.6;
  animation:float 9s linear infinite;
}
@keyframes float{
  0%{transform:translateY(110vh) scale(0.6);}
  100%{transform:translateY(-10vh) scale(1.2);}
}

/* ---------- FIRST PAGE ---------- */
#question{
  text-align:center;
  padding:20px;
}
#question h1{
  font-size:2.2rem;
  font-weight:900;
  text-shadow:0 0 25px #ff4da6;
}
.buttons{
  margin-top:30px;
  display:flex;
  gap:20px;
  justify-content:center;
  position:relative;
}
button{
  padding:15px 35px;
  font-size:1.1rem;
  border:none;
  border-radius:50px;
  cursor:pointer;
  font-weight:700;
}
#yes{
  background:linear-gradient(45deg,#ff2f92,#a600ff);
  color:white;
  box-shadow:0 0 20px #ff2f92;
}
#no{
  background:#fff;
  color:#ff2f92;
  position:relative;
  transition:0.2s;
}

/* ---------- SECOND PAGE ---------- */
#celebration{
  display:none;
  width:100%;
  min-height:100vh;
  justify-content:center;
  align-items:center;
  padding:30px 20px;
}

.message-box{
  max-width:520px;
  width:100%;
  background:rgba(0,0,0,0.6);
  border-radius:24px;
  padding:30px;
  text-align:center;
  box-shadow:0 0 40px rgba(255,0,140,0.4);
  animation:fadeUp 1.2s ease forwards;
}
@keyframes fadeUp{
  from{opacity:0; transform:translateY(40px);}
  to{opacity:1; transform:translateY(0);}
}
.message-box h2{
  font-family:'Pacifico',cursive;
  font-size:1.9rem;
  color:#ff9ad5;
  margin-bottom:15px;
}
.message-box p{
  line-height:1.7;
  color:#f2e9ff;
}

/* OPEN MEMORY */
.open-box{
  margin-top:25px;
  padding:14px;
  border-radius:16px;
  background:linear-gradient(45deg,#ff2f92,#7b00ff);
  font-weight:700;
  cursor:pointer;
  box-shadow:0 0 20px rgba(255,47,146,0.6);
}

/* SLIDER */
.slider{
  margin:20px auto 0;
  width:230px;
  height:300px;
  border-radius:20px;
  overflow:hidden;
  box-shadow:0 0 30px rgba(255,255,255,0.4);
  display:none;
}
.slider img{
  width:100%;
  height:100%;
  object-fit:cover;
}

/* MOBILE */
@media(max-width:480px){
  #question h1{font-size:1.9rem;}
  .message-box h2{font-size:1.6rem;}
}
</style>
</head>

<body>

<!-- FIRST PAGE -->
<div id="question">
  <h1>AMBALIKA, WILL YOU BE MY VALENTINE? 💖</h1>
  <div class="buttons">
    <button id="yes">YES 💘</button>
    <button id="no">NO 🙈</button>
  </div>
</div>

<!-- SECOND PAGE -->
<div id="celebration">
  <div class="message-box">
    <h2>Happy Valentine Week 💖</h2>
    <p>
      Tu sirf dost nahi,<br>
      meri aadat aur sukoon hai 🌙<br><br>

      Andheri raaton me jo roshni bane,<br>
      wo pyari si wajah tu hai ✨<br><br>

      Valentine shayad pyaar ke liye hota ho ❤️<br>
      par meri har khushi ka reason<br>
      bas tu hi rahe 🤍
    </p>

    <div class="open-box" id="openBox">
      Open Memories 💕
    </div>

    <div class="slider" id="slider">
      <img id="slide" src="1.jpg">
    </div>
  </div>
</div>

<audio id="music" src="https://cdn.pixabay.com/audio/2023/02/14/audio_5c7c3a63a4.mp3"></audio>

<script>
/* HEARTS */
const hearts=["❤️","💖","💘","💕"];
setInterval(()=>{
  const h=document.createElement("div");
  h.className="heart";
  h.innerText=hearts[Math.floor(Math.random()*hearts.length)];
  h.style.left=Math.random()*100+"vw";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),9000);
},900);

/* NO BUTTON PLAYFUL */
const no=document.getElementById("no");
function moveNo(){
  no.style.position="absolute";
  no.style.left=Math.random()*(window.innerWidth-120)+"px";
  no.style.top=Math.random()*(windo

w.innerHeight-80)+"px";
}
no.addEventListener("mouseenter",moveNo);
no.addEventListener("click",moveNo);
no.addEventListener("touchstart",moveNo);

/* YES CLICK – PAGE SWITCH */
document.getElementById("yes").onclick=()=>{
  document.getElementById("question").style.display="none";
  document.getElementById("celebration").style.display="flex";
  music.currentTime=0;
  music.play();
};

/* OPEN MEMORY – PHOTO ONE BY ONE */
let index=1, started=false;
document.getElementById("openBox").onclick=()=>{
  const slider=document.getElementById("slider");
  slider.style.display="block";

  if(!started){
    started=true;
    setInterval(()=>{
      index++;
      if(index>10) index=1;
      document.getElementById("slide").src=index+".jpg";
    },2000);
  }
};
</script>

</body>
</html>
