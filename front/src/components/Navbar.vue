<template>
  <div class="nav-card">
    <div class="nav-inner">
      <!-- Logo -->
      <div class="nav-left row items-center">
        <!-- Mobile: botón menú -->
        <q-btn
          v-show="$q.screen.lt.md"
          round dense flat icon="menu"
          class="menu-fab q-pl-md"
          @click="$emit('open-drawer')"
        />
        <q-img src="/logo.svg" alt="StoreCopilot" width="42px" class="logo" contain />
        <span class="q-pl-md">Store <b>Copilot</b></span>
      </div>

      <!-- Links (solo desktop) -->
      <div class="nav-center">
        <q-tabs dense shrink class="nav-tabs" v-show="!$q.screen.lt.md">
          <q-route-tab
            v-for="item in navItems"
            :key="item.to"
            :label="item.label"
            :to="item.to"
            exact
            no-caps
          />
        </q-tabs>
      </div>

      <!-- Derecha -->
      <div class="nav-right">
        <div class="row items-center" v-show="!$q.screen.lt.md">
          <q-btn flat no-caps label="Login" class="q-mr-sm text-weight-medium" />
          <q-btn no-caps label="Demo" class="btn-demo" />
        </div>

        <!-- Mobile atajos -->
        <q-btn
          v-show="$q.screen.lt.md"
          round dense label="Login" no-caps class="text-primary" flat
          @click="$emit('open-drawer')"
        />
        <q-btn
          v-show="$q.screen.lt.md"
          class="q-ml-md"
          color="dark"
          label="Demo"
          no-caps
          @click="$emit('open-drawer')"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  props: {
    navItems: { type: Array, default: () => [] }
  }
}
</script>

<style scoped>
.nav-card{
  position:absolute; top:16px; left:16px; right:16px;
  max-width:1180px; margin:0 auto; background:#fff; color:#000;
  border-radius:16px;
  box-shadow:0 10px 30px rgba(24,20,40,.08), 0 2px 6px rgba(24,20,40,.05);
}
.nav-inner{
  display:grid; grid-template-columns:auto 1fr auto;
  align-items:center; padding:10px 12px; gap:8px;
}
.logo{ filter: drop-shadow(0 2px 6px rgba(0,0,0,.04)); }
.btn-demo{
  background:#262438; color:#fff; border-radius:12px; padding:8px 16px; font-weight:700;
}
.menu-fab{ border-radius:12px; }
</style>
