<template>
  <section class="adaptive-wrapper">

    <!-- Banda suave como en Figma -->
    <div class="band">
      <div class="container">

        <!-- Título y bajada -->
        <h2 class="title">
          Un dashboard que se adapta a tu <span class="accent">negocio</span>, no al revés
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
            width="125px"
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

      <div class="ops-grid">
        <!-- Izquierda: texto (sincronizado al slide actual) -->
        <div class="ops-left">
          <div class="chip">{{ currentPanel.chip }}</div>
          <h4 class="ops-h4">{{ currentPanel.title }}</h4>
          <p class="ops-p">{{ currentPanel.text }}</p>

          <!-- Paginación decorativa (puntos) -->
          <div class="dots">
            <span
              v-for="(p, i) in panelsFinal"
              :key="'dot-'+i"
              class="dot"
              :class="{ active: slide === i }"
              @click="go(i)"
            />
          </div>
        </div>

        <!-- Derecha: carrusel de screenshots -->
        <div class="ops-right">
          <q-carousel
            v-model="slide"
            animated
            swipeable
            infinite
            transition-prev="slide-right"
            transition-next="slide-left"
            height="360px"
            arrows
            navigation
            control-color="primary"
            class="panel-carousel"
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
    // 6 logos como máximo (se ajusta responsivo)
    logos: {
      type: Array,
      default: () => ([
        './img1.png', './img2.png', './img3.png',
        './img4.png', './img5.png', './img6.png'
      ])
    },
    // Permite sobreescribir los paneles desde el padre si quieres
    panels: {
      type: Array,
      default: null
    }
  },
  data () {
    return {
      slide: 0,
      // Defecto: panel1..panel6 en /public/panels/
      defaultPanels: [
        {
          img: '/panel1.png',
          chip: 'Rentabilidad y Finanzas',
          title: 'Controla la rentabilidad de tu ecommerce',
          text: 'Controla la rentabilidad de tu ecommerce con márgenes, costes variables y rendimiento operativo siempre actualizados.'
        },
        {
          img: '/panel2.png',
          chip: 'Ventas y conversión',
          title: 'Rendimiento por canal y funnel',
          text: 'Visualiza tus ingresos, pedidos, ticket medio y funnel de conversión. Detecta tendencias y evalúa la evolución de tus principales canales de venta.'
        },
        {
          img: '/panel3.png',
          chip: 'Producto',
          title: 'Métricas por SKU y rotación',
          text: 'Analiza el rendimiento de tu catálogo con métricas de ventas por SKU, margen y rotación de stock. Identifica productos estrella y los que lastran la rentabilidad.'
        },
        {
          img: '/panel4.png',
          chip: 'Marketing',
          title: 'Performance multicanal',
          text: 'Centraliza el performance de campañas en Meta, Google, TikTok, Pinterest y Klaviyo. Controla las métricas claves para escalar con rentabilidad.'
        },
        {
          img: '/panel5.png',
          chip: 'Suscripciones',
          title: 'MRR y churn bajo control',
          text: 'Controla el MRR, churn y tasas de renovación de tus clientes de suscripción. Analiza la salud de tu base recurrente.'
        },
        {
          img: '/panel6.png',
          chip: 'Clientes y fidelización',
          title: 'Retención, recurrencia y LTV',
          text: 'Mide la retención, recurrencia y LTV de tus clientes. Identifica qué cohortes compran más y cómo impactan tus acciones en la retención.'
        }
      ]
    }
  },
  computed: {
    logosToShow () {
      return this.logos.slice(0, 6)
    },
    panelsFinal () {
      const list = (this.panels && this.panels.length) ? this.panels : this.defaultPanels
      return list.slice(0, 6)
    },
    currentPanel () {
      return this.panelsFinal[this.slide] || this.panelsFinal[0]
    }
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
  color: #2a2940;
}
.subtitle{
  margin: 0 auto 26px;
  max-width: 820px;
  text-align: center;
  font-size: 15px;
  color: #3a3952;
  opacity: .95;
}
.accent{ color: #6f5bff; }

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
  font-weight: 800;
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
</style>
