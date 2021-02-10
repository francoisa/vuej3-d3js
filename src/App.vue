<template>
  <div id="app">
    <BarChart :chart_data="barChartData"/>
  </div>
</template>

<script>
import BarChart from './components/BarChart.vue'

export default {
  name: 'App',
  components: {
    BarChart
  },
  data() {
    return {
      barChartData: [
        { name: 'Andre Francois', value: 100 },
        { name: 'Eric Liu', value: 50 },
        { name: 'Scott Darvin', value: 20 }
      ] 
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
