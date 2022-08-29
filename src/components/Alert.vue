<template>
  <div
    :class="[
      'alert',
      `mode-${mode}`
    ]">
    <div class="alert__container">
      <header class="alert__header">
        <h3
          v-if="title"
          class="alert__title"
        >
          {{ title }}
        </h3>
      </header>
      <div class="alert__body">
        <slot />
      </div>
      <footer class="alert__footer">
        <slot name="actions" />
      </footer>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  props: {
    title: {
      type: String,
    },
    mode: {
      type: String,
      default: 'standalone',
      validator: (val:string) => ['standalone', 'confirmation'].includes(val)
    }
  }
}
</script>

<style scoped>
.alert {
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  display: flex;
  justify-content: center;
  background: rgba(0,0,0,0.5);
}

.mode-standalone {
  position: fixed;
  align-items: center;
}

.mode-confirmation {
  position: absolute;
  align-items: flex-start;
}

.alert__container {
  width: calc(100% - 60px);
  max-width: 250px;
  background: white;
  box-shadow: 0 5px 20px rgba(0,0,0,0.2);
}

.alert__header {
  position: relative;
  margin: 30px 0;
  text-align: center;
}

.alert__close-icon {
  position: absolute;
  top: 50%;
  right: 30px;
  transform: translateY(-50%);
  width: 30px;
  height: 30px;
  cursor: pointer;
}

.alert__body {
  margin: 30px;
}

.alert__footer {
  margin: 10px 30px 30px 30px;
}

.alert__footer button:last-child:not(:first-child) {
  margin-top: 10px;
}
</style>