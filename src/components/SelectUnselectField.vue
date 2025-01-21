<!-- Vue component -->
<template>
  <div>
    <select v-model="selected" @change="updateSelection" multiple="true">
      <option v-for="option in options" :key="option.value" :value="option.value">
        {{ option.text }} ({{ option.status }})
      </option>
    </select>
  </div>
  <div>
    <select v-model="selected" @change="updateSelection" multiple="true">
      <option v-for="option in options" :key="option.value" :value="option.value">
        {{ option.text }} ({{ option.status }})
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    options: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      selected: null
    }
  },
  methods: {
    updateSelection() {
      const selectedOption = this.options.find(option => option.value === this.selected);
      selectedOption.status = selectedOption.status === 'Available' ? 'Disabled' : 'Available';
      this.$emit('update', this.options);
    }
  }
}
</script>
