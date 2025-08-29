<template>
  <q-layout view="lHh Lpr lFf">
    <drawer-menu ref="drawerMenu" :nav-items="navItems" />

    <q-page-container>
      <q-page class="hero-bg">
        <navbar @open-drawer="openDrawer" :nav-items="navItems" />
        <hero-section />

        <!-- Nueva sección -->
        <adaptive-section :logos="logos" />
        <PricingPlans />
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
import Navbar from 'components/Navbar.vue'
import DrawerMenu from 'components/DrawerMenu.vue'
import HeroSection from 'components/HeroSection.vue'
import AdaptiveSection from 'components/AdaptiveSection.vue'
import PricingPlans from "components/PricingPlans.vue";

export default {
  name: 'LoadingPage',
  components: {PricingPlans, Navbar, DrawerMenu, HeroSection, AdaptiveSection },
  data () {
    return {
      navItems: [
        { label: 'Cómo funciona', to: '/funciona' },
        { label: 'Beneficios', to: '/beneficios' },
        { label: 'Roadmap', to: '/roadmap' },
        { label: 'Integraciones', to: '/integraciones' },
        { label: 'Nosotros', to: '/nosotros' },
        { label: 'FAQs', to: '/faqs' }
      ],
      // Ajusta rutas según tu /public
      logos: ['/img1.png','/img2.png','/img3.png','/img4.png','/img5.png','/img6.png']
    }
  },
  methods: {
    openDrawer () { this.$refs.drawerMenu && this.$refs.drawerMenu.open() }
  }
}
</script>

<style scoped>
.hero-bg{
  min-height:100dvh; width:100%; position:relative; overflow:hidden;
  background:
    radial-gradient(1100px 700px at 18% 0%, rgba(160,130,255,.34), rgba(255,255,255,0) 58%),
    radial-gradient(850px 650px at 75% 62%, rgba(142,114,255,.35), rgba(255,255,255,0) 62%),
    linear-gradient(180deg,#ffffff 0%, #f7f4ff 42%, #ece4ff 100%);
}
</style>
