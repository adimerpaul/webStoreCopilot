<template>
  <section class="pricing-wrapper">
    <div class="container">

      <h3 class="pricing-title">Nuestros planes</h3>

      <!-- ===== Desktop / Tablet (dos tarjetas) ===== -->
      <div class="cards" v-show="$q.screen.gt.sm">
        <!-- Core Plan -->
        <q-card class="plan-card">
          <div class="plan-header">
            <div class="plan-name">Core Plan</div>

            <div class="price-row">
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
        <q-card class="plan-card">
          <div class="plan-header">
            <div class="plan-name">Custom Plan</div>

            <div class="adhoc-row">
              <span class="adhoc">AD HOC*</span>
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
.pricing-wrapper{
  background: linear-gradient(180deg, #f6f4ff 0%, #ffffff 40%);
  border-top: 1px solid rgba(123,102,255,.12);
  padding: 60px 0 56px;
}
.container{
  max-width: 1180px;
  margin: 0 auto;
  padding: 0 22px;
}
.pricing-title{
  text-align: center;
  font-size: 26px;
  font-weight: 800;
  color: #2a2940;
  margin: 0 0 24px 0;
}

/* ===== Desktop cards ===== */
.cards{
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 26px;
}
.plan-card{
  border-radius: 16px;
  background: #fff;
  box-shadow:
    0 18px 40px rgba(24,20,40,.08),
    0 2px 8px rgba(24,20,40,.06);
  border: 1px solid rgba(123,102,255,.14);
  overflow: hidden;
  display: flex; flex-direction: column;
}
.plan-header{
  padding: 20px 22px 0 22px;
}
.plan-name{
  font-weight: 800; color: #2a2940; font-size: 16px; margin-bottom: 8px;
}
.price-row{
  display: flex; align-items: baseline; gap: 6px;
}
.price-row.compact .price{ font-size: 40px; }
.price{
  font-size: 56px;
  font-weight: 800;
  color: #5f48ff;
  line-height: .95;
}
.currency{
  font-size: 24px;
  font-weight: 800;
  color: #5f48ff;
  transform: translateY(1px);
}
.per{
  color:#7c7a92;
  font-weight:700;
}
.adhoc-row{ display:flex; align-items:baseline; }
.adhoc-row.compact .adhoc{ font-size: 28px; }
.adhoc{
  font-size: 34px; font-weight: 900; letter-spacing:.2px;
  background: linear-gradient(90deg, #6e59ff, #8c7bff);
  -webkit-background-clip: text; background-clip: text;
  color: transparent;
}

.plan-body{
  padding: 12px 22px 8px;
}
.plan-sub{
  color:#3a3952; font-size:14px; opacity:.95; margin-bottom: 10px;
}
.features{ margin:0; padding:0; list-style:none; }
.features li{
  display:flex; align-items:flex-start; gap:8px;
  color:#2a2940; font-size:14px; margin: 8px 0;
}
.ok{ color:#5f48ff; font-size:18px; margin-top:2px; }

.soft-divider{
  background: rgba(20,16,40,.08);
  height: 1px;
}

.footnote{
  font-size: 11px; color:#6f6d85; line-height:1.4;
}

.plan-cta{
  padding: 16px 22px 22px;
}
.btn-cta{
  width: 100%;
  background: linear-gradient(180deg, #6c55ff, #5a48e6);
  color:#fff; font-weight:800; border-radius: 12px; padding: 12px 16px;
  box-shadow: 0 12px 28px rgba(108,85,255,.26);
  transition: transform .15s ease, box-shadow .15s ease, filter .15s ease;
}
.btn-cta:hover{
  transform: translateY(-1px);
  box-shadow: 0 16px 36px rgba(108,85,255,.32);
  filter: brightness(1.02);
}

/* ===== Mobile acordeón ===== */
.mobile-accordion .acc-card{
  border-radius: 14px;
  box-shadow: 0 10px 26px rgba(24,20,40,.10);
  border: 1px solid rgba(123,102,255,.14);
  overflow: hidden;
}
.acc-header{
  background:#fff;
}
.acc-head-inner{
  display:flex; justify-content:space-between; align-items:center; width:100%;
  padding: 10px 6px 6px 2px;
}
.acc-head-inner .plan-name{
  font-weight: 800; color: #2a2940; font-size: 15px; margin: 0;
}

@media (max-width: 1024px){
  .cards{ grid-template-columns: 1fr; }
}
</style>
