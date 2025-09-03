<template>
  <section class="founders-wrapper">
    <!-- Banda superior con claim -->
    <div class="band">
      <div class="container">
        <div class="band-grid">
          <div class="band-text">
            <h3 class="band-title">
              Hecha por ecommerce founders,
              <span class="accent">para ecommerce founders.</span>
            </h3>
            <p class="band-p">
              <b>Store Copilot no nace en una hoja de cálculo.</b>
              Nace en el día a día de gestionar ecommerce reales,
              <b>algunos de ellos con una facturación superior a 1M € al año.</b>
              Sí, además de agencia, somos tienda. Y como tú, hemos vivido lo que
              significa escalar sin saber si de verdad estás ganando dinero.
            </p>
          </div>
        </div>
      </div>
    </div>

    <!-- ¿Por qué creamos Store Copilot? -->
    <div class="container why-grid">
      <!-- Izquierda: imagen del gráfico (en desktop) -->
      <div class="why-left">
        <div class="chart-card" style="background: transparent;">
          <q-img :src="chartImage" alt="Gráfico" contain class="chart-img" />
        </div>
      </div>

      <!-- Derecha: texto -->
      <div class="why-right">
        <h3 class="why-title">
          ¿Por qué <span class="accent">creamos Store Copilot?</span>
        </h3>

        <p class="why-p">
          En <b>Copilot Agency</b>, llevamos años <b>ayudando a ecommerce crecer.</b>
        </p>
        <br>
        <p class="why-p">
          Pero también gestionamos nuestros propios ecommerce.
        </p>
        <br>
        <p class="why-p">
          Y ahí aprendimos una lección clave:
          <b>facturar más no siempre significa ser más rentable.</b>
        </p>
        <br>
        <p class="why-p">
          Hemos visto muchos clientes con datos por todas partes (Shopify, Ads, Klaviyo, Excel…)
          pero sin una respuesta clara a la pregunta más importante:
          <b>“¿Estamos creciendo de forma rentable?”</b>
        </p>
        <br>
        <p class="why-p">
          Por eso nació <b>Store Copilot</b>: no como otro dashboard más, sino como
          <b>la herramienta que nos habría encantado tener desde el primer día.</b>
        </p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'FoundersSection',
  props: {
    chartImage: {
      type: String,
      default: '/chart.png' // pon aquí tu ruta real
    }
  }
}
</script>

<style scoped>
.founders-wrapper{
  background: #fff;
}

/* ===== Banda superior ===== */
.band{
  background: linear-gradient(180deg, #f3f1ff 0%, #f7f5ff 100%);
  border-top: 1px solid rgba(123,102,255,.12);
  border-bottom: 1px solid rgba(123,102,255,.12);
  padding: 46px 0;
}
.container{
  max-width: 1180px;
  margin: 0 auto;
  padding: 0 22px;
}
.band-grid{
  display: grid;
  grid-template-columns: 1fr;
}
.band-text{ max-width: 980px; margin: 0 auto; }
.band-title{
  margin: 0 0 10px 0;
  font-size: 28px;
  line-height: 1.18;
  font-weight: 900;
  color: #23233a;
  text-align: left;
}
.band-p{
  margin: 0;
  font-size: 15px;
  color: #343349;
  opacity: .95;
}
.accent{ color:#6f5bff; }

/* ===== Sección “¿Por qué…?” ===== */
.why-grid{
  display: grid;
  grid-template-columns: 1.05fr 0.95fr;
  gap: 28px;
  align-items: center;
  padding: 54px 22px;
}
.why-left{ order: 1; }
.why-right{ order: 2; }

.chart-card{
  border-radius: 16px;
}
.chart-img{ width: 100%; height: 100%; display:block; }

.why-title{
  margin: 0 0 10px 0;
  font-size: 30px;
  line-height: 1.18;
  font-weight: 900;
  color: #23233a;
}
.why-p{
  margin: 8px 0;
  color: #3a3952;
  font-size: 15px;
}

/* ===== Responsive ===== */
@media (max-width: 1024px){
  .why-grid{
    grid-template-columns: 1fr;
    gap: 18px;
    padding: 36px 22px;
  }
  /* En mobile, primero texto y luego imagen (como tu mock de la izquierda) */
  .why-left{ order: 2; }
  .why-right{ order: 1; }
  .band-title{ font-size: 24px; }
}
@media (max-width: 640px){
  .band-title{ font-size: 22px; }
  .why-title{ font-size: 22px; }
  .why-p, .band-p{ font-size: 14px; }
}
</style>
