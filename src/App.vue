<template>
  <main class="wrapper">
    <Calculator />
  </main>
</template>

<script>
import Calculator from '@/components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>

<style lang="scss">
  @import '@/styles/main.scss';
</style>
