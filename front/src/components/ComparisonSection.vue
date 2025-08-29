<template>
  <section class="compare-wrapper">
    <div class="container">
      <h3 class="compare-title">
        Lo que Store Copilot hace <span class="accent">(y otros no)</span>
      </h3>
      <p class="compare-sub">
        No es otro dashboard más. Es el que tomarías si tuvieras que elegir solo uno.
      </p>

      <!-- scroller para pantallas estrechas -->
      <div class="table-scroller">
        <q-markup-table flat class="cmp-table" wrap-cells>
          <thead>
          <tr class="head">
            <th class="left-th">Funcionalidad</th>
            <th class="mid-col mid-th">Store Copilot</th>
            <th class="right-th">Dashboard genérico</th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="(f, i) in items" :key="i">
            <td class="feat-cell">
              {{ f }}
            </td>
            <td class="mid-col">
              <div class="badge check">
                <q-icon name="check"/>
              </div>
            </td>
            <td class="right-col">
              <div class="badge cross">
                <q-icon name="close"/>
              </div>
            </td>
          </tr>
          </tbody>
        </q-markup-table>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ComparisonSection',
  props: {
    items: {
      type: Array,
      default: () => ([
        'Unifica finanzas, marketing, ventas, stock y fidelización en un solo panel',
        'Reportes personalizados según tu negocio y etapa de crecimiento',
        'Integraciones a medida con tus sistemas clave (ERP, contabilidad, CRM, suscripciones)',
        'Accesible y fácil de usar, sin conocimientos técnicos',
        'Pensado específicamente para eCommerce en Shopify'
      ])
    }
  }
}
</script>

<style scoped>
.compare-wrapper{
  background: linear-gradient(180deg,#f4f2ff 0%, #ffffff 36%);
  border-top: 1px solid rgba(123,102,255,.12);
  padding: 56px 0;
}
.container{
  max-width: 1180px;
  margin: 0 auto;
  padding: 0 22px;
}

.compare-title{
  text-align:center;
  font-size:26px;
  font-weight:900;
  color:#23233a;
  margin:0 0 6px 0;
}
.compare-sub{
  text-align:center;
  color:#54526e;
  font-size:14px;
  margin:0 0 18px 0;
}
.accent{ color:#6f5bff; }

/* ===== Tabla ===== */
.table-scroller{
  overflow-x:auto;
  -webkit-overflow-scrolling: touch;
}
.cmp-table{
  min-width: 760px;            /* permite scroll horizontal en móviles muy estrechos */
  border: 1px dashed rgba(0,0,0,.18);
  border-radius: 12px;
  overflow: hidden;
  background:#fff;
}
.cmp-table thead tr.head th{
  font-weight:800; font-size:14px; color:#1f2237;
  padding: 14px 16px;
  border-bottom: 1px dashed rgba(0,0,0,.18);
}
.cmp-table tbody td{
  padding: 14px 16px;
  border-top: 1px dashed rgba(0,0,0,.12);
}

/* Columna izquierda (texto con line wrap) */
.feat-cell{
  white-space: normal;          /* wrap */
  word-break: break-word;       /* rompe palabras largas si hace falta */
  overflow-wrap: anywhere;      /* fuerza salto si no hay espacios */
  font-size:14px; color:#2b2942; line-height:1.35;
}

/* Columna morada (centro) */
.mid-col{
  background:#6f5bff;
  color:#fff;
  text-align:center;
  border-left: 1px dashed rgba(255,255,255,.35);
  border-right: 1px dashed rgba(255,255,255,.35);
}
.mid-th{ color:#fff; }

/* Columna derecha */
.right-col{ text-align:center; }

/* Badges */
.badge{
  width: 28px; height: 28px; border-radius:50%;
  display:flex; align-items:center; justify-content:center;
  font-weight:900; margin: 0 auto;
}
.badge.check{ border:2px solid #fff; color:#fff; }
.badge.cross{ border:2px solid #23233a; color:#23233a; }
.badge .q-icon{ font-size:18px; }

/* Responsive */
@media (max-width: 640px){
  .compare-title{ font-size:22px; }
  .cmp-table thead tr.head th{ font-size:13px; padding: 12px; }
  .cmp-table tbody td{ padding: 12px; }
  .feat-cell{ font-size:13px; }
  .badge{ width:24px; height:24px; }
  .badge .q-icon{ font-size:16px; }
}
</style>
