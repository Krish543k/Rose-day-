<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<title>Rose Day – Annu 🌹</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
*{box-sizing:border-box;}

body{
    margin:0;
    min-height:100vh;
    background:linear-gradient(135deg,#ff758c,#ff7eb3);
    overflow:hidden;
    font-family:'Segoe UI',sans-serif;
}

/* PASSWORD SCREEN */
#lockScreen{
    position:fixed;
    inset:0;
    background:linear-gradient(135deg,#ff758c,#ff7eb3);
    display:flex;
    justify-content:center;
    align-items:center;
    z-index:10000;
}
.lock-box{
    background:rgba(255,255,255,0.25);
    backdrop-filter:blur(12px);
    padding:25px;
    border-radius:20px;
    text-align:center;
    width:90%;
    max-width:320px;
}
.lock-box h2{color:#b30000;}
.lock-box input{
    width:100%;
    padding:10px;
    border:none;
    border-radius:15px;
    font-size:18px;
    text-align:center;
}
.lock-box button{
    margin-top:15px;
    padding:10px 25px;
    border:none;
    border-radius:20px;
    background:#ff4d6d;
    color:#fff;
    font-size:16px;
}
.lock-error{color:#fff;font-size:14px;display:none;}

/* BACKGROUND ROSES */
.bg-rose{
    position:absolute;
    font-size:30px;
    opacity:0.35;
    animation:bgFloat 12s linear infinite;
    pointer-events:none;
}
@keyframes bgFloat{
    from{transform:translateY(110vh) rotate(0deg);}
    to{transform:translateY(-120vh) rotate(360deg);}
}

/* FLOWER RAIN */
.rain-flower{
    position:fixed;
    top:-50px;
    font-size:34px;
    animation:fall linear forwards;
    pointer-events:none;
    z-index:2000;
}
@keyframes fall{
    to{transform:translateY(120vh) rotate(360deg);opacity:0;}
}

/* FLOWER BUTTON */
.flower-btn{
    position:fixed;
    top:15px;
    right:15px;
    background:#fff;
    border:none;
    border-radius:30px;
    padding:10px 16px;
    font-size:18px;
    cursor:pointer;
    z-index:3000;
}

/* MAIN BOX */
.box{
    z-index:10;
    width:90%;
    max-width:380px;
    background:rgba(255,255,255,0.22);
    backdrop-filter:blur(12px);
    padding:20px;
    border-radius:22px;
    text-align:center;
    box-shadow:0 20px 40px rgba(0,0,0,0.3);
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
}

h1{color:#b30000;margin:8px 0;}
h2{color:#fff;margin:0;}

.rose{
    font-size:120px;
    cursor:pointer;
    animation:bounce 2s infinite;
}
@keyframes bounce{
    0%,100%{transform:translateY(0);}
    50%{transform:translateY(-18px);}
}

/* POPUP */
.popup{
    position:fixed;
    inset:0;
    background:rgba(0,0,0,0.6);
    display:none;
    justify-content:center;
    align-items:center;
    z-index:4000;
}
.popup-box{
    background:#fff;
    width:90%;
    max-width:320px;
    padding:20px;
    border-radius:18px;
    text-align:center;
}
.popup-box p{color:#b30000;}
.popup-box button{
    margin-top:15px;
    padding:10px 22px;
    border:none;
    border-radius:20px;
    background:#ff4d6d;
    color:#fff;
}

/* TEXT */
.stable-line{margin-top:14px;color:#fff;}
.girl-line{margin-top:8px;color:#ffe6ea;font-size:15px;}

/* BOTTOM LINE */
.bottom-line{
    position:fixed;
    bottom:12px;
    width:100%;
    text-align:center;
    color:#fff;
    animation:glow 2s infinite alternate;
}
@keyframes glow{
    from{text-shadow:0 0 5px #fff;}
    to{text-shadow:0 0 15px #ffd1dc;}
}
</style>
</head>

<body>

<!-- PASSWORD -->
<div id="lockScreen">
    <div class="lock-box">
        <h2>🔐 Enter Password</h2>
        <input type="password" id="pwd" placeholder="only u ddmm">
        <button onclick="checkPassword()">OPEN</button>
        <div class="lock-error" id="err">❌ Galat password</div>
    </div>
</div>

<button class="flower-btn" onclick="flowerRain()">🌸 Flowers</button>

<script>
function checkPassword(){
    let p=document.getElementById("pwd").value;
    if(p==="1110"){
        document.getElementById("lockScreen").style.display="none";
        for(let i=0;i<25;i++){
            let r=document.createElement("div");
            r.className="bg-rose";
            r.innerHTML="🌹";
            r.style.left=Math.random()*100+"vw";
            r.style.animationDuration=(7+Math.random()*6)+"s";
            document.body.appendChild(r);
        }
    }else{
        document.getElementById("err").style.display="block";
    }
}

function flowerRain(){
    for(let i=0;i<50;i++){
        let f=document.createElement("div");
        f.className="rain-flower";
        f.innerHTML="🌸";
        f.style.left=Math.random()*100+"vw";
        f.style.animationDuration=(3+Math.random()*3)+"s";
        document.body.appendChild(f);
        setTimeout(()=>f.remove(),6500);
    }
}
</script>

<div class="box">
    <h1>🌹 Happy Rose Day 🌹</h1>
    <h2>Dear Annu 💖</h2>

    <div class="rose" onclick="openPopup()">🌹</div>
    <p style="color:#fff;">(☝️ touch karo)</p>

    <div id="stableText"></div>
</div>

<!-- POPUP WITH MISS-YOU SHAYARI -->
<div class="popup" id="popup">
    <div class="popup-box">
        <p>
        🌹 Rose Day aaya hai aaj,<br>
        Aur tumhari yaad aur gehri ho gayi,<br>
        Phool haath me hai mere,<br>
        Par khushboo tumhare bina adhoori ho gayi.
        </p>
        <button onclick="nextLine()">ok</button>
    </div>
</div>

<div class="bottom-line">
    🌸 Yeh khubsurat & beautiful ladki ke liye 🌸
</div>

<script>
function openPopup(){
    document.getElementById("popup").style.display="flex";
}
function nextLine(){
    document.getElementById("popup").style.display="none";
    document.getElementById("stableText").innerHTML = `
        <div class="stable-line">
            💕 Annu, tumhari dosti meri zindagi ka sabse khubsurat phool hai 🌹
        </div>
        <div class="girl-line">
            Mujhe pata hai tum pareshaan ho,<br>
            par pareshaan hone ki zarurat nahi hai 💖<br><br>
            Phool to bahut hain par gulaab jaisa koi nahi,<br>
            Ladkiyan to bahut hain… par tum jaisi koi nahi 😇 bigi hui ladki
        </div>
    `;
}
</script>

</body>
</html>



