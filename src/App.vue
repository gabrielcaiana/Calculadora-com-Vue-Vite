<template>
  <div class="app">
    <Calculator />
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'
export default {
  components: {
    Calculator
  }
}
</script>

<style lang="scss" scoped>
 .app {
   height: 100vh;
   display: flex;
   align-items: center;
   justify-content: center;
   font-family: -apple-system, 'Open Sans', 'Helvetica Neue', sans-serif;
 }
</style>
