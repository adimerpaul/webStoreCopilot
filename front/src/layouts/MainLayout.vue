<template>
  <q-layout view="lHh Lpr lFf">
    <q-page-container>
      <q-page class="hero-bg">
        <!-- ====== NAV flotante ====== -->
        <div class="nav-card">
          <div class="nav-inner">
            <!-- Izquierda: logo -->
            <div class="nav-left">
              <q-img src="logo.svg" alt="StoreCopilot" width="45px" class="logo" fit="contain" />
              <span class="q-pa-xs">
                Store <span class="text-bold">Copilot</span>
              </span>
            </div>

            <!-- Centro: links -->
            <div class="nav-center">
              <q-tabs dense shrink class="nav-tabs">
                <q-tab label="Cómo funciona" no-caps />
                <q-tab label="Beneficios" no-caps />
                <q-tab label="Roadmap" no-caps />
                <q-tab label="Integraciones" no-caps />
                <q-tab label="Nosotros" no-caps />
                <q-tab label="FAQs" no-caps />
              </q-tabs>
            </div>

            <!-- Derecha: Login + Demo -->
            <div class="nav-right">
              <q-btn flat no-caps label="Login" class="q-mr-sm text-weight-medium" />
              <q-btn no-caps label="Demo" class="btn-demo" />
            </div>
          </div>
        </div>

        <!-- ====== HERO ====== -->
        <div class="hero-container">
          <div class="hero-left">
            <h1 class="hero-title">
              Datos para el control<br />
              total del <span>crecimiento de tu</span><br />
              <span>ecommerce</span>
            </h1>

            <p class="hero-sub">
              Todas tus métricas clave en un solo lugar.<br />
              StoreCopilot no es un dashboard más: <b>es el copiloto<br />
              de datos para ecommerce, hecho a tu medida.</b>
            </p>

            <q-btn
              class="btn-cta"
              no-caps
              label="Quiero ver una Demo"
              unelevated
            />
          </div>

          <div class="hero-right">
            <!-- imagen del teléfono / mock -->
            <q-img src="/phone.png" alt="Phone preview" class="phone" />
          </div>
        </div>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
export default { name: 'LoadingPage' }
</script>

<style scoped>
/* ===== Fondo (ya afinado) ===== */
.hero-bg{
  min-height:100dvh; width:100%; position:relative; overflow:hidden;
  background:
    radial-gradient(900px 600px at 15% 0%, rgba(160,130,255,.38), rgba(255,255,255,0) 55%),
    radial-gradient(950px 650px at 85% 80%, rgba(160,130,255,.34), rgba(255,255,255,0) 55%),
    linear-gradient(180deg,#fff 0%,#f6f2ff 42%,#ece4ff 100%);
  background-attachment: fixed, fixed, scroll;
}

/* ===== NAV ===== */
.nav-card{
  position:absolute; top:16px; left:16px; right:16px;
  max-width:1180px; margin:0 auto; background:#fff; color:#000;
  border-radius:16px;
  box-shadow:0 10px 30px rgba(24,20,40,.08), 0 2px 6px rgba(24,20,40,.05);
}
.nav-inner{
  display:grid;
  grid-template-columns: 1fr auto 1fr;
  align-items:center;
  padding:10px 16px;
  gap:8px;
}
.nav-left{ display:flex; align-items:center; }
.logo { filter: drop-shadow(0 2px 6px rgba(0,0,0,.04)); }

.nav-center{ display:flex; justify-content:center; }
.nav-tabs :deep(.q-tab__label){ font-weight:600; letter-spacing:.1px; }

.nav-right{ display:flex; justify-content:flex-end; align-items:center; }
.btn-demo{
  background:#262438; color:#fff; border-radius:12px; padding:8px 16px;
  font-weight:700;
}

/* ===== HERO ===== */
.hero-container{
  max-width:1180px; margin:140px auto 0; /* deja aire bajo la nav pill */
  padding:0 24px; display:grid; grid-template-columns: 1.15fr 0.85fr; gap:24px;
  align-items:center;
}
.hero-title{
  margin:0 0 14px 0; line-height:1.1; color:#1d1d26;
  font-size:48px; font-weight:800;
}
.hero-title span{ color:#7b66ff; } /* lila del Figma */

.hero-sub{
  margin:0 0 22px 0; font-size:16px; color:#1d1d26; opacity:.85;
}
.btn-cta{
  background:#6c55ff; color:#fff; border-radius:12px; padding:12px 18px;
  box-shadow: 0 10px 18px rgba(108,85,255,.22);
  font-weight:700;
}

/* Imagen teléfono */
.phone{
  width:100%; max-width:520px; border-radius:32px;
  box-shadow: 0 30px 60px rgba(0,0,0,.18);
  background: transparent;
}

/* ===== Responsive ===== */
@media (max-width: 1024px){
  .nav-inner{ grid-template-columns: auto 1fr auto; }
  .hero-container{ grid-template-columns: 1fr; text-align:left; }
  .hero-right{ order:-1; display:flex; justify-content:center; }
  .hero-title{ font-size:40px; text-align:center; }
  .hero-sub{ text-align:center; }
  .btn-cta{ display:block; margin:0 auto; }
}
@media (max-width: 640px){
  .nav-tabs{ display:none; }        /* oculta tabs en móvil; podrías abrir un drawer */
  .logo{ width:150px; }
  .hero-container{ margin-top:120px; }
  .hero-title{ font-size:34px; }
}
</style>
