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
      fetch('http://127.0.0.1:5000/data_records')
        .then(response => response.json())
        .then(data => {this.dataSets = data;})
        .catch(error => console.log('Error fetching datasets: ', error))
    }
  },
  data() {
    return {
      dataSets: [],
    };
  }
}
</script>