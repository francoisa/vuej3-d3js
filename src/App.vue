<template>
  <div id="app">
    <BarChart :chart_data="barChartData"/>
    <div>
      <form v-for="d in fullDataSet" :key="d.name">
          <input type="checkbox" @change="process()" :value="d.name" v-model="checkedNames">
          {{d.name}}
      </form>
    </div>
  </div>
</template>

<script>
import BarChart from './components/BarChart.vue'

export default {
  name: 'App',
  components: {
    BarChart
  },
  methods: {
    compare(a, b) {
      if (a.value > b.value) {
        return -1;
      }
      if (a.value < b.value) {
        return 1;
      }
      return 0;
    },
    process() {
      let remove = this.fullDataSet.map(fds => fds.name);
      this.checkedNames.forEach( n => remove = remove.filter(r => r !== n ));
      remove.forEach(r => this.barChartData = this.barChartData.filter(b => b.name !== r));
      this.checkedNames.forEach( n => {
          let d = this.fullDataSet.find(fds => fds.name === n); 
          this.barChartData.push(d); 
        }
      )
      this.barChartData.sort(this.compare);
    }
  },
  data() {
    return {
      barChartData: [
        { name: 'Andre Francois', value: 100 },
        { name: 'Eric Liu', value: 50 },
        { name: 'Scott Darvin', value: 20 }
      ],
      fullDataSet: [
        { name: 'Steve Rogers', value: 90 },
        { name: 'Bruce Wayne', value: 80 },
        { name: 'Mary Jane', value: 40 }
      ],
      checkedNames: []
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
