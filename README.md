<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Soccer Training Pro</title>

<style>
body{
    margin:0;
    font-family:Arial, sans-serif;
    background:#d9d9d9;
    overflow-x:hidden;
}
.container{
    max-width:1200px;
    margin:auto;
    padding:20px;
}

/* NAVBAR */
nav{
    display:flex;
    justify-content:space-between;
    align-items:center;
    background:#e6d8bd;
    padding:15px 25px;
    border-radius:20px;
}
nav .links{
    display:flex;
    gap:30px;
}
nav a{
    text-decoration:none;
    color:#000;
    font-weight:bold;
    cursor:pointer;
    position:relative;
}
nav a::after{
    content:'';
    position:absolute;
    left:0;
    bottom:-4px;
    width:0;
    height:2px;
    background:#000;
    transition:width .25s ease-out;
}
nav a:hover::after{
    width:100%;
}
nav input{
    padding:5px 10px;
    border-radius:20px;
    border:none;
    width:200px;
}
nav button{
    padding:5px 10px;
    border-radius:10px;
    cursor:pointer;
    background:#fff;
    border:none;
    position:relative;
    overflow:hidden;
}
nav button::after{
    content:'';
    position:absolute;
    width:0;
    height:0;
    top:50%;
    left:50%;
    background:rgba(0,0,0,0.15);
    border-radius:50%;
    transform:translate(-50%,-50%);
    transition:width .3s ease-out, height .3s ease-out;
}
nav button:active::after{
    width:200%;
    height:200%;
}

/* SECTIONS */
.section{
    position:absolute;
    width:100%;
    top:120px;
    left:100%;
    transition:left 0.6s ease-in-out;
    opacity:0;
}
.section.active{
    left:0;
    opacity:1;
}

/* HOME – HERO */
#home{
    text-align:center;
}
.home-hero{
    display:flex;
    justify-content:center;
    text-align:center;
    padding:40px 20px 10px 20px;
}
.home-hero-text{
    max-width:700px;
    animation:fadeDown 0.9s ease-out;
}
.hero-title{
    font-size:55px;
    font-weight:bold;
    margin:0;
}
.hero-subtitle{
    font-size:28px;
    margin-top:10px;
    color:#333;
    font-weight:bold;
}
.hero-desc{
    margin-top:10px;
    font-size:18px;
    color:#444;
}
.hero-btn{
    margin-top:20px;
    background:#000;
    color:#fff;
    padding:12px 30px;
    border:none;
    border-radius:12px;
    cursor:pointer;
    font-size:18px;
    transition:transform 0.2s, box-shadow 0.2s, background 0.2s, color 0.2s;
    box-shadow:0 0 10px #000;
    position:relative;
    overflow:hidden;
}
.hero-btn::after{
    content:'';
    position:absolute;
    width:0;
    height:0;
    top:50%;
    left:50%;
    background:rgba(255,255,255,0.25);
    border-radius:50%;
    transform:translate(-50%,-50%);
    transition:width .35s ease-out, height .35s ease-out;
}
.hero-btn:active::after{
    width:220%;
    height:220%;
}
.hero-btn:hover{
    background:#0f0;
    color:#000;
    box-shadow:0 0 20px #0f0;
    transform:translateY(-2px);
}

/* GOAT ROW */
.goat-row{
    display:flex;
    justify-content:center;
    gap:20px;
    margin-top:10px;
    padding-bottom:20px;
}
.goat-card{
    width:160px;
    height:200px;
    border-radius:15px;
    overflow:hidden;
    background:#ccc;
    transition:transform .2s, box-shadow .2s;
    animation:fadeUp 0.8s ease-out;
    transform-origin:center bottom;
}
.goat-card img{
    width:100%;
    height:100%;
    object-fit:cover;
    border-radius:inherit;
}
.goat-card:hover{
    transform:scale(1.06) rotate(-1.5deg) translateY(-4px);
    box-shadow:0 0 20px rgba(0,0,0,0.4);
}

/* TRAINING GRID */
#training{
    padding:20px;
}
#training h2{
    animation:fadeDown 0.8s ease-out;
}
.grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
    gap:20px;
    margin-top:10px;
}

/* DRILL CARDS */
.drill{
    background:#fff;
    border-radius:15px;
    padding-bottom:20px;
    text-align:center;
    cursor:pointer;
    transition:transform .2s, box-shadow .2s;
    box-shadow:0 0 10px rgba(0,0,0,0.1);
    animation:fadeUp 0.8s ease-out;
}
.drill:hover{
    transform:translateY(-5px) scale(1.03);
    box-shadow:0 0 20px #0f0;
}
.drill-header{
    padding:20px;
}
.hidden{
    display:none;
}
.timer{
    margin-top:10px;
    font-weight:bold;
}

/* TIMER BUTTONS */
button.timer-btn{
    background:linear-gradient(45deg,#0f0,#00f);
    color:#fff;
    font-weight:bold;
    padding:10px 20px;
    border:none;
    border-radius:50px;
    cursor:pointer;
    transition:transform 0.15s, box-shadow 0.15s, filter 0.15s;
    box-shadow:0 5px 15px rgba(0,0,0,0.3);
    margin:5px 3px;
    position:relative;
    overflow:hidden;
}
button.timer-btn::after{
    content:'';
    position:absolute;
    width:0;
    height:0;
    top:50%;
    left:50%;
    background:rgba(255,255,255,0.25);
    border-radius:50%;
    transform:translate(-50%,-50%);
    transition:width .3s ease-out, height .3s ease-out;
}
button.timer-btn:active::after{
    width:220%;
    height:220%;
}
button.timer-btn:hover{
    transform:scale(1.08) translateY(-1px);
    box-shadow:0 0 20px #0f0,0 0 10px #00f;
    filter:brightness(1.05);
}

/* VIDEO BUTTON */
.video-btn{
    display:inline-block;
    margin-top:10px;
    padding:8px 15px;
    background:#ff0000;
    color:#fff;
    border-radius:8px;
    text-decoration:none;
    font-weight:bold;
    transition:transform 0.15s, box-shadow 0.15s, background 0.15s;
}
.video-btn:hover{
    background:#cc0000;
    transform:scale(1.06) translateY(-1px);
    box-shadow:0 0 12px rgba(0,0,0,0.4);
}

/* PROGRESS */
#progress{
    padding:20px;
}
#progress h2{
    animation:fadeDown 0.8s ease-out;
}
#progress p{
    font-size:18px;
    animation:fadeUp 0.8s ease-out;
}

/* HEALTHY DIET */
#healthy{
    padding:20px;
}
#healthy h2{
    animation:fadeDown 0.8s ease-out;
}
.health-content{
    margin-top:20px;
    background:#fff;
    padding:20px;
    border-radius:15px;
    box-shadow:0 0 10px rgba(0,0,0,0.1);
    animation:fadeUp 0.8s ease-out;
}
.health-content h3{
    margin-top:0;
}

/* ANIMATIONS */
@keyframes fadeDown{
    from{opacity:0;transform:translateY(-20px);}
    to{opacity:1;transform:translateY(0);}
}
@keyframes fadeUp{
    from{opacity:0;transform:translateY(20px);}
    to{opacity:1;transform:translateY(0);}
}

/* RESPONSIVE */
@media(max-width:768px){
    .goat-row{
        flex-wrap:wrap;
    }
    .goat-card{
        width:130px;
        height:170px;
    }
    .hero-title{
        font-size:40px;
    }
    .hero-subtitle{
        font-size:22px;
    }
}
</style>
</head>

<body>
<div class="container">

<nav>
    <div><b>Soccer</b></div>
    <div class="links">
        <a onclick="showSection('home')">HOME</a>
        <a onclick="showSection('training')">TRAINING</a>
        <a onclick="showSection('progress')">PROGRESS</a>
    </div>
    <input id="searchBar" placeholder="Search...">
    <button onclick="showSection('healthy')">HEALTHY DIET</button>
</nav>

<!-- HOME -->
<div id="home" class="section active">
    <div class="home-hero">
        <div class="home-hero-text">
            <h1 class="hero-title">Soccer Training<br>Become Pro</h1>
            <h2 class="hero-subtitle">Train Like These GOATS</h2>
            <p class="hero-desc">Customize your drills, track your progress, and test your reaction time.</p>
            <button class="hero-btn" onclick="showSection('training')">SKILLS</button>
        </div>
    </div>

    <div class="goat-row">
        <div class="goat-card"><img src="soccerball.jpg" alt="Soccer Ball"></div>
        <div class="goat-card"><img src="ronaldo.jpg" alt="Ronaldo"></div>
        <div class="goat-card"><img src="messi.jpg" alt="Messi"></div>
        <div class="goat-card"><img src="maradona.jpg" alt="Maradona"></div>
        <div class="goat-card"><img src="pele.jpg" alt="Pele"></div>
    </div>
</div>

<!-- TRAINING -->
<div id="training" class="section">
<h2>Training Drills</h2>

<div class="grid">

<div class="drill">
    <div class="drill-header" onclick="toggleDrill(this)">
        <h3>Dribbling</h3>
        <p>Control & moves</p>
    </div>
    <div class="hidden">
        <div class="timer">300s</div>
        <button class="timer-btn" onclick="start(event)">Start</button>
        <button class="timer-btn" onclick="stopTimer(event)">Stop</button>
        <button class="timer-btn" onclick="reset(event,300)">Reset</button>
        <a class="video-btn" href="https://www.youtube.com/watch?v=ziXYzblzgzQ" target="_blank">Watch Tutorial</a>
    </div>
</div>

<div class="drill">
    <div class="drill-header" onclick="toggleDrill(this)">
        <h3>Passing</h3>
        <p>Accuracy & vision</p>
    </div>
    <div class="hidden">
        <div class="timer">300s</div>
        <button class="timer-btn" onclick="start(event)">Start</button>
        <button class="timer-btn" onclick="stopTimer(event)">Stop</button>
        <button class="timer-btn" onclick="reset(event,300)">Reset</button>
        <a class="video-btn" href="https://www.youtube.com/watch?v=JqxwTcpf07w" target="_blank">Watch Tutorial</a>
    </div>
</div>

<div class="drill">
    <div class="drill-header" onclick="toggleDrill(this)">
        <h3>Shooting</h3>
        <p>Power & finishing</p>
    </div>
    <div class="hidden">
        <div class="timer">600s</div>
        <button class="timer-btn" onclick="start(event)">Start</button>
        <button class="timer-btn" onclick="stopTimer(event)">Stop</button>
        <button class="timer-btn" onclick="reset(event,600)">Reset</button>
        <a class="video-btn" href="https://www.youtube.com/watch?v=JqxwTcpf07w" target="_blank">Watch Tutorial</a>
    </div>
</div>

<div class="drill">
    <div class="drill-header" onclick="toggleDrill(this)">
        <h3>Ball Control</h3>
        <p>First touch mastery</p>
    </div>
    <div class="hidden">
        <div class="timer">240s</div>
        <button class="timer-btn" onclick="start(event)">Start</button>
        <button class="timer-btn" onclick="stopTimer(event)">Stop</button>
        <button class="timer-btn" onclick="reset(event,240)">Reset</button>
        <a class="video-btn" href="https://www.youtube.com/watch?v=FqZArr8E56E" target="_blank">Watch Tutorial</a>
    </div>
</div>

<div class="drill">
    <div class="drill-header" onclick="toggleDrill(this)">
        <h3>Speed & Agility</h3>
        <p>Explosiveness</p>
    </div>
    <div class="hidden">
        <div class="timer">360s</div>
        <button class="timer-btn" onclick="start(event)">Start</button>
        <button class="timer-btn" onclick="stopTimer(event)">Stop</button>
        <button class="timer-btn" onclick="reset(event,360)">Reset</button>
        <a class="video-btn" href="https://www.youtube.com/watch?v=oYgfODvpt58" target="_blank">Watch Tutorial</a>
    </div>
</div>

<div class="drill">
    <div class="drill-header" onclick="toggleDrill(this)">
        <h3>Endurance Run</h3>
        <p>Improve stamina</p>
    </div>
    <div class="hidden">
        <div class="timer">600s</div>
        <button class="timer-btn" onclick="start(event)">Start</button>
        <button class="timer-btn" onclick="stopTimer(event)">Stop</button>
        <button class="timer-btn" onclick="reset(event,600)">Reset</button>
        <a class="video-btn" href="https://www.youtube.com/watch?v=-GwdRuBX2Fo" target="_blank">Watch Tutorial</a>
    </div>
</div>

<div class="drill">
    <div class="drill-header" onclick="toggleDrill(this)">
        <h3>Reflex Drill</h3>
        <p>Quick reflexes</p>
    </div>
    <div class="hidden">
        <div class="timer">300s</div>
        <button class="timer-btn" onclick="start(event)">Start</button>
        <button class="timer-btn" onclick="stopTimer(event)">Stop</button>
        <button class="timer-btn" onclick="reset(event,300)">Reset</button>
        <a class="video-btn" href="https://www.youtube.com/watch?v=N-TuSZtyqPY" target="_blank">Watch Tutorial</a>
    </div>
</div>

<div class="drill">
    <div class="drill-header" onclick="toggleDrill(this)">
        <h3>Headers Practice</h3>
        <p>Jump & accuracy</p>
    </div>
    <div class="hidden">
        <div class="timer">300s</div>
        <button class="timer-btn" onclick="start(event)">Start</button>
        <button class="timer-btn" onclick="stopTimer(event)">Stop</button>
        <button class="timer-btn" onclick="reset(event,300)">Reset</button>
        <a class="video-btn" href="https://www.youtube.com/watch?v=Fyp4M70M6Hw&t=576s" target="_blank">Watch Tutorial</a>
    </div>
</div>

<div class="drill">
    <div class="drill-header" onclick="toggleDrill(this)">
        <h3>Reaction Time</h3>
        <p>Instant response</p>
    </div>
    <div class="hidden">
        <div class="timer">300s</div>
        <button class="timer-btn" onclick="start(event)">Start</button>
        <button class="timer-btn" onclick="stopTimer(event)">Stop</button>
        <button class="timer-btn" onclick="reset(event,300)">Reset</button>
        <a class="video-btn" href="https://www.youtube.com/watch?v=8ZxbHcMVqQ8" target="_blank">Watch Tutorial</a>
    </div>
</div>

<div class="drill">
    <div class="drill-header" onclick="toggleDrill(this)">
        <h3>Tackling Drills</h3>
        <p>Defensive strength</p>
    </div>
    <div class="hidden">
        <div class="timer">300s</div>
        <button class="timer-btn" onclick="start(event)">Start</button>
        <button class="timer-btn" onclick="stopTimer(event)">Stop</button>
        <button class="timer-btn" onclick="reset(event,300)">Reset</button>
        <a class="video-btn" href="https://www.youtube.com/watch?v=4vBZzkVRqbE" target="_blank">Watch Tutorial</a>
    </div>
</div>

</div>
</div>

<!-- PROGRESS -->
<div id="progress" class="section">
    <h2>Progress</h2>
    <p>Drills completed: <span id="count">0</span></p>
</div>

<!-- HEALTHY DIET -->
<div id="healthy" class="section">
    <h2>Healthy Diet & Sleep</h2>
    <div class="health-content">
        <h3>Nutrition</h3>
        <ul>
            <li>Lean protein: chicken, fish, eggs</li>
            <li>Complex carbs: brown rice, oats, whole wheat bread</li>
            <li>Fruits & vegetables: bananas, berries, spinach, broccoli</li>
            <li>Healthy fats: avocado, nuts, olive oil</li>
        </ul>

        <h3>Sleep</h3>
        <p>Get 8–10 hours of sleep per night for recovery and performance.</p>
    </div>
</div>

<script>
let intervals = new Map();
let openDrillCard = null;
let completed = 0;

function showSection(id){
    const current = document.querySelector('.section.active');
    if(current && current.id === id) return;
    if(current) current.classList.remove('active');
    document.getElementById(id).classList.add('active');
}

function toggleDrill(header){
    let drill = header.parentElement;
    let hidden = drill.querySelector('.hidden');

    if (hidden.style.display === 'block') {
        hidden.style.display = 'none';
        openDrillCard = null;
        return;
    }

    if (openDrillCard) {
        openDrillCard.querySelector('.hidden').style.display = 'none';
    }

    hidden.style.display = 'block';
    openDrillCard = drill;
}

function start(e){
    e.stopPropagation();
    let drill = e.target.closest('.drill');

    if (intervals.get(drill)) return;

    let timer = drill.querySelector('.timer');
    let t = parseInt(timer.textContent);

    let i = setInterval(() => {
        t--;
        timer.textContent = t + 's';

        if (t <= 0) {
            clearInterval(i);
            intervals.delete(drill);
            completed++;
            document.getElementById('count').textContent = completed;
        }
    }, 1000);

    intervals.set(drill, i);
}

function stopTimer(e){
    e.stopPropagation();
    let drill = e.target.closest('.drill');
    clearInterval(intervals.get(drill));
    intervals.delete(drill);
}

function reset(e, time){
    e.stopPropagation();
    let drill = e.target.closest('.drill');
    clearInterval(intervals.get(drill));
    intervals.delete(drill);
    drill.querySelector('.timer').textContent = time + 's';
}

document.getElementById('searchBar').addEventListener('keyup', function(e){
    let value = e.target.value.toLowerCase();
    if (value.includes('home')) showSection('home');
    else if (value.includes('training') || value.includes('skills')) showSection('training');
    else if (value.includes('healthy') || value.includes('diet') || value.includes('sleep')) showSection('healthy');
    else if (value.includes('progress')) showSection('progress');
});
</script>

</body>
</html>
