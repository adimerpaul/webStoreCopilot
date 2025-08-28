<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>
          <q-tabs>
            <q-route-tab
              label="Como funciona"
              to="/mails"
              exact
              no-caps
            />
            <q-route-tab
              label="Beneficios"
              to="/alarms"
              exact
              no-caps
            />
            <q-route-tab
              label="Roadmap"
              to="/roadmap"
              exact
              no-caps
            />
            <q-route-tab
              label="Integraciones"
              to="/integrations"
              exact
              no-caps
            />
            <q-route-tab
              label="Nosotros"
              to="/about"
              exact
              no-caps
            />
            <q-route-tab
              label="FAQs"
              to="/faqs"
              exact
              no-caps
            />
          </q-tabs>
        </div>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <q-page class="hero-bg">
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: "LoadingPage",
};
</script>

<style scoped>
.hero-bg {
  min-height: 100vh;
  width: 100%;

  /* Degradado más parecido al Figma */
  background:
    radial-gradient(
      circle at top left,
      rgba(160, 130, 255, 0.35) 0%,
      rgba(255, 255, 255, 0) 40%
    ),
    radial-gradient(
      circle at bottom right,
      rgba(160, 130, 255, 0.3) 0%,
      rgba(255, 255, 255, 0) 40%
    ),
    linear-gradient(
      180deg,
      #ffffff 0%,
      #f9f7ff 40%,
      #f0eaff 100%
    );
}
</style>

