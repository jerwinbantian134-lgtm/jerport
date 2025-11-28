<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>My Portfolio</title>
<style>
html, body {
  margin:0; padding:0;
  width:100%; height:100%;
  font-family:'Poppins', sans-serif;
  background:#001011;
  display:flex; justify-content:center; align-items:center;
  overflow:hidden;
}

/* PARTICLES */
#particles { position:fixed; inset:0; z-index:0; pointer-events:none; }
.particle { position:absolute; width:6px; height:6px; background:rgba(0,255,255,0.6); border-radius:50%; animation:float 5s linear infinite; opacity:0; }
@keyframes float { 0%{transform:translateY(100vh) scale(0.6);opacity:0;} 10%{opacity:1;} 100%{transform:translateY(-10vh) scale(1);opacity:0;} }

/* PAGE CONTAINER */
.pages-container { position:relative; width:100%; height:100%; z-index:1; }

/* PAGE */
.page {
  position:absolute; top:50%; left:50%;
  transform:translate(-50%,-50%) translateX(40px);
  width:90vw; height:90vh;
  background:rgba(255,255,255,0.06);
  border-radius:25px;
  display:flex; flex-direction:column; align-items:center; text-align:center;
  padding:20px; box-sizing:border-box;
  opacity:0; transition:0.5s ease;
}
.page.active { opacity:1; transform:translate(-50%,-50%) translateX(0); z-index:2; }

/* PROFILE IMAGE */
.profile { width:28%; border-radius:50%; object-fit:cover; border:5px solid rgba(255,255,255,0.8); box-shadow:0 0 20px rgba(0,255,255,0.7); margin-bottom:10px; }

/* STANDARD IMAGE */
.page-image { width:95%; max-height:55%; border-radius:15px; border:6px solid rgba(0,255,255,0.8); box-shadow:0 0 25px rgba(0,255,255,0.7); object-fit:contain; margin:10px 0; }

/* EDUCATIONAL IMAGE */
.education-image { width:135%; max-height:55%; border-radius:20px; border:8px solid rgba(0,255,255,0.8); box-shadow:0 0 25px rgba(0,255,255,0.7); object-fit:contain; margin:10px 0; }

/* FAMILY GRID */
.family-container { display:flex; justify-content:center; gap:10px; margin-top:10px; width:100%; flex-wrap:wrap; }
.family-card { width:30%; display:flex; flex-direction:column; align-items:center; }
.family-image { width:100%; aspect-ratio:1/1; border-radius:12px; border:4px solid rgba(0,255,255,0.8); box-shadow:0 0 15px rgba(0,255,255,0.7); object-fit:cover; }
.family-desc { font-size:0.85rem; margin-top:5px; color:white; }

/* TEXT */
h2,p{color:white;margin:5px 0;}

/* BUTTONS */
.nav{margin-top:auto;display:flex;gap:15px;}
.btn{padding:10px 25px;background:#d3d3d3;color:#013233;border-radius:25px;font-weight:700;cursor:pointer;z-index:3;pointer-events:auto;}
.btn:hover{background:#00ffe5;transform:scale(1.1);}
</style>
</head>
<body>

<div id="particles"></div>

<div class="pages-container">
  <!-- PAGE 1 -->
  <div class="page active" id="page1">
    <img src="profile.png" class="profile">
    <h2>WHO I AM</h2>
    <p style="font-size:0.88rem; max-width:95%; line-height:1.4em;">
      I’ve always been drawn to the digital world, especially how ideas can turn into real opportunities online.  
      What started as curiosity became a passion for creating digital products that simplify work and help people achieve their goals.  
      I enjoy building tools, refining systems, and experimenting to make everyday work more efficient.  
      Creative thinking and problem solving drive me to keep improving every day.
    </p>
    <div class="nav">
      <div class="btn" onclick="nextPage()">Next</div>
    </div>
  </div>

  <!-- PAGE 2 -->
  <div class="page" id="page2">
    <h2 style="font-size:1.2em;">Educational Background</h2>
    <img src="education.png" class="education-image">
    <div class="nav">
      <div class="btn" onclick="prevPage()">Previous</div>
      <div class="btn" onclick="nextPage()">Next</div>
    </div>
  </div>

  <!-- PAGE 3 -->
  <div class="page" id="page3">
    <h2>My Achievements</h2>
    <img src="achivements.png" class="page-image" style="width:130%; max-height:55%;">
    <div class="nav">
      <div class="btn" onclick="prevPage()">Previous</div>
      <div class="btn" onclick="nextPage()">Next</div>
    </div>
  </div>

  <!-- PAGE 4 -->
  <div class="page" id="page4">
    <h2 style="font-size:1.2em;">My Family</h2>
    <div class="family-container">
      <div class="family-card">
        <img src="father.png" class="family-image" style="width:90%;">
        <p class="family-desc">FATHER — A great husband who always shows up for our family. He works hard, provides for us, and still comes home ready to cook. Dependable, consistent, and quietly strong.</p>
      </div>
      <div class="family-card">
        <img src="mother.png" class="family-image" style="width:90%;">
        <p class="family-desc">MOTHER — The heart of our home, loving, warm, and endlessly kind. She gives comfort, shows resilience, and taught me to believe in women’s strength through the way she carries herself.</p>
      </div>
      <div class="family-card">
        <img src="siblings.png" class="family-image" style="width:90%;">
        <p class="family-desc">SIBLINGS — My siblings hate the camera but are full of personality. My brother is wild yet introverted, surprising once you know him. My sister, the youngest, is a dreamer, always lost in her own world. Their quirks make our home lively and full of character.</p>
      </div>
    </div>
    <div class="nav">
      <div class="btn" onclick="prevPage()">Previous</div>
    </div>
  </div>
</div>

<script>
let currentPage = 1;
const totalPages = 4;

function showPage(num){
  document.querySelectorAll('.page').forEach((p,i)=>{
    p.classList.toggle('active', i+1===num);
  });
}

function nextPage(){ if(currentPage<totalPages) currentPage++; showPage(currentPage); }
function prevPage(){ if(currentPage>1) currentPage--; showPage(currentPage); }

/* PARTICLES */
const particleContainer = document.getElementById("particles");
const particleCount = 30;
for(let i=0;i<particleCount;i++){
  let p = document.createElement("div");
  p.classList.add("particle");
  p.style.left = Math.random()*100 + "vw";
  p.style.animationDelay = (i*0.5)+"s";
  particleContainer.appendChild(p);
}
</script>
</body>
</html>
