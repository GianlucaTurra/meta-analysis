<template>
  <div>
    <h4>Use an existing dataset</h4>
    <div class="col">
      <form @submit.prevent="useExistingDataSet">
        <div class="row">
          <select v-model="selectedDataSet" class="form-select form-select-lg mb-3" aria-label="Large select example">
            <option v-for="dataSet in dataSets" :key="dataSet.id" :value="dataSet.value">{{ dataSet.label }}</option>
          </select>
        </div>
        <div class="row"></div>
        <div class="row">
          <button type="submit" class="btn btn-primary">Select Dataset</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    dataSets: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      selectedDataSet: null
    };
  },
  methods: {
    useExistingDataSet() {
      this.$emit('use-existing-dataset', this.selectedDataSet)
    }
  }
}
</script>