<template>
  <button
    :class="[
      'button',
      `variant-${variant}`,
      {fullwidth}
    ]"
    @click="$emit('click')"
  >
    <slot />
  </button>
</template>

<script lang="ts">
export default {
  props: {
    variant: {
      type: String,
      default: 'filled',
      validator: (val:string) => ['filled', 'outline'].includes(val)
    },
    fullwidth: {
      type: Boolean
    }
  }
}
</script>

<style scoped>
.button {
  display: inline-block;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  outline: none;
}

.variant-filled {
  color: white;
  background: #1243BA;
}

.variant-outline {
  color: #1243BA;
  background: #fff;
  box-shadow: inset 0 0 0 2px #1243BA;
}

.fullwidth {
  width: 100%;
}
</style>
