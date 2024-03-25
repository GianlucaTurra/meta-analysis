<template>
  <div class="container">
    <h2>Meta Analysis</h2>
    <div class="row">
      <div class="col">
        <CreateDataSet @create-dataset="getNewDataset"/>  
      </div>
      <div class="col">
        <UseExistingDataSet :dataSets="dataSets" @use-existing-dataset="getExistingDataset"/>
      </div>
    </div>
  </div>
</template>

<style>
.container {
  text-align: center;
}
</style>

<script>
import CreateDataSet from './CreateDataSet.vue';
import UseExistingDataSet from './UseExistingDataSet.vue';

export default {
  name: 'LandingPage',
  components: {
    CreateDataSet,
    UseExistingDataSet
  },
  mounted() {
    this.fetchDataSets();
  }, 
  methods: {
    getNewDataset(selectedFormat, selectedTimeSpan) {
      console.log(selectedFormat, selectedTimeSpan);
    },
    getExistingDataset(selectedDataSet) {
      console.log(selectedDataSet)
    },
    fetchDataSets() {
      fetch('https://example.com/api/options')
        .then(response => response.json())
        .then(data => {this.dataSets = data;})
        .catch(error => console.log('Error fetching datasets: ', error))
    }
  },
  data() {
    return {
      dataSets: [
        { id: 1, value: 'first-dataset', label: '2024-01-01' },
        { id: 2, value: 'second-dataset', label: '2024-01-15' },
        { id: 3, value: 'third-dataset', label: '2024-03-01' }
      ]
    };
  }
}
</script>