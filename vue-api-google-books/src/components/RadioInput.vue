<template>
  <div class="radio">
    <label v-for="(option, index) in options" :key="index">
      <input type="radio" :name="name" :value="option.value" v-model="selected">
      {{ option.label }}
    </label>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  props: {
    name: {
      type: String,
      required: true
    },
    options: {
      type: Array,
      required: true
    },
    value: {
      type: String,
      required: true
    }
  },
  setup(props, { emit }) {
    const selected = ref(props.value)
  
    const updateSelected = (event) => {
      selected.value = event.target.value
      emit('update:modelValue', selected.value)
    }
  
    return {
      selected,
      updateSelected
    }
  }
}
</script>
<style scoped>
.radio {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  margin-top: 10px;
}

.radio label {
  font-size: 18px;
  color: #333;
}
</style>






