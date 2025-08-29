<template>
  <footer class="site-footer">
    <div class="container">

      <!-- CTA card -->
      <div class="cta-card">
        <div class="brand row items-center justify-center q-gutter-sm">
          <q-img src="/logo.svg" width="40px" class="logo" contain />
          <div class="brand-name">Store<span class="accent-bold">Copilot</span></div>
        </div>

        <h3 class="cta-title">
          ¿Quieres ver <span class="accent">tu tienda</span><br class="br-md" />
          como nunca antes?
        </h3>

        <q-btn
          class="cta-btn"
          no-caps
          label="Reserva una demo ahora"
          @click="onDemo"
        />
      </div>

      <q-separator class="sep" color="white" />

      <!-- Legal row -->
      <div class="legal-row">
        <div class="links">
          <a href="#" class="footer-link">Aviso Legal</a>
          <a href="#" class="footer-link">Política de Privacidad</a>
          <a href="#" class="footer-link">Política de Cookies</a>
        </div>

        <div class="copy">
          © {{ year }} Store Copilot — Todos los derechos reservados.
        </div>
      </div>

    </div>
  </footer>
</template>

<script>
export default {
  name: 'SiteFooter',
  computed: {
    year () {
      return new Date().getFullYear()
    }
  },
  methods: {
    onDemo () {
      // Reemplaza por tu navegación/modal real
      // this.$router.push('/demo')
      this.$q.notify({
        color: 'primary',
        message: 'Abrir flujo para reservar demo',
        position: 'top',
        timeout: 1200
      })
    }
  }
}
</script>

<style scoped>
.site-footer{
  position: relative;
  color: #e9ebff;
  padding: 56px 0 28px;
  /* Fondo azul con halo lila suave */
  background:
    radial-gradient(900px 420px at 42% -8%, rgba(124,102,255,.20), rgba(124,102,255,0) 60%),
    linear-gradient(180deg, #0e1e47 0%, #081634 100%);
}
.container{
  max-width: 1180px;
  margin: 0 auto;
  padding: 0 22px;
}

/* CTA */
.cta-card{
  position: relative;
  margin: 0 auto 24px;
  padding: 26px 24px;
  max-width: 820px;
  background: rgba(13, 23, 60, .78);
  backdrop-filter: blur(4px);
  border: 1px solid rgba(255,255,255,.08);
  border-radius: 20px;
  box-shadow: 0 26px 60px rgba(6, 10, 28, .5);
  text-align: center;
}
.brand .logo{ filter: drop-shadow(0 2px 6px rgba(0,0,0,.2)); }
.brand-name{
  font-weight: 900; letter-spacing: .2px;
  color: #fff; font-size: 18px;
}
.accent-bold{ color: #a9a6ff; }

.cta-title{
  margin: 10px 0 16px;
  font-size: 28px;
  font-weight: 900;
  color: #ffffff;
  line-height: 1.15;
}
.accent{ color: #b5a8ff; }
.br-md{ display: none; } /* salto solo en md+ */

.cta-btn{
  background: linear-gradient(180deg, #6d58ff, #5a49e6);
  color:#fff; font-weight: 800;
  border-radius: 12px;
  padding: 12px 18px;
  min-width: 260px;
  box-shadow: 0 16px 38px rgba(109,88,255,.35);
  transition: transform .15s ease, box-shadow .15s ease, filter .15s ease;
}
.cta-btn:hover{
  transform: translateY(-1px);
  box-shadow: 0 22px 48px rgba(109,88,255,.42);
  filter: brightness(1.02);
}

/* Separator */
.sep{
  opacity: .25;
  margin: 20px 0 12px;
}

/* Legal */
.legal-row{
  display: grid;
  grid-template-columns: 1fr auto;
  align-items: center;
  gap: 12px;
}
.links{
  display: flex; flex-wrap: wrap; gap: 18px;
}
.footer-link{
  color: #cfd3ff;
  text-decoration: none;
  font-size: 13px;
  opacity: .9;
}
.footer-link:hover{ opacity: 1; text-decoration: underline; }
.copy{
  color: #c1c6f9;
  font-size: 13px;
  opacity: .9;
  text-align: right;
}

/* Responsive */
@media (max-width: 900px){
  .cta-title{ font-size: 24px; }
  .br-md{ display: inline; }
}
@media (max-width: 640px){
  .cta-card{
    padding: 22px 18px;
    border-radius: 16px;
  }
  .cta-title{ font-size: 20px; }
  .brand-name{ font-size: 16px; }
  .legal-row{
    grid-template-columns: 1fr;
    text-align: center;
  }
  .links{ justify-content: center; }
  .copy{ text-align: center; }
}
</style>
