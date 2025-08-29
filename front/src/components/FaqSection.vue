<template>
  <section class="faq-wrapper">
    <div class="container">
      <h3 class="faq-title">
        Lo que seguramente <span class="accent">te estás preguntando</span>
      </h3>
      <p class="faq-sub">
        No es otro dashboard más. Es el que tomarías si tuvieras que elegir solo uno.
      </p>

      <div class="faq-list">
        <q-card
          v-for="(item, i) in faqs"
          :key="i"
          class="faq-card"
        >
          <q-expansion-item
            dense
            expand-separator
            :default-opened="i === 0"
            group="faq"
          >
            <!-- Header personalizado -->
            <template v-slot:header="scope">
              <div class="faq-header">
                <div class="faq-q">{{ item.q }}</div>
                <q-icon :name="scope.expanded ? 'remove' : 'add'" class="toggle-icn" />
              </div>
            </template>

            <div class="faq-a">
              <p v-for="(p, j) in normalize(item.a)" :key="j" class="faq-p">{{ p }}</p>
              <ul v-if="item.list && item.list.length" class="faq-ul">
                <li v-for="(li, k) in item.list" :key="k">{{ li }}</li>
              </ul>
            </div>
          </q-expansion-item>
        </q-card>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'FaqSection',
  data () {
    return {
      faqs: [
        {
          q: '¿Qué es exactamente StoreCopilot?',
          a: `StoreCopilot es un Consultant SaaS: un copiloto de datos diseñado para eCommerce.
              No es un dashboard genérico: conectamos tus fuentes de datos, personalizamos reportes
              y te ayudamos a tomar decisiones rentables.`
        },
        {
          q: '¿Qué diferencia a StoreCopilot de otros dashboards?',
          a: `No vendemos “plantillas”; diseñamos paneles a medida para tu modelo y etapa de crecimiento.
              Unificamos métricas de finanzas, ventas, marketing, logística e inventario para responder:
              “¿Estamos creciendo de forma rentable?”`
        },
        {
          q: '¿Necesito conocimientos técnicos para usar StoreCopilot?',
          a: `No. Lo implementamos contigo y dejamos flujos automáticos. Tú decides; nosotros
              nos encargamos de la orquestación de datos.`
        },
        {
          q: '¿Con qué plataformas se integra?',
          a: `Trabajamos con los principales ecosistemas y pasarelas.`,
          list: [
            'Tiendas: Shopify (nativo), WooCommerce (conector).',
            'Marketing: Meta, Google, TikTok, Pinterest, Klaviyo.',
            'Pagos: Shopify Payments, PayPal, Klarna, SeQura, Afterpay, etc.',
            'Datos/ERP/Contabilidad: conectores a medida bajo demanda.'
          ]
        },
        {
          q: '¿Cuánto tiempo tardaré en ver resultados?',
          a: `Primer panel en 1–2 semanas. Mejora de rentabilidad desde el primer mes
              al optimizar márgenes, canales y logística.`
        },
        {
          q: '¿Puedo personalizar los reportes?',
          a: `Sí, personalizamos KPIs, cohortes, vistas y permisos por equipo
              (dirección, marketing, finanzas, operaciones).`
        },
        {
          q: '¿Qué pasa si mi negocio crece o cambia?',
          a: `Escalamos contigo: añadimos nuevas fuentes/tiendas/países y ajustamos
              reportes cuando tu estrategia evoluciona.`
        },
        {
          q: '¿Cuánto cuesta StoreCopilot?',
          a: `Core Plan desde 90 € / mes* y planes AD HOC para integraciones y reporting avanzado.
              Agenda una demo para un estimado ajustado a tu caso.`
        }
      ]
    }
  },
  methods: {
    normalize (txt) {
      return Array.isArray(txt) ? txt : String(txt).split('\n').filter(Boolean)
    }
  }
}
</script>

<style scoped>
.faq-wrapper{
  background: linear-gradient(180deg, #ffffff 0%, #fbfaff 100%);
  border-top: 1px solid rgba(123,102,255,.12);
  padding: 56px 0;
}
.container{
  max-width: 1180px;
  margin: 0 auto;
  padding: 0 22px;
}

.faq-title{
  text-align: center;
  font-size: 26px;
  font-weight: 900;
  color: #23233a;
  margin: 0 0 6px 0;
}
.faq-sub{
  text-align: center;
  color: #54526e;
  font-size: 14px;
  margin: 0 0 22px 0;
}
.accent{ color:#6f5bff; }

.faq-list{
  display: grid;
  grid-template-columns: 1fr;
  gap: 12px;
}

.faq-card{
  border-radius: 12px;
  background: #fff;
  border: 1px solid rgba(123,102,255,.20);
  box-shadow: 0 10px 26px rgba(24,20,40,.06);
  overflow: hidden;
}

.faq-header{
  width: 100%;
  display: grid;
  grid-template-columns: 1fr auto;
  align-items: center;
  padding: 12px 14px;
}
.faq-q{
  font-weight: 800;
  color: #1e2340;
  font-size: 15px;
  line-height: 1.25;
  white-space: normal;
  word-break: break-word;
  overflow-wrap: anywhere;
}
.toggle-icn{ color: #1e2340; }

.faq-a{ padding: 0 14px 14px 14px; }
.faq-p{
  margin: 8px 0 0 0;
  color: #3a3952;
  font-size: 14px;
  line-height: 1.45;
}
.faq-ul{
  margin: 6px 0 0 16px;
  padding: 0;
  color: #3a3952;
  font-size: 14px;
  line-height: 1.45;
}

@media (max-width: 640px){
  .faq-title{ font-size: 22px; }
  .faq-q{ font-size: 14px; }
  .faq-p, .faq-ul{ font-size: 13px; }
}
</style>
