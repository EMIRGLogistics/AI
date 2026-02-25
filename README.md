<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EMIRG AI | Strategic AI for Global Supply Chains</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>
:root{
--black:#0d0d0d;
--gold:#C6A75E;
--gray:#9a9a9a;
--light-gray:#cfcfcf;
--divider:rgba(255,255,255,0.06);
--hover-scale:1.03;
}

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Inter',sans-serif;
scroll-behavior:smooth;
}

body{
background:var(--black);
color:white;
line-height:1.6;
transition:background 0.3s;
}

.container{
width:88%;
max-width:1100px;
margin:auto;
}

/* HEADER */
header{
position:fixed;
top:0;
width:100%;
background:rgba(13,13,13,0.97);
border-bottom:1px solid var(--divider);
z-index:1000;
}

.nav-wrapper{
display:flex;
justify-content:space-between;
align-items:center;
height:85px;
}

.logo{
font-weight:700;
letter-spacing:1px;
font-size:1.4rem;
color:white;
}

.logo span{
color:var(--gold);
}

nav ul{
display:flex;
gap:42px;
list-style:none;
align-items:center;
}

nav li{
height:100%;
display:flex;
align-items:center;
}

nav a{
position:relative;
text-decoration:none;
color:var(--light-gray);
font-weight:500;
font-size:0.9rem;
padding:8px 0;
transition:all 0.3s ease;
}

nav a::after{
content:'';
position:absolute;
left:0;
bottom:-6px;
width:0;
height:2px;
background:var(--gold);
transition:width 0.3s ease;
}

nav a:hover{
color:white;
transform:translateY(-1px);
}

nav a:hover::after{
width:100%;
}

/* HERO */
.hero{
position:relative;
padding-top:180px;
padding-bottom:140px;
border-bottom:1px solid var(--divider);
overflow:hidden;
transition:all 0.3s;
}

#networkCanvas{
position:absolute;
top:0;
left:0;
width:100%;
height:100%;
z-index:0;
opacity:0.25;
transition:opacity 0.3s ease;
}

.hero .container{
position:relative;
z-index:2;
}

.hero h1{
font-size:2.4rem;
font-weight:600;
margin-bottom:35px;
max-width:760px;
transition:transform 0.3s ease;
}

.hero p{
color:var(--gray);
max-width:600px;
margin-bottom:40px;
transition:transform 0.3s ease, color 0.3s ease;
}

.cta-btn{
display:inline-block;
padding:14px 36px;
border:1px solid var(--gold);
color:var(--gold);
text-decoration:none;
font-weight:600;
font-size:0.85rem;
letter-spacing:0.5px;
transition:all 0.3s ease;
background:none;
cursor:pointer;
transform:translateZ(0);
}

.cta-btn:hover{
background:var(--gold);
color:black;
transform:scale(var(--hover-scale));
}

/* SECTIONS */
section{
padding:130px 0;
border-bottom:1px solid var(--divider);
transition:all 0.3s ease;
}

.section-title{
font-size:1.8rem;
font-weight:600;
margin-bottom:70px;
}

.grid{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(260px,1fr));
gap:60px;
}

.card{
padding-top:10px;
transition:all 0.3s ease;
cursor:pointer;
}

.card:hover{
transform:scale(var(--hover-scale));
}

.card h3{
font-weight:600;
margin-bottom:12px;
transition:color 0.3s ease;
}

.card p{
color:var(--gray);
margin-bottom:12px;
transition:color 0.3s ease;
}

.metric{
color:var(--gold);
font-weight:600;
font-size:0.9rem;
transition:color 0.3s ease;
}

/* REVIEWS */
.review{
background:#141414;
padding:30px;
border-radius:4px;
transition:transform 0.3s ease;
cursor:pointer;
}

.review:hover{
transform:scale(var(--hover-scale));
}

.review p{
color:var(--gray);
margin-bottom:15px;
font-style:italic;
transition:color 0.3s ease;
}

.review strong{
color:white;
font-size:0.85rem;
transition:color 0.3s ease;
}

/* ESTIMATOR */
.estimator{
max-width:650px;
}

select{
width:100%;
padding:14px;
margin-bottom:20px;
background:#111;
color:white;
border:1px solid var(--divider);
transition:all 0.3s ease;
}

select:hover, select:focus{
border-color:var(--gold);
transform:scale(1.01);
}

/* FORM */
form{
max-width:650px;
}

form input, form textarea{
width:100%;
padding:14px;
margin-bottom:20px;
background:#111;
border:1px solid var(--divider);
color:white;
transition:all 0.3s ease;
}

form input:hover, form input:focus,
form textarea:hover, form textarea:focus{
border-color:var(--gold);
transform:scale(1.01);
}

/* FADE */
.fade{
opacity:0;
transform:translateY(25px);
transition:all 0.8s ease;
}

.fade.visible{
opacity:1;
transform:translateY(0);
}

/* MOBILE */
@media(max-width:768px){
.nav-wrapper{
flex-direction:column;
height:auto;
padding:20px 0;
gap:20px;
}
nav ul{
flex-wrap:wrap;
justify-content:center;
gap:20px;
}
.hero h1{
font-size:1.8rem;
}
}
</style>
</head>

<body>

<header>
<div class="container nav-wrapper">
<div class="logo">EMIRG <span>AI</span></div>
<nav>
<ul>
<li><a href="#solutions">Solutions</a></li>
<li><a href="#insights">Insights</a></li>
<li><a href="#reviews">Perspectives</a></li>
<li><a href="#estimator">AI Estimator</a></li>
<li><a href="#contact">Engage</a></li>
</ul>
</nav>
</div>
</header>

<section class="hero fade">
<canvas id="networkCanvas"></canvas>
<div class="container">
<h1>AI Strategy for Global Logistics & Supply Chain Leadership</h1>
<p>Operational visibility. Predictive precision. Autonomous execution across complex global networks.</p>
<a href="#contact" class="cta-btn">Request Strategic Assessment →</a>
</div>
</section>

<section id="solutions" class="fade">
<div class="container">
<h2 class="section-title">Advisory Solutions</h2>
<div class="grid">

<div class="card">
<h3>Operational Mapping</h3>
<p>End-to-end AI visibility frameworks identifying structural inefficiencies.</p>
<div class="metric">18–30% Potential Cost Reduction</div>
</div>

<div class="card">
<h3>Forecasting & Demand Planning</h3>
<p>Advanced predictive models stabilizing demand volatility.</p>
<div class="metric">25–35% Forecast Accuracy Improvement</div>
</div>

<div class="card">
<h3>Intelligent Autonomy</h3>
<p>Autonomous execution systems enhancing decision velocity.</p>
<div class="metric">2–3x Faster Operational Decisions</div>
</div>

<div class="card">
<h3>AI Risk & Resilience Modeling</h3>
<p>Scenario modeling to mitigate systemic supply disruptions.</p>
<div class="metric">20–40% Risk Exposure Reduction</div>
</div>

</div>
</div>
</section>

<section id="insights" class="fade">
<div class="container">
<h2 class="section-title">AI Market Insights</h2>
<p style="color:var(--gray);max-width:700px;">
AI adoption across global logistics networks is accelerating rapidly, with enterprises deploying control tower intelligence,
predictive demand stabilization, and autonomous execution layers to compress cost structures while increasing resilience.
</p>
</div>
</section>

<section id="reviews" class="fade">
<div class="container">
<h2 class="section-title">Client Perspectives</h2>
<div class="grid">

<div class="review">
<p>"EMIRG AI materially improved our supply chain transparency and execution speed."</p>
<strong>COO, Global Freight Enterprise</strong>
</div>

<div class="review">
<p>"Forecast stability improved significantly across multi-region operations."</p>
<strong>VP Supply Chain Strategy</strong>
</div>

<div class="review">
<p>"Autonomous optimization reduced cost leakage across our network."</p>
<strong>Director of Logistics Innovation</strong>
</div>

<div class="review">
<p>"Resilience modeling gave clarity during volatile macro shifts."</p>
<strong>Chief Strategy Officer</strong>
</div>

</div>
</div>
</section>

<section id="estimator" class="fade">
<div class="container">
<h2 class="section-title">AI Readiness & ROI Estimator</h2>
<div class="estimator">
<select id="companySize">
<option value="">Company Size</option>
<option value="1">Small (1-100)</option>
<option value="2">Mid-Market (100-1000)</option>
<option value="3">Enterprise (1000+)</option>
</select>

<select id="complexity">
<option value="">Operational Complexity</option>
<option value="1">Single Region</option>
<option value="2">Multi-Region</option>
<option value="3">Global Network</option>
</select>

<div class="result" id="result"></div>
<button class="cta-btn" onclick="transferEstimator()">Continue to Strategic Inquiry →</button>
</div>
</div>
</section>

<section id="contact" class="fade">
<div class="container">
<h2 class="section-title">Strategic Inquiry</h2>
<form onsubmit="sendEmail(); return false;">
<input type="text" id="name" placeholder="Full Name" required>
<input type="text" id="company" placeholder="Company Name" required>
<textarea id="message" placeholder="Describe your objectives..." required></textarea>
<button class="cta-btn" type="submit">Submit Strategic Request →</button>
</form>
</div>
</section>

<footer class="fade">
<div class="container" style="text-align:center;color:var(--gray);padding:40px 0;font-size:0.85rem;">
© 2026 EMIRG AI. All rights reserved.
</div>
</footer>

<script>
/* ROI Calculator */
let storedData="";
document.getElementById("complexity").addEventListener("change", calculateROI);
function calculateROI(){
let size=parseInt(document.getElementById("companySize").value);
let complexity=parseInt(document.getElementById("complexity").value);
if(size && complexity){
let score=size*complexity;
let roi=(score*8)+10;
storedData=`AI Readiness Assessment:
Company Size Score: ${size}
Complexity Score: ${complexity}
Estimated ROI Potential: ${roi}%+
Recommended Engagement: Enterprise AI Transformation`;
document.getElementById("result").innerHTML=`Estimated ROI Potential: ${roi}%+`;
}
}
function transferEstimator(){
if(!storedData){
alert("Please complete the estimator selections.");
return;
}
document.getElementById("message").value=storedData+"\n\nObjectives:\n";
document.getElementById("contact").scrollIntoView({behavior:"smooth"});
}
function sendEmail(){
let name=document.getElementById("name").value;
let company=document.getElementById("company").value;
let message=document.getElementById("message").value;
window.location.href=
`mailto:logistics@emirg-group.com?subject=Strategic AI Inquiry - ${company}&body=Name: ${name}%0ACompany: ${company}%0A%0A${encodeURIComponent(message)}`;
}

/* Fade In */
const faders=document.querySelectorAll('.fade');
const observer=new IntersectionObserver(entries=>{
entries.forEach(entry=>{
if(entry.isIntersecting){
entry.target.classList.add('visible');
}
});
},{threshold:0.2});
faders.forEach(el=>observer.observe(el));

/* AI Network Background */
const canvas=document.getElementById("networkCanvas");
const ctx=canvas.getContext("2d");
let particles=[];
const particleCount=60;
function resizeCanvas(){canvas.width=canvas.offsetWidth; canvas.height=canvas.offsetHeight;}
resizeCanvas();
window.addEventListener("resize",resizeCanvas);
class Particle{constructor(){this.x=Math.random()*canvas.width; this.y=Math.random()*canvas.height; this.vx=(Math.random()-0.5)*0.4; this.vy=(Math.random()-0.5)*0.4; this.radius=2;}
update(){this.x+=this.vx; this.y+=this.vy; if(this.x<=0||this.x>=canvas.width)this.vx*=-1; if(this.y<=0||this.y>=canvas.height)this.vy*=-1;}
draw(){ctx.beginPath(); ctx.arc(this.x,this.y,this.radius,0,Math.PI*2); ctx.fillStyle="#C6A75E"; ctx.fill();}}
function init(){particles=[]; for(let i=0;i<particleCount;i++){particles.push(new Particle());}}
init();
function connect(){for(let a=0;a<particles.length;a++){for(let b=a;b<particles.length;b++){let dx=particles[a].x-particles[b].x; let dy=particles[a].y-particles[b].y; let distance=dx*dx+dy*dy; if(distance<12000){ctx.beginPath(); ctx.strokeStyle="rgba(198,167,94,0.08)"; ctx.lineWidth=1; ctx.moveTo(particles[a].x,particles[a].y); ctx.lineTo(particles[b].x,particles[b].y); ctx.stroke();}}}}
function animate(){ctx.clearRect(0,0,canvas.width,canvas.height); particles.forEach(p=>{p.update();p.draw();}); connect(); requestAnimationFrame(animate);}
animate();
</script>

</body>
</html>
