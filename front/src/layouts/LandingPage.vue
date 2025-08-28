<template>
  <q-layout view="lHh Lpr lFf">
    <DrawerMenu ref="drawerMenu" :nav-items="navItems" />
    <q-page-container>
      <q-page class="hero-bg">
        <Navbar @open-drawer="openDrawer" :nav-items="navItems" />

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
          <div class="hero-right">
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
<!--          <q-img-->
<!--            src="/phone.png"-->
<!--            alt="Phone preview"-->
<!--            class="phone"-->
<!--            fit="contain"-->
<!--          />-->
        </div>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import Navbar from 'components/Navbar.vue'
import DrawerMenu from 'components/DrawerMenu.vue'

const drawerMenu = ref(null)
const navItems = [
  { label: 'Cómo funciona', to: '/funciona' },
  { label: 'Beneficios', to: '/beneficios' },
  { label: 'Roadmap', to: '/roadmap' },
  { label: 'Integraciones', to: '/integraciones' },
  { label: 'Nosotros', to: '/nosotros' },
  { label: 'FAQs', to: '/faqs' }
]
function openDrawer () {
  if (drawerMenu.value) drawerMenu.value.drawer = true
}
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
.hero-left{
  max-width: 640px;
}
.hero-title{
  margin: 0 0 18px 0;
  line-height: 1.08;
  color: #1b1b22;
  font-weight: 800;
  font-size: 52px;                 /* desktop */
}
.highlight{
  color: #7b66ff;
}
.hero-sub{
  margin: 0 0 26px 0;
  font-size: 17px;
  color: #1b1b22;
  opacity: .9;
}
.btn-cta{
  background: #6c55ff;
  color: #fff;
  border-radius: 14px;
  padding: 14px 22px;
  font-weight: 800;
  box-shadow: 0 14px 26px rgba(108,85,255,.28);
  transition: transform .15s ease, box-shadow .15s ease, filter .15s ease;
}
.btn-cta:hover{
  transform: translateY(-1px);
  box-shadow: 0 18px 34px rgba(108,85,255,.32);
  filter: brightness(1.03);
}

/* Teléfono con halo y bleed a la derecha */
.hero-right{
  position: relative;
}
.phone-wrap{
  position: relative;
  width: 100%;
  max-width: 640px;
  margin-left: auto;
  /* lo desplazamos un poco a la derecha para simular que "sale" del canvas */
  transform: translateX(40px);
}
.halo{
  position: absolute;
  right: 6%;
  top: 36%;
  width: 410px; height: 410px;
  border-radius: 50%;
  background: radial-gradient(circle at 50% 50%, rgba(124,92,255,.42) 0%, rgba(124,92,255,0) 70%);
  filter: blur(18px);
  z-index: 0;
}
.phone{
  position: relative;
  z-index: 1;
  width: 100%;
  max-width: 360px;               /* tamaño de teléfono */
  border-radius: 28px;
  /*box-shadow: 0 40px 70px rgba(0,0,0,.22); */
  background: transparent;
}

/* ====== Responsive ====== */
@media (max-width: 1024px){
  .hero-container{
    grid-template-columns: 1fr 1fr;
    gap: 18px;
  }
  .hero-title{ font-size: 44px; }
  .phone-wrap{ transform: translateX(20px); }
  .halo{ width: 360px; height: 360px; }
}

@media (max-width: 768px) {
  .hero-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-inline: 18px;
    gap: 18px;
  }
  .hero-left {
    text-align: center;
  }
  .hero-title {
    font-size: 34px;
    line-height: 1.12;
  }
  .hero-sub {
    font-size: 14px;
  }
  .hero-right {
    display: flex; /* Ensures image container is a flexbox */
    justify-content: center; /* Centers the image horizontally */
    width: 100%; /* Ensures the container takes full width */
  }
  .phone-wrap {
    transform: none;
    max-width: 420px;
    width: 100%;
    /* Add padding or margin here if needed */
  }
  .phone {
    width: 100%;
    height: auto; /* Ensures the aspect ratio is maintained */
  }
  .halo {
    position: absolute;
    right: auto;
    left: 50%;
    top: 58%;
    transform: translateX(-50%);
    width: 320px;
    height: 320px;
  }
}
</style>
