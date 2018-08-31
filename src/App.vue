<template>
  <div id="app">
    <h1 class="title">Car filters</h1>
    <car-filter></car-filter>
  </div>
</template>

<script>
import carFilter from './components/Car-filter.vue';

export default {
  name: 'app',
  components: {
    carFilter
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.title {
  margin-bottom: 30px;
}
</style>
