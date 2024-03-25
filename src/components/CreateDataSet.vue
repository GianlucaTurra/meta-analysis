<template>
  <div>
    <h4>Create a new dataset</h4>
    <div class="col">
      <form @submit.prevent="createDataSet">
        <div class="row">
          <select v-model="format" class="form-select form-select-lg mb-3" aria-label="Large select example">
            <option value="standard">Standard</option>
            <option value="pioneer">Pioneer</option>
            <option value="modern">Modern</option>
          </select>
        </div>
        <div class="row">
          <select v-model="timeSpan" class="form-select form-select-lg mb-3" aria-label="Large select example">
            <option value="three-months">Last three months</option>
            <option value="one-month">Last month</option>
          </select>
          <button type="submit" class="btn btn-primary">Create DataSet</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      format: null,
      timeSpan: null
    };
  },
  methods: {
    createDataSet() {
      this.$emit('create-dataset', this.format, this.timeSpan)
    }
  }
}
</script>