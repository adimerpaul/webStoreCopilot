<template>
  <div class="hero-container">
    <!-- Texto -->
    <div class="hero-left">
      <h1 class="hero-title">
        Datos para el control<br />
        total del <span class="highlight">crecimiento de tu</span><br />
        <span class="highlight">ecommerce</span>
      </h1>

      <p class="hero-sub">
        Todas tus métricas clave en un solo lugar.<br />
        StoreCopilot no es un dashboard más:
        <b> es el copiloto de datos para ecommerce, hecho a tu medida.</b>
      </p>

      <q-btn class="btn-cta" no-caps label="Quiero ver una Demo" unelevated />
    </div>

    <!-- Teléfono -->
    <div :class="`hero-right ${!$q.screen.lt.md ? 'text-center' : ''}`">
      <div class="phone-wrap">
        <div class="halo"></div>
        <q-img
          src="/phone.png"
          alt="Phone preview"
          class="phone"
          fit="contain"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default { name: 'HeroSection' }
</script>

<style scoped>
/* ===== Fondo más fiel al Figma ===== */
.hero-bg{
  min-height:100dvh; width:100%; position:relative; overflow:hidden;
  background:
    radial-gradient(1100px 700px at 18% 0%, rgba(160,130,255,.34), rgba(255,255,255,0) 58%),
    radial-gradient(850px 650px at 75% 62%, rgba(142,114,255,.35), rgba(255,255,255,0) 62%),
    linear-gradient(180deg,#ffffff 0%, #f7f4ff 42%, #ece4ff 100%);
}

/* ===== Layout hero ===== */
.hero-container{
  max-width: 1240px;
  margin: 130px auto 0;
  padding: 0 28px;

  display: grid;
  grid-template-columns: 1.05fr 0.95fr;
  align-items: center;
  gap: 24px;
}

/* Texto */
.hero-left{ max-width: 640px; }
.hero-title{
  margin: 0 0 18px 0;
  line-height: 1.08;
  color: #1b1b22;
  font-weight: 800;
  font-size: 52px;
}
.highlight{ color: #7b66ff; }
.hero-sub{
  margin: 0 0 26px 0;
  font-size: 17px;
  color: #1b1b22;
  opacity: .9;
}
.btn-cta{
  background: #6c55ff; color: #fff; border-radius: 14px; padding: 14px 22px;
  font-weight: 800; box-shadow: 0 14px 26px rgba(108,85,255,.28);
  transition: transform .15s ease, box-shadow .15s ease, filter .15s ease;
}
.btn-cta:hover{
  transform: translateY(-1px);
  box-shadow: 0 18px 34px rgba(108,85,255,.32);
  filter: brightness(1.03);
}

/* Teléfono con halo y bleed a la derecha */
.hero-right{ position: relative; }
.phone-wrap{
  position: relative; width: 100%; max-width: 640px; margin-left: auto;
  transform: translateX(40px);
}
.halo{
  position: absolute; right: 6%; top: 36%;
  width: 410px; height: 410px; border-radius: 50%;
  background: radial-gradient(circle at 50% 50%, rgba(124,92,255,.42) 0%, rgba(124,92,255,0) 70%);
  filter: blur(18px); z-index: 0;
}
.phone{
  position: relative; z-index: 1; width: 100%; max-width: 360px; border-radius: 28px; background: transparent;
}

/* ====== Responsive ====== */
@media (max-width: 1024px){
  .hero-container{ grid-template-columns: 1fr 1fr; gap: 18px; }
  .hero-title{ font-size: 44px; }
  .phone-wrap{ transform: translateX(20px); }
  .halo{ width: 360px; height: 360px; }
}
@media (max-width: 768px) {
  .hero-container{
    display:flex; flex-direction:column; justify-content:center; align-items:center;
    padding-inline:18px; gap:18px;
  }
  .hero-left{ text-align:center; }
  .hero-title{ font-size:34px; line-height:1.12; }
  .hero-sub{ font-size:14px; }
  .hero-right{ display:flex; justify-content:center; width:100%; }
  .phone-wrap{ transform:none; max-width:420px; width:100%; }
  .phone{ width:100%; height:auto; }
  .halo{
    position:absolute; right:auto; left:50%; top:58%; transform:translateX(-50%);
    width:320px; height:320px;
  }
}

/* ===== Animaciones “copilot style” (solo CSS) ===== */

/* 1) Entrada escalonada del texto */
.hero-left .hero-title,
.hero-left .hero-sub,
.hero-left .btn-cta{
  opacity: 0;
  transform: translateY(18px) scale(.985);
  filter: blur(2px);
  will-change: transform, opacity, filter;
  animation: fadeUp .7s cubic-bezier(.16,1,.3,1) forwards;
}
.hero-left .hero-title{ animation-delay: .05s; }
.hero-left .hero-sub{  animation-delay: .18s; }
.hero-left .btn-cta{   animation-delay: .30s; }

/* 2) Teléfono: entra desde la derecha y luego “flota” */
.phone{
  opacity: 0;
  transform-origin: 50% 85%;
  will-change: transform, opacity, filter;
  animation:
    slideInRight .8s cubic-bezier(.16,1,.3,1) .12s both,
    bob 7.5s ease-in-out 1.1s infinite;
  filter: drop-shadow(0 18px 40px rgba(32,22,86,.22));
}

/* 3) Halo con respiración */
.halo{
  animation: haloPulse 4.8s ease-in-out .6s infinite alternate;
  will-change: opacity, transform, filter;
}

/* 4) Botón con micro-pop y glow sutil */
.btn-cta{
  transform-origin: 50% 50%;
  animation: fadeUp .7s cubic-bezier(.16,1,.3,1) .3s forwards, glowPulse 3.2s ease-in-out 1.6s infinite;
}
.btn-cta:hover{
  transform: translateY(-1px) scale(1.015);
}

/* ===== Keyframes ===== */
@keyframes fadeUp{
  from{ opacity:0; transform: translateY(18px) scale(.985); filter: blur(2px); }
  to  { opacity:1; transform: translateY(0)    scale(1);     filter: blur(0);   }
}
@keyframes slideInRight{
  0%  { opacity:0; transform: translateX(46px) rotate(-1.2deg) scale(.985); filter: blur(1px); }
  100%{ opacity:1; transform: translateX(0)    rotate(0)       scale(1);    filter: blur(0);  }
}
@keyframes bob{
  0%,100%{ transform: translateY(0) rotate(0); }
  50%    { transform: translateY(-10px) rotate(.2deg); }
}
@keyframes haloPulse{
  from{ opacity:.55; transform: scale(1);    filter: blur(16px); }
  to  { opacity:.9;  transform: scale(1.08); filter: blur(20px); }
}
@keyframes glowPulse{
  0%,100%{ box-shadow: 0 14px 26px rgba(108,85,255,.28); }
  50%    { box-shadow: 0 18px 36px rgba(108,85,255,.38); }
}

/* ===== Accesibilidad: respeta reduce motion ===== */
@media (prefers-reduced-motion: reduce){
  .hero-left .hero-title,
  .hero-left .hero-sub,
  .hero-left .btn-cta,
  .phone,
  .halo{
    animation: none !important;
    opacity: 1 !important;
    transform: none !important;
    filter: none !important;
  }
}
</style>
