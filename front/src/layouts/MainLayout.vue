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
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
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

