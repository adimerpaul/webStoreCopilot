<template>
  <section class="beyond-wrapper">
    <div class="container">
      <h3 class="section-title">
        Más allá de las ventas: <span class="accent">tu rentabilidad real</span>
      </h3>
      <p class="section-sub">
        StoreCopilot te permite incluir todos los costes asociados a tu eCommerce:
        <b>desde COGS hasta comisiones de pago, envíos, devoluciones y logística.</b>
        Así obtienes una visión completa de cuánto ganas de verdad en cada pedido.
      </p>

      <!-- ===== Desktop / Tablet ===== -->
      <div class="grid" v-show="$q.screen.gt.sm">
        <!-- Izquierda: tarjetas features -->
        <div class="left">
          <div
            v-for="(f, i) in features"
            :key="f.key"
            class="feature-card"
            :class="{ active: i === selected }"
            @click="selected = i"
          >
            <div class="feature-text">
              <div class="icon-wrap">
                <q-icon :name="f.icon" />
              </div>
              <div class="feature-title">{{ f.title }}</div>
              <div class="feature-sub">{{ f.sub }}</div>
            </div>
          </div>
        </div>

        <!-- Derecha: tarjetas de configuración (como en Figma) -->
        <div class="right" style="background: transparent;">
          <q-img src="sales_cogs.png" alt="COGS y márgenes" />
        </div>
      </div>

      <!-- ===== Mobile: carrusel + tarjetas apiladas ===== -->
      <div v-show="!$q.screen.gt.sm">
        <q-carousel
          v-model="mobSlide"
          swipeable
          animated
          navigation
          arrows
          height="160px"
          class="feature-carousel q-mb-md"
        >
          <q-carousel-slide
            v-for="(f, i) in features"
            :key="'mob-'+f.key"
            :name="i"
            class="feature-slide"
          >
            <div class="feature-card mobile">
              <div class="icon-wrap">
                <q-icon :name="f.icon" />
              </div>
              <div class="feature-text">
                <div class="feature-title">{{ f.title }}</div>
                <div class="feature-sub">{{ f.sub }}</div>
              </div>
            </div>
          </q-carousel-slide>
        </q-carousel>
        <q-img src="sales_cogs.png" alt="COGS y márgenes" />
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'BeyondSalesSection',
  data () {
    return {
      selected: 0,
      mobSlide: 0,
      features: [
        {
          key: 'cogs',
          icon: 'inventory_2',
          title: 'COGS y márgenes',
          sub: 'Sube tus costes de producto y entiende el beneficio real por SKU.'
        },
        {
          key: 'shipping',
          icon: 'local_shipping',
          title: 'Costes de envío y devoluciones',
          sub: 'Calcula el impacto real en tu margen.'
        },
        {
          key: 'fees',
          icon: 'payments',
          title: 'Fees de pago y pasarelas',
          sub: 'Integra comisiones de Shopify, PayPal, Klarna, etc.'
        },
        {
          key: 'pack',
          icon: 'inventory',
          title: 'Pick & Pack y logística',
          sub: 'Costes asociados al servicio de preparación y logística.'
        }
      ],
      paymentMethods: [
        { key: 'default', name: 'Predeterminado', percent: 2.5, fixed: 0 },
        { key: 'manual',  name: 'Manual',        percent: 2.5, fixed: 0 },
        { key: 'paypal',  name: 'Paypal',        percent: 2.5, fixed: 0 },
        { key: 'shopify', name: 'Shopify Payments', percent: 2.5, fixed: 0 },
        { key: 'klarna',  name: 'Klarna',        percent: 2.5, fixed: 0 },
        { key: 'clearpay',name: 'Clearpay',      percent: 2.5, fixed: 0 },
        { key: 'sequra',  name: 'SeQura',        percent: 2.5, fixed: 0 },
        { key: 'afterpay',name: 'Afterpay',      percent: 2.5, fixed: 0 },
        { key: 'other',   name: 'Otro',          percent: 2.5, fixed: 0 }
      ]
    }
  }
}
</script>

<style scoped>
.beyond-wrapper{
  padding: 60px 0;
  background: linear-gradient(180deg, #ffffff 0%, #fbfaff 100%);
  border-top: 1px solid rgba(123,102,255,.12);
}
.container{
  max-width: 1180px;
  margin: 0 auto;
  padding: 0 22px;
}

.section-title{
  text-align: center;
  font-size: 26px;
  font-weight: 900;
  color: #23233a;
  margin: 0 0 8px 0;
}
.section-sub{
  text-align: center;
  color: #3a3952;
  max-width: 900px;
  margin: 0 auto 22px;
  font-size: 15px;
}
.accent{ color:#6f5bff; }

/* Grid principal */
.grid{
  display:grid;
  grid-template-columns: 300px 1fr;
  gap: 28px;
}

/* Izquierda: tarjetas dark */
.left{ display:flex; flex-direction:column; gap:16px; }
.feature-card{
  display:flex; align-items:flex-start; gap:14px;
  background:#0d0f38;
  color:#fff; padding:16px; border-radius:14px;
  box-shadow: 0 12px 28px rgba(13,15,56,.28);
  border:1px solid rgba(255,255,255,.08);
  cursor:pointer; transition: transform .12s ease, box-shadow .12s ease, border .12s ease;
}
.feature-card.active, .feature-card:hover{
  transform: translateY(-1px);
  box-shadow: 0 16px 36px rgba(13,15,56,.32);
  border-color: rgba(123,102,255,.38);
}
.icon-wrap{
  width:42px; height:42px; border-radius:10px;
  background: radial-gradient(80% 80% at 30% 20%, #7c66ff, #533bff);
  display:flex; align-items:center; justify-content:center; flex-shrink:0;
}
.icon-wrap .q-icon{ color:#fff; font-size:22px; }
.feature-text .feature-title{ font-weight:800; font-size:16px; line-height:1.15; }
.feature-text .feature-sub{ opacity:.9; font-size:13px; }

/* Derecha: tarjetas de configuración */
.right{ display:flex; flex-direction:column; gap:18px; }
.conf-card{
  border-radius:14px;
  background:#fff;
  border:1px solid rgba(123,102,255,.14);
  box-shadow: 0 14px 34px rgba(24,20,40,.10);
}
.conf-title{
  font-weight:800; color:#23233a; font-size:16px; margin-bottom:6px;
}
.conf-sub{
  color:#5a5970; font-size:13px;
}

/* Tabla de métodos de pago */
.method-grid .header .label{
  font-size:12px; color:#6c6b82; font-weight:700;
}
.method-grid .item{
  align-items:center;
  padding:6px 0;
  border-top: 1px solid rgba(0,0,0,.04);
}
.item-name{ font-size:14px; color:#272638; }

/* Mobile carrusel */
.feature-carousel{ border-radius:14px; overflow:hidden; }
.feature-slide{
  display:flex; align-items:center; justify-content:center; height:100%;
  background: transparent;
}
.feature-card.mobile{ width:100%; height:100%; border-radius:14px; }

@media (max-width: 1024px){
  .grid{ grid-template-columns: 1fr; }
}
</style>
