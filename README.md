<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mis XV - Angélica</title>

  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">

  <style>
    :root{
      --celeste:#bfe6ff;
      --dorado:#f7d37b;
      --card: rgba(255,255,255,.10);
      --card2: rgba(255,255,255,.06);
      --borde: rgba(255,255,255,.22);
      --texto: rgba(255,255,255,.92);
    }

    *{box-sizing:border-box}
    body{
      margin:0;
      font-family:'Poppins', sans-serif;
      color:var(--texto);
      background: radial-gradient(1200px 800px at 50% 10%, #2a6aa1 0%, #132a3a 45%, #0b1018 100%);
      overflow-x:hidden;
      min-height:100vh;
    }

    /* Fondo de estrellas */
    canvas{
      position:fixed;
      inset:0;
      z-index:-2;
    }

    /* Glow decorativo */
    .glow{
      position:fixed;
      inset:-20%;
      background:
        radial-gradient(circle at 25% 20%, rgba(191,230,255,.25), transparent 40%),
        radial-gradient(circle at 75% 30%, rgba(247,211,123,.15), transparent 45%),
        radial-gradient(circle at 50% 85%, rgba(191,230,255,.12), transparent 55%);
      filter: blur(10px);
      z-index:-1;
      pointer-events:none;
    }

    .wrap{
      max-width:520px;
      margin:0 auto;
      padding:28px 18px 60px;
    }

    .card{
      background: linear-gradient(180deg, var(--card), var(--card2));
      border: 1px solid var(--borde);
      border-radius:22px;
      padding:22px 18px;
      backdrop-filter: blur(12px);
      box-shadow: 0 18px 60px rgba(0,0,0,.35);
    }

    .top{
      text-align:center;
      padding:18px 10px 10px;
      animation: pop 900ms ease both;
    }

    @keyframes pop{
      0%{opacity:0; transform: translateY(18px) scale(.98)}
      100%{opacity:1; transform: translateY(0) scale(1)}
    }

    .titulo{
      font-family:'Great Vibes', cursive;
      font-size:64px;
      line-height:1;
      margin:0;
      color:var(--celeste);
      text-shadow: 0 0 18px rgba(191,230,255,.25);
    }

    .sub{
      margin:8px 0 0;
      font-weight:300;
      opacity:.92;
    }

    .nombre{
      margin:8px 0 2px;
      font-size:26px;
      font-weight:600;
      color:#ffffff;
      text-shadow: 0 0 16px rgba(255,255,255,.15);
    }

    .quince{
      margin:4px 0 0;
      font-size:18px;
      opacity:.95;
    }

    .divider{
      height:1px;
      background: linear-gradient(90deg, transparent, rgba(255,255,255,.35), transparent);
      margin:18px 0;
    }

    .grid{
      display:grid;
      gap:14px;
      margin-top:14px;
    }

    .box{
      padding:16px 14px;
      border-radius:18px;
      border:1px solid rgba(255,255,255,.18);
      background: rgba(0,0,0,.18);
    }

    .label{
      font-size:12px;
      letter-spacing:1px;
      text-transform:uppercase;
      opacity:.85;
      margin-bottom:6px;
    }

    .texto{
      font-size:14px;
      line-height:1.5;
      margin:0;
    }

    .resaltado{
      color: var(--celeste);
      font-weight:600;
    }

    .btns{
      display:grid;
      grid-template-columns:1fr;
      gap:10px;
      margin-top:14px;
    }

    button, a.btn{
      width:100%;
      border:none;
      padding:12px 14px;
      border-radius:16px;
      cursor:pointer;
      font-size:15px;
      font-weight:600;
      transition: transform .15s ease, opacity .15s ease;
      text-decoration:none;
      text-align:center;
      display:inline-block;
    }

    button:active, a.btn:active{ transform: scale(.98); }

    .btn-map{
      background: rgba(191,230,255,.18);
      border: 1px solid rgba(191,230,255,.35);
      color: #e9f7ff;
    }

    .btn-wsp{
      background: rgba(0,255,138,.14);
      border: 1px solid rgba(0,255,138,.28);
      color: #dbffe9;
    }

    .btn-yape{
      background: rgba(247,211,123,.14);
      border: 1px solid rgba(247,211,123,.35);
      color: #fff2cf;
    }

    .nota{
      font-size:12px;
      opacity:.82;
      margin-top:8px;
      text-align:center;
    }

    .countdown{
      display:grid;
      grid-template-columns: repeat(4, 1fr);
      gap:10px;
      margin-top:12px;
    }

    .cd{
      background: rgba(255,255,255,.08);
      border:1px solid rgba(255,255,255,.16);
      border-radius:16px;
      padding:10px 8px;
      text-align:center;
    }

    .cd .num{
      font-size:22px;
      font-weight:700;
      color: #ffffff;
    }
    .cd .txt{
      font-size:11px;
      opacity:.85;
      margin-top:2px;
    }

    .frase{
      text-align:center;
      margin:16px 0 0;
      font-style:italic;
      opacity:.92;
    }

    .toast{
      position:fixed;
      left:50%;
      bottom:18px;
      transform:translateX(-50%);
      background: rgba(0,0,0,.75);
      border:1px solid rgba(255,255,255,.16);
      color:#fff;
      padding:10px 14px;
      border-radius:999px;
      font-size:13px;
      opacity:0;
      pointer-events:none;
      transition: opacity .25s ease, transform .25s ease;
      z-index:50;
    }
    .toast.show{
      opacity:1;
      transform:translateX(-50%) translateY(-6px);
    }

    /* Música (opcional) */
    .music{
      display:flex;
      justify-content:center;
      margin-top:10px;
      gap:10px;
    }
    .music button{
      max-width:220px;
      background: rgba(255,255,255,.10);
      border:1px solid rgba(255,255,255,.18);
      color:#fff;
      font-weight:600;
    }
  </style>
</head>
<body>

<canvas id="stars"></canvas>
<div class="glow"></div>

<div class="wrap">
  <div class="card">
    <div class="top">
      <h1 class="titulo">Mis XV Años</h1>
      <p class="sub">“Mi cuento de hadas empieza aquí…”</p>

      <div class="divider"></div>

      <div class="nombre">Angélica Rodríguez Escobedo</div>
      <div class="quince">Te invita con mucha ilusión a celebrar sus <span class="resaltado">15 años</span></div>

      <div class="countdown" aria-label="Cuenta regresiva">
        <div class="cd"><div class="num" id="d">--</div><div class="txt">Días</div></div>
        <div class="cd"><div class="num" id="h">--</div><div class="txt">Horas</div></div>
        <div class="cd"><div class="num" id="m">--</div><div class="txt">Min</div></div>
        <div class="cd"><div class="num" id="s">--</div><div class="txt">Seg</div></div>
      </div>

      <div class="music">
        <button onclick="toggleMusic()">🎵 Música (opcional)</button>
      </div>

      <!-- Pon aquí un audio si deseas (MP3). Ejemplo:
      <audio id="bgm" loop>
        <source src="musica.mp3" type="audio/mpeg">
      </audio>
      -->
      <audio id="bgm" loop></audio>

      <p class="frase">“Acompáñame a vivir este día tan especial lleno de magia, sueños y alegría.”</p>
    </div>

    <div class="grid">

      <div class="box">
        <div class="label">Fecha & Hora</div>
        <p class="texto"><strong>14 de marzo</strong> • <strong>8:00 p.m.</strong></p>
      </div>

      <div class="box">
        <div class="label">Dirección</div>
        <p class="texto">
          Mz X Prima Lt 10 – Villa Huanchaco<br>
          <span style="opacity:.9">Referencia:</span> A 2 cuadras de la posta médica de Manuel Arévalo
        </p>

        <div class="btns">
          <a class="btn btn-map" target="_blank"
             href="https://maps.google.com/?q=-8.075103,-79.066162">
            📍 Abrir ubicación en Google Maps
          </a>
        </div>
      </div>

      <div class="box">
        <div class="label">Familia</div>
        <p class="texto" style="text-align:center;">
          <strong>Padres:</strong><br>
          Yosver Rodríguez Rodríguez<br>
          Jenny Escobedo Álvarez
          <br><br>
          <strong>Padrinos:</strong><br>
          Jhon Moreno Hurtado<br>
          Sharmin Rivas Eguizabal<br>
          Raúl Valle Pérez<br>
          Roxana Guerrero Narró
        </p>
      </div>

      <div class="box">
        <div class="label">Código de vestimenta</div>
        <p class="texto">
          <strong>Sport Elegante</strong><br><br>
          💙 El color <strong>CELESTE</strong> es exclusivo para la quinceañera.<br>
          Todos los demás colores están disponibles.
        </p>

        <div class="btns">
          <button class="btn-yape" onclick="copiarYape()">💫 Copiar Yape: +51 958735157</button>

          <a class="btn btn-wsp" target="_blank" id="btnWsp" href="#">
            ✅ Confirmar asistencia por WhatsApp
          </a>
        </div>

        <div class="nota">Tu yapeo será el mejor regalo ✨</div>
      </div>

    </div>
  </div>
</div>

<div class="toast" id="toast">Copiado ✨</div>

<script>
/* ========= WhatsApp con mensaje listo (solo NOMBRE) ========= */
const telWsp = "51958735157"; // SOLO números (receptor del WhatsApp)
const mensaje = encodeURIComponent(
`Hola, confirmo mi asistencia a los XV Años de Angélica Rodríguez Escobedo 🎀✨
Nombre: `
);
document.getElementById("btnWsp").href = `https://wa.me/${telWsp}?text=${mensaje}`;

/* ========= Copiar Yape ========= */
function copiarYape(){
  navigator.clipboard.writeText("+51958735157");
  showToast("Número de Yape copiado 💙");
}
function showToast(text){
  const t = document.getElementById("toast");
  t.textContent = text;
  t.classList.add("show");
  setTimeout(()=> t.classList.remove("show"), 1600);
}

/* ========= Cuenta regresiva ========= */
/* Evento: 14 de marzo a las 20:00 (hora Perú).
   El navegador usa hora local del dispositivo. */
const eventDate = new Date(new Date().getFullYear(), 2, 14, 20, 0, 0); // Mes 2 = Marzo
function updateCountdown(){
  const now = new Date();
  let diff = eventDate - now;

  // Si ya pasó este año, setear al siguiente
  if(diff < 0){
    eventDate.setFullYear(eventDate.getFullYear()+1);
    diff = eventDate - now;
  }

  const sec = Math.floor(diff/1000);
  const days = Math.floor(sec / 86400);
  const hours = Math.floor((sec % 86400) / 3600);
  const mins = Math.floor((sec % 3600) / 60);
  const secs = sec % 60;

  document.getElementById("d").textContent = String(days).padStart(2,"0");
  document.getElementById("h").textContent = String(hours).padStart(2,"0");
  document.getElementById("m").textContent = String(mins).padStart(2,"0");
  document.getElementById("s").textContent = String(secs).padStart(2,"0");
}
setInterval(updateCountdown, 1000);
updateCountdown();

/* ========= Música (opcional) ========= */
function toggleMusic(){
  const a = document.getElementById("bgm");
  if(a.paused){
    a.play().then(()=> showToast("Música activada 🎵")).catch(()=>{
      showToast("Agrega un MP3 en el código 🎵");
    });
  }else{
    a.pause();
    showToast("Música pausada ⏸️");
  }
}

/* ========= Fondo de estrellas animadas ========= */
const canvas = document.getElementById("stars");
const ctx = canvas.getContext("2d");
let w,h,stars;

function resize(){
  w = canvas.width = window.innerWidth;
  h = canvas.height = window.innerHeight;
  stars = Array.from({length: Math.floor((w*h)/18000)}, () => ({
    x: Math.random()*w,
    y: Math.random()*h,
    r: Math.random()*1.6 + 0.4,
    a: Math.random()*0.8 + 0.2,
    s: Math.random()*0.35 + 0.05
  }));
}
window.addEventListener("resize", resize);
resize();

function draw(){
  ctx.clearRect(0,0,w,h);
  for(const st of stars){
    st.a += (Math.random()-0.5)*0.03;
    if(st.a<0.15) st.a=0.15;
    if(st.a>1) st.a=1;
    st.y += st.s;
    if(st.y>h+10){ st.y=-10; st.x=Math.random()*w; }

    ctx.beginPath();
    ctx.arc(st.x, st.y, st.r, 0, Math.PI*2);
    ctx.fillStyle = `rgba(255,255,255,${st.a})`;
    ctx.fill();
  }
  requestAnimationFrame(draw);
}
draw();
</script>

</body>
</html>
