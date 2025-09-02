<template>
  <section class="adaptive-wrapper">

    <!-- Banda suave como en Figma -->
    <div class="band">
      <div class="container">

        <!-- Título y bajada -->
        <h2 class="title">
          Un dashboard que se adapta a tu negocio, <span class="accent">no al revés</span>
        </h2>
        <p class="subtitle">
          StoreCopilot no es un SaaS que solo muestra gráficos. Es un copiloto que se adapta a tu negocio:
          <b>entendemos tu modelo, tus métricas claves y tus necesidades de reporting.</b>
          Personalizamos las visualizaciones e integraciones que realmente importan para que tomes decisiones con datos hechos a tu medida.
        </p>

        <!-- Logos -->
        <div class="logos">
          <q-img
            v-for="(src, i) in logosToShow"
            :key="'logo-'+i"
            :src="src"
            :alt="'logo-'+(i+1)"
            width="110px"
            contain
            spinner-color="grey-5"
          />
        </div>
      </div>
    </div>

    <!-- Bloque: Toda tu operación -->
    <div class="container section-ops">
      <h3 class="ops-title">
        Toda tu operación <span class="accent">en un solo panel</span>
      </h3>

      <div class="ops-grid q-pa-lg">
        <div class="ops-left">
          <h4 class="ops-h4">{{ currentPanel.title }}</h4>
          <p class="ops-p">{{ currentPanel.text }}</p>

          <!-- Paginación decorativa (puntos) -->
<!--          <div class="dots">-->
<!--            <span-->
<!--              v-for="(p, i) in panelsFinal"-->
<!--              :key="'dot-'+i"-->
<!--              class="dot"-->
<!--              :class="{ active: slide === i }"-->
<!--              @click="go(i)"-->
<!--            />-->
<!--          </div>-->
<!--          fechas en ve de putnos-->

          <div class="dots">
<!--            <q-btn atras-->
            <q-btn outline round dense icon="chevron_left" @click="go(slide > 0 ? slide - 1 : panelsFinal.length - 1)" />
            <q-btn outline round dense icon="chevron_right" @click="go(slide < panelsFinal.length - 1 ? slide + 1 : 0)" />
          </div>
        </div>

        <!-- Derecha: carrusel de screenshots -->
        <div>
          <q-carousel
            v-model="slide"
            animated
            swipeable
            infinite
            height="360px"
            arrows
            navigation
            style="background: transparent;"
          >
            <q-carousel-slide
              v-for="(p, i) in panelsFinal"
              :key="'panel-'+i"
              :name="i"
              class="panel-slide"
            >
              <q-img :src="p.img" alt="panel" class="panel-img" contain />
            </q-carousel-slide>
          </q-carousel>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AdaptiveSection',
  props: {
    logos: {
      type: Array,
      default: () => ([
        './img1.png', './img2.png', './img3.png',
        './img4.png', './img5.png', './img6.png'
      ])
    },
    panels: {
      type: Array,
      default: null
    }
  },
  data () {
    return {
      slide: 0,
      defaultPanels: [
        { img: '/panel1.png', chip: 'Rentabilidad y Finanzas', title: 'Controla la rentabilidad de tu ecommerce', text: 'Controla la rentabilidad de tu ecommerce con márgenes, costes variables y rendimiento operativo siempre actualizados.' },
        { img: '/panel2.png', chip: 'Ventas y conversión', title: 'Rendimiento por canal y funnel', text: 'Visualiza tus ingresos, pedidos, ticket medio y funnel de conversión. Detecta tendencias y evalúa la evolución de tus principales canales de venta.' },
        { img: '/panel3.png', chip: 'Producto', title: 'Métricas por SKU y rotación', text: 'Analiza el rendimiento de tu catálogo con métricas de ventas por SKU, margen y rotación de stock. Identifica productos estrella y los que lastran la rentabilidad.' },
        { img: '/panel4.png', chip: 'Marketing', title: 'Performance multicanal', text: 'Centraliza el performance de campañas en Meta, Google, TikTok, Pinterest y Klaviyo. Controla las métricas claves para escalar con rentabilidad.' },
        { img: '/panel5.png', chip: 'Suscripciones', title: 'MRR y churn bajo control', text: 'Controla el MRR, churn y tasas de renovación de tus clientes de suscripción. Analiza la salud de tu base recurrente.' },
        { img: '/panel6.png', chip: 'Clientes y fidelización', title: 'Retención, recurrencia y LTV', text: 'Mide la retención, recurrencia y LTV de tus clientes. Identifica qué cohortes compran más y cómo impactan tus acciones en la retención.' }
      ]
    }
  },
  computed: {
    logosToShow () { return this.logos.slice(0, 6) },
    panelsFinal () { return (this.panels && this.panels.length ? this.panels : this.defaultPanels).slice(0, 6) },
    currentPanel () { return this.panelsFinal[this.slide] || this.panelsFinal[0] }
  },
  methods: {
    go (i) { this.slide = i }
  }
}
</script>

<style scoped>
.adaptive-wrapper{
  position: relative;
  width: 100%;
}

/* Banda superior lila muy suave */
.band{
  background: linear-gradient(180deg, #f3f0ff 0%, #f6f4ff 100%);
  border-top: 1px solid rgba(123,102,255,.12);
  border-bottom: 1px solid rgba(123,102,255,.12);
  padding: 56px 0 42px;
}

.container{
  max-width: 1180px;
  margin: 0 auto;
  padding: 0 22px;
}

.title{
  margin: 0 0 10px 0;
  text-align: center;
  font-size: 28px;
  line-height: 1.2;
  font-weight: 800;
  color: #6f5bff;
}
.subtitle{
  margin: 0 auto 26px;
  max-width: 820px;
  text-align: center;
  font-size: 15px;
  color: #3a3952;
  opacity: .95;
}
.accent{ color: #3a3952; }

/* Logos */
.logos{
  margin-top: 18px;
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: 22px;
  align-items: center;
}

/* Sección operación */
.section-ops{ padding: 56px 0; }
.ops-title{
  text-align: center;
  font-size: 26px;
  font-weight: 800;
  color: #2a2940;
  margin: 0 0 24px 0;
}
.ops-grid{
  display: grid;
  grid-template-columns: 1.02fr 0.98fr;
  gap: 28px;
  align-items: center;
}

/* Izquierda */
.chip{
  display: inline-block;
  background: #efeaff;
  color: #5b46ff;
  border-radius: 999px;
  padding: 6px 12px;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: .2px;
  margin-bottom: 10px;
}
.ops-h4{
  font-size: 20px;
  margin: 0 0 8px 0;
  color: #2a2940;
}
.ops-p{
  color: #3a3952;
  font-size: 14px;
  opacity: .95;
  margin: 0 0 16px 0;
}

/* Dots */
.dots{ display: flex; gap: 8px; align-items: center; }
.dot{
  width: 8px; height: 8px; border-radius: 50%;
  background: #d6d2ff; cursor: pointer;
  transition: transform .15s ease, background .15s ease;
}
.dot.active{ background: #6f5bff; transform: scale(1.1); }

/* Carrusel / imagen */
.ops-right{ position: relative; }
.panel-carousel{
  border-radius: 14px;
  box-shadow: 0 18px 48px rgba(24,20,40,.10);
  background: #fff;
}
.panel-slide{ display: flex; align-items: center; justify-content: center; }
.panel-img{
  width: 100%;
  max-height: 100%;
  border-radius: 14px;
  background: #fff;
}

/* Responsive */
@media (max-width: 1024px){
  .logos{ grid-template-columns: repeat(3, 1fr); gap: 18px; }
  .ops-grid{ grid-template-columns: 1fr; }
  .panel-img{ margin-top: 6px; }
}
@media (max-width: 640px){
  .title{ font-size: 22px; }
  .ops-title{ font-size: 20px; }
  .subtitle{ font-size: 14px; }
}

/* ===========================
   Animaciones “suaves” (solo CSS)
   =========================== */

/* Entrada escalonada en la banda */
.title,
.subtitle{
  opacity: 0;
  transform: translateY(14px) scale(.985);
  filter: blur(1.5px);
  will-change: transform, opacity, filter;
  animation: fadeUp .65s cubic-bezier(.16,1,.3,1) forwards;
}
.title{ animation-delay: .05s; }
.subtitle{ animation-delay: .16s; }

/* Logos con estela */
.logos .q-img{
  opacity: 0;
  transform: translateY(10px) scale(.985);
  filter: blur(1px);
  animation: fadeUp .5s cubic-bezier(.16,1,.3,1) forwards;
}
.logos .q-img:nth-child(1){ animation-delay: .08s; }
.logos .q-img:nth-child(2){ animation-delay: .12s; }
.logos .q-img:nth-child(3){ animation-delay: .16s; }
.logos .q-img:nth-child(4){ animation-delay: .20s; }
.logos .q-img:nth-child(5){ animation-delay: .24s; }
.logos .q-img:nth-child(6){ animation-delay: .28s; }

/* Texto del bloque operación */
.ops-h4, .ops-p, .dots{
  opacity: 0;
  transform: translateY(14px);
  filter: blur(1px);
  animation: fadeUp .6s cubic-bezier(.16,1,.3,1) forwards;
}
.ops-h4{ animation-delay: .05s; }
.ops-p{  animation-delay: .15s; }
.dots{   animation-delay: .25s; }

/* Carrusel: entra desde la derecha y luego respira sutilmente */
.panel-carousel{
  opacity: 0;
  transform: translateX(22px);
  animation:
    slideInRight .75s cubic-bezier(.16,1,.3,1) .12s forwards,
    glowPulse 4.2s ease-in-out 1.1s infinite;
  will-change: transform, opacity, box-shadow;
}
.panel-img{
  animation: bob 8s ease-in-out 1.2s infinite;
  will-change: transform;
}

/* Keyframes compartidos */
@keyframes fadeUp{
  from{ opacity:0; transform: translateY(14px) scale(.985); filter: blur(1.5px); }
  to  { opacity:1; transform: translateY(0)    scale(1);     filter: blur(0);     }
}
@keyframes slideInRight{
  from{ opacity:0; transform: translateX(22px); }
  to  { opacity:1; transform: translateX(0);    }
}
@keyframes bob{
  0%,100%{ transform: translateY(0); }
  50%    { transform: translateY(-8px); }
}
@keyframes glowPulse{
  0%,100%{ box-shadow: 0 18px 48px rgba(24,20,40,.10); }
  50%    { box-shadow: 0 22px 56px rgba(24,20,40,.14); }
}

/* Respeta reduce motion */
@media (prefers-reduced-motion: reduce){
  .title, .subtitle,
  .logos .q-img,
  .ops-h4, .ops-p, .dots,
  .panel-carousel, .panel-img{
    animation: none !important;
    opacity: 1 !important;
    transform: none !important;
    filter: none !important;
  }
}
</style>
