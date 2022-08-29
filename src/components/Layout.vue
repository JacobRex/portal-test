<template>
  <div class="layout">
    <slot />
    <portal-target name="modal-layer" />
    <portal-target name="alert-layer" />
  </div>
</template>

<script lang="ts">
import { PortalTarget } from 'portal-vue';

export default {
  components: {
    PortalTarget
  }
}
</script>

<style scoped>
.layout {
  position: relative;
}
</style>