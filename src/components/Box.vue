<template>
  <div class="box has-text-weight-bold" :style="estilos">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  /* eslint-disable-next-line */
  name: "Box",
  data() {
    return {
      estilos: {
        'background-color': '#FAF0CA'
      }
    }
  }
})
</script>

<style scoped>

/* .box {
  background: #FAF0CA;
} */
</style>
