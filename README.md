<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pro Soccer Training ⚽</title>

<style>
body {
    margin:0;
    font-family:Arial;
    background:#0b0b0b;
    color:white;
}

/* NAV */
nav {
    display:flex;
    justify-content:center;
    gap:20px;
    padding:15px;
    background:#000;
}
nav button {
    background:#0f0;
    border:none;
    padding:10px 20px;
    font-weight:bold;
    cursor:pointer;
    border-radius:10px;
}

/* SECTIONS */
.section {
    display:none;
    padding:20px;
}
.active { display:block; }

/* PLAYER CARDS */
.players {
    display:flex;
    gap:15px;
    justify-content:center;
    margin-top:20px;
}
.players img {
    width:120px;
    height:120px;
    border-radius:15px;
    object-fit:cover;
}

/* DRILLS */
.drill-container {
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(180px,1fr));
    gap:20px;
    max-width:900px;
    margin:auto;
}
.drill-card {
    background:#1a1a1a;
    border-radius:15px;
    aspect-ratio:1/1;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    cursor:pointer;
}
.drill-card.active {
    background:#222;
}
.hidden { display:none; }

/* BUTTONS */
.control-btn {
    margin:5px;
    padding:5px 10px;
    border:none;
    background:#0f0;
    cursor:pointer;
    border-radius:5px;
}
</style>
</head>

<body>

<nav>
<button onclick="show('home')">HOME</button>
<button onclick="show('training')">TRAINING</button>
<button onclick="show('progress')">PROGRESS</button>
</nav>

<!-- HOME -->
<div id="home" class="section active">
<h1>Train Like a Pro ⚽</h1>

<div class="players">
<img src="https://images.unsplash.com/photo-1603297631958-9b9c5f0c6a3d">
<img src="https://images.unsplash.com/photo-1517649763962-0c623066013b">
<img src="https://images.unsplash.com/photo-1521417531039-51c0c3e6b8d6">
<img src="https://images.unsplash.com/photo-1508098682722-e99c43a406b2">
<img src="https://images.unsplash.com/photo-1495555687398-3f50d6e9a2c4">
</div>

<br>
<button onclick="show('training')">START TRAINING</button>
</div>

<!-- TRAINING -->
<div id="training" class="section">
<h2>Training Drills</h2>

<div class="drill-container">

<div class="drill-card" onclick="toggle(this,120)">
<h3>Dribbling</h3>
<div class="hidden">
<p class="timer">120</p>
<button class="control-btn" onclick="start(event)">Start</button>
<button class="control-btn" onclick="stop(event)">Stop</button>
<button class="control-btn" onclick="reset(event,120)">Reset</button>
</div>
</div>

<div class="drill-card" onclick="toggle(this,180)">
<h3>Passing</h3>
<div class="hidden">
<p class="timer">180</p>
<button class="control-btn" onclick="start(event)">Start</button>
<button class="control-btn" onclick="stop(event)">Stop</button>
<button class="control-btn" onclick="reset(event,180)">Reset</button>
</div>
</div>

<div class="drill-card" onclick="toggle(this,300)">
<h3>Shooting</h3>
<div class="hidden">
<p class="timer">300</p>
<button class="control-btn" onclick="start(event)">Start</button>
<button class="control-btn" onclick="stop(event)">Stop</button>
<button class="control-btn" onclick="reset(event,300)">Reset</button>
</div>
</div>

<div class="drill-card" onclick="toggle(this,240)">
<h3>Ball Control</h3>
<div class="hidden">
<p class="timer">240</p>
<button class="control-btn" onclick="start(event)">Start</button>
<button class="control-btn" onclick="stop(event)">Stop</button>
<button class="control-btn" onclick="reset(event,240)">Reset</button>
</div>
</div>

<div class="drill-card" onclick="toggle(this,360)">
<h3>Speed</h3>
<div class="hidden">
<p class="timer">360</p>
<button class="control-btn" onclick="start(event)">Start</button>
<button class="control-btn" onclick="stop(event)">Stop</button>
<button class="control-btn" onclick="reset(event,360)">Reset</button>
</div>
</div>

</div>
</div>

<!-- PROGRESS -->
<div id="progress" class="section">
<h2>Progress</h2>
<p>Completed drills: <span id="count">0</span></p>
</div>

<script>
let count = 0;
let interval;

/* NAV */
function show(id){
    document.querySelectorAll('.section').forEach(s=>s.classList.remove('active'));
    document.getElementById(id).classList.add('active');
}

/* OPEN/CLOSE CARD */
function toggle(card,time){
    document.querySelectorAll('.drill-card').forEach(c=>{
        if(c!==card){
            c.classList.remove('active');
            c.querySelector('div').classList.add('hidden');
        }
    });

    card.classList.toggle('active');
    card.querySelector('div').classList.toggle('hidden');
}

/* TIMER */
function start(e){
    e.stopPropagation();
    let timer = e.target.parentElement.querySelector('.timer');

    interval = setInterval(()=>{
        timer.innerText--;

        if(timer.innerText <= 0){
            clearInterval(interval);
            count++;
            document.getElementById("count").innerText = count;
        }
    },1000);
}

function stop(e){
    e.stopPropagation();
    clearInterval(interval);
}

function reset(e,time){
    e.stopPropagation();
    clearInterval(interval);
    e.target.parentElement.querySelector('.timer').innerText = time;
}
</script>

</body>
</html>
