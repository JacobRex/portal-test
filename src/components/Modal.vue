<template>
  <div class="modal">
    <div class="modal__container">
      <header class="modal__header">
        <img
          class="modal__close-icon"
          src="../assets/x.svg"
          @click="$emit('close')"
        />
        <h3
          v-if="title"
          class="modal__title"
        >
          {{ title }}
        </h3>
      </header>
      <div class="modal__body">
        <slot />
      </div>
      <footer
        v-if="$slots.actions"
        class="modal__footer"
      >
        <slot name="actions" />
      </footer>
      <portal-target name="modal-component-layer" />
    </div>
  </div>
</template>

<script lang="ts">
import { PortalTarget } from 'portal-vue';

export default {
  components: {
    PortalTarget,
  },
  props: {
    title: {
      type: String,
    }
  }
}
</script>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0,0,0,0.5);
}

.modal__container {
  position: relative;
  width: calc(100% - 60px);
  max-width: 500px;
  background: white;
  box-shadow: 0 5px 20px rgba(0,0,0,0.2);
}

.modal__header {
  position: relative;
  margin: 30px 0;
  text-align: center;
}

.modal__close-icon {
  position: absolute;
  top: 50%;
  right: 30px;
  transform: translateY(-50%);
  width: 30px;
  height: 30px;
  cursor: pointer;
}

.modal__body {
  margin: 30px;
}

.modal__footer {
  display: flex;
  justify-content: space-between;
  padding: 10px 30px;
  border-top: 1px solid #ddd;
}
</style>