<template>
  <q-drawer
    v-model="drawer"
    side="right"
    overlay
    bordered
    :width="280"
    content-class="drawer-bg"
  >
    <div class="q-pa-md">
      <div class="row items-center q-mb-md">
        <q-img src="/logo.svg" width="28px" class="q-mr-sm" />
        <span class="text-subtitle1 text-weight-bold">StoreCopilot</span>
      </div>

      <q-list padding>
        <q-item
          v-for="item in navItems"
          :key="item.to"
          clickable
          v-ripple
          :to="item.to"
          @click="drawer = false"
        >
          <q-item-section>{{ item.label }}</q-item-section>
        </q-item>

        <q-separator class="q-my-md" />

        <div class="column q-gutter-sm">
          <q-btn flat no-caps label="Login" class="q-px-md" />
          <q-btn no-caps color="dark" label="Demo" class="q-px-md" unelevated />
        </div>
      </q-list>
    </div>
  </q-drawer>
</template>

<script setup>
import { ref } from 'vue'

const drawer = ref(false)
const props = defineProps({
  navItems: {
    type: Array,
    default: () => ([])
  }
})

// expone el estado para controlarlo desde el padre
defineExpose({ drawer })
</script>

<style scoped>
.drawer-bg{
  background:
    radial-gradient(600px 400px at 80% 100%, rgba(160,130,255,.12), transparent 60%),
    #fff;
}
</style>
