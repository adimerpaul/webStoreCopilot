<template>
  <section class="pricing-wrapper">
    <div class="container">

      <h3 class="pricing-title">Nuestros planes</h3>

      <!-- ===== Desktop / Tablet (dos tarjetas) ===== -->
      <div class="cards " v-show="$q.screen.gt.sm">
        <!-- Core Plan -->
        <q-card class="plan-card" style="width: 350px;">
          <div class="plan-header">
            <div class="plan-name text-center">Core Plan</div>

            <div class="price-row text-center">
              <span class="price">{{ priceCoreVal }}</span>
              <span class="currency">€</span>
              <span class="per">/mes*</span>
            </div>
          </div>

          <div class="plan-body">
            <div class="plan-sub">El stack esencial de datos para tu ecommerce</div>

            <ul class="features">
              <li><q-icon name="check_circle" class="ok" /> Business Intelligence: panel de finanzas, ventas y marketing centralizado.</li>
              <li><q-icon name="check_circle" class="ok" /> Insights de producto: productos estrella, rotación, márgenes.</li>
              <li><q-icon name="check_circle" class="ok" /> Ads Performance: ROAS objetivo, CPAs, resultados de campañas.</li>
            </ul>

            <q-separator class="soft-divider q-my-md" />

            <div class="footnote">
              *El coste se adapta al tamaño y necesidades de tu negocio. La tarifa base es de {{ priceCoreVal }}€ y puede variar en función del número de órdenes mensuales y de tiendas que conectemos.
            </div>
          </div>

          <div class="plan-cta">
            <q-btn class="btn-cta" no-caps label="Reserva tu demo" @click="onDemo('core')" />
          </div>
        </q-card>

        <!-- Custom Plan -->
        <q-card class="plan-card" style="width: 350px;">
          <div class="plan-header">
            <div class="plan-name text-center">Custom Plan</div>

            <div class="adhoc-row">
              <span class="adhoc text-center">AD HOC*</span>
            </div>
          </div>

          <div class="plan-body">
            <div class="plan-sub">La herramienta hecha a tu medida</div>

            <ul class="features">
              <li><q-icon name="check_circle" class="ok" /> Integraciones personalizadas: conectamos tus sistemas o herramientas clave (ERP, logística, etc.).</li>
              <li><q-icon name="check_circle" class="ok" /> Reportes adaptados a tu negocio: métricas diseñadas para tu casuística y la de tus equipos.</li>
              <li><q-icon name="check_circle" class="ok" /> No es una plataforma genérica: es tu copiloto de datos personalizado para tomar decisiones con total claridad.</li>
            </ul>

            <q-separator class="soft-divider q-my-md" />

            <div class="footnote">
              *El coste se definirá en función del número de integraciones adicionales, número de tiendas y volumen de órdenes.
            </div>
          </div>

          <div class="plan-cta">
            <q-btn class="btn-cta" no-caps label="Reserva tu demo" @click="onDemo('custom')" />
          </div>
        </q-card>
      </div>

      <!-- ===== Mobile (acordeón como en el Figma) ===== -->
      <div class="mobile-accordion" v-show="!$q.screen.gt.sm">
        <!-- Core -->
        <q-card class="acc-card q-mb-md">
          <q-expansion-item
            v-model="acc.core"
            dense
            expand-separator
            switch-toggle-side
            header-class="acc-header"
            expand-icon="keyboard_arrow_down"
            group="planes"
          >
            <template v-slot:header>
              <div class="acc-head-inner">
                <div class="plan-name">Core Plan</div>
                <div class="price-row compact">
                  <span class="price">{{ priceCoreVal }}</span>
                  <span class="currency">€</span>
                  <span class="per">/mes*</span>
                </div>
              </div>
              <q-space />
            </template>

            <div class="q-pa-md">
              <div class="plan-sub q-mb-sm">El stack esencial de datos para tu ecommerce</div>

              <ul class="features q-mb-sm">
                <li><q-icon name="check_circle" class="ok" /> Business Intelligence: panel de finanzas, ventas y marketing centralizado.</li>
                <li><q-icon name="check_circle" class="ok" /> Insights de producto: productos estrella, rotación, márgenes.</li>
                <li><q-icon name="check_circle" class="ok" /> Ads Performance: ROAS objetivo, CPAs, resultados de campañas.</li>
              </ul>

              <q-separator class="soft-divider q-my-md" />
              <div class="footnote q-mb-md">
                *El coste se adapta al tamaño y necesidades de tu negocio. La tarifa base es de {{ priceCoreVal }}€ y puede variar en función del número de órdenes mensuales y de tiendas que conectemos.
              </div>

              <q-btn class="btn-cta full-width" no-caps label="Reserva tu demo" @click="onDemo('core')" />
            </div>
          </q-expansion-item>
        </q-card>

        <!-- Custom -->
        <q-card class="acc-card">
          <q-expansion-item
            v-model="acc.custom"
            dense
            expand-separator
            switch-toggle-side
            header-class="acc-header"
            expand-icon="keyboard_arrow_down"
            group="planes"
          >
            <template v-slot:header>
              <div class="acc-head-inner">
                <div class="plan-name">Custom Plan</div>
                <div class="adhoc-row compact">
                  <span class="adhoc">AD HOC*</span>
                </div>
              </div>
              <q-space />
            </template>

            <div class="q-pa-md">
              <div class="plan-sub q-mb-sm">La herramienta hecha a tu medida</div>

              <ul class="features q-mb-sm">
                <li><q-icon name="check_circle" class="ok" /> Integraciones personalizadas: conectamos tus sistemas o herramientas clave (ERP, logística, etc.).</li>
                <li><q-icon name="check_circle" class="ok" /> Reportes adaptados a tu negocio: métricas diseñadas para tu casuística y la de tus equipos.</li>
                <li><q-icon name="check_circle" class="ok" /> No es una plataforma genérica: es tu copiloto de datos personalizado para tomar decisiones con total claridad.</li>
              </ul>

              <q-separator class="soft-divider q-my-md" />
              <div class="footnote q-mb-md">
                *El coste se definirá en función del número de integraciones adicionales, número de tiendas y volumen de órdenes.
              </div>

              <q-btn class="btn-cta full-width" no-caps label="Reserva tu demo" @click="onDemo('custom')" />
            </div>
          </q-expansion-item>
        </q-card>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'PricingPlans',
  data () {
    return {
      period: 'mensual', // si luego quieres mensual/anual, aquí lo conectas
      acc: { core: true, custom: false }
    }
  },
  computed: {
    priceCoreVal () {
      // Si más adelante activas el toggle de periodo:
      // return this.period === 'anual' ? 80 : 90
      return 90
    }
  },
  methods: {
    onDemo (plan) {
      this.$q.notify({
        color: 'primary',
        message: `🗓️ Reservando demo para: ${plan === 'core' ? 'Core Plan' : 'Custom Plan'}`,
        position: 'top',
        timeout: 1500
      })
      // o usa this.$router.push('/demo')
    }
  }
}
</script>

<style scoped>
/* ===== Sección / fondo ===== */
.pricing-wrapper{
  /* fondo lila muy sutil como en Figma */
  background:
    radial-gradient(900px 600px at 18% -18%, rgba(160,130,255,.16) 0%, rgba(160,130,255,0) 60%),
    linear-gradient(180deg, #f6f4ff 0%, #ffffff 52%);
  border-top: 1px solid rgba(123,102,255,.10);
  padding: 72px 0 64px;
}
.container{
  max-width: 1160px;
  margin: 0 auto;
  padding: 0 22px;
}
.pricing-title{
  text-align: center;
  font-size: 28px;
  font-weight: 800;
  color: #2a2940;
  margin: 0 0 28px 0;
}

/* ===== Grid desktop ===== */
.cards{
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 32px; /* más respiración entre tarjetas */
}

/* ===== Tarjeta ===== */
.plan-card{
  --card-border: rgba(18, 16, 40, .06);
  --card-shadow-1: 0 28px 60px rgba(50, 36, 120, .12);
  --card-shadow-2: 0 2px 10px rgba(18, 16, 40, .05);

  border-radius: 22px;                /* radio grande como Figma */
  background: #fff;
  border: 1px solid var(--card-border);
  box-shadow: var(--card-shadow-1), var(--card-shadow-2);
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.plan-header{
  padding: 26px 26px 0 26px;          /* más margen superior */
}
.plan-name{
  font-weight: 800;
  color: #2a2940;
  font-size: 16px;
  margin-bottom: 10px;
}

/* Precio grande con gradiente como en Figma */
.price-row{
  display: flex;
  align-items: baseline;
  gap: 8px;
}
.price{
  font-size: 60px;                    /* más grande */
  font-weight: 900;
  line-height: .9;
  background: linear-gradient(90deg,#6e59ff,#8c7bff);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  letter-spacing: .5px;
}
.currency{
  font-size: 26px;
  font-weight: 900;
  background: linear-gradient(90deg,#6e59ff,#8c7bff);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  transform: translateY(2px);
}
.per{
  color:#79789a;
  font-weight:700;
}

/* AD HOC con gradiente */
.adhoc-row{ display:flex; align-items:baseline; }
.adhoc{
  font-size: 36px;
  font-weight: 900;
  letter-spacing:.2px;
  background: linear-gradient(90deg, #6e59ff, #8c7bff);
  -webkit-background-clip: text; background-clip: text;
  color: transparent;
}

/* Cuerpo */
.plan-body{
  padding: 14px 26px 10px;
}
.plan-sub{
  color:#3a3952;
  font-size:14px;
  opacity:.95;
  margin-bottom: 12px;
}

/* Bullets estilo “check” con pastilla lila y sombra suave */
.features{ margin:0; padding:0; list-style:none; }
.features li{
  display:flex; align-items:flex-start; gap:10px;
  color:#2a2940; font-size:14px; margin: 10px 0;
}
.ok{
  --ok-bg: linear-gradient(180deg,#6e59ff,#7f6bff);
  position: relative;
  font-size: 0;                 /* ocultar el ícono material */
  width: 18px; height: 18px;    /* pastilla redonda */
  border-radius: 50%;
  background: var(--ok-bg);
  box-shadow: 0 4px 10px rgba(108,85,255,.30);
  margin-top: 2px;
}
.ok::after{
  content: '';
  position: absolute; inset: 0;
  mask: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path fill="white" d="M9 16.2 4.8 12l-1.4 1.4L9 19 21 7l-1.4-1.4z"/></svg>') center/70% no-repeat;
  background: #fff;
}

/* Divisor fino */
.soft-divider{
  height: 1px;
  background: rgba(20,16,40,.10);
}

/* Nota al pie */
.footnote{
  font-size: 11.5px;
  color:#6f6d85;
  line-height:1.45;
}

/* CTA con glow elíptico como en Figma */
.plan-cta{
  position: relative;
  padding: 18px 26px 26px;
}
.btn-cta{
  position: relative;
  width: 100%;
  background: linear-gradient(180deg, #6c55ff, #5a48e6);
  color:#fff; font-weight:800; border-radius: 14px; padding: 13px 18px;
  box-shadow: 0 12px 28px rgba(108,85,255,.26);
  transition: transform .15s ease, box-shadow .15s ease, filter .15s ease;
}
.btn-cta:hover{
  transform: translateY(-1px);
  box-shadow: 0 18px 40px rgba(108,85,255,.33);
  filter: brightness(1.02);
}
/* sombra elíptica por debajo del botón (como “pastilla”) */
.plan-cta::after{
  content:'';
  position:absolute; left: 26px; right: 26px; bottom: 12px;
  height: 28px;
  border-radius: 999px;
  background: radial-gradient(60% 100% at 50% 50%, rgba(108,85,255,.35), rgba(108,85,255,0) 70%);
  filter: blur(6px);
  pointer-events:none;
}

/* ===== Acordeón mobile ===== */
.mobile-accordion .acc-card{
  border-radius: 16px;
  border: 1px solid rgba(18,16,40,.06);
  box-shadow: 0 16px 34px rgba(24,20,40,.10);
  overflow: hidden;
}
.acc-header{ background:#fff; }
.acc-head-inner{
  display:flex; justify-content:space-between; align-items:center; width:100%;
  padding: 12px 8px 6px 2px;
}
.acc-head-inner .plan-name{
  font-weight: 800; color: #2a2940; font-size: 15px; margin: 0;
}
.price-row.compact .price{ font-size: 44px; }
.adhoc-row.compact .adhoc{ font-size: 30px; }

/* ===== Responsivo ===== */
@media (max-width: 1180px){
  .cards{ gap: 28px; }
}
@media (max-width: 1024px){
  .cards{ grid-template-columns: 1fr; }
}

</style>
