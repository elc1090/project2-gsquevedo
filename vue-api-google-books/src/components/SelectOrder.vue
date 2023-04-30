<template>
    <div class="select">
        <label :for="name">{{ name }}</label>
        <select :name="name" v-model="selected">
            <option v-for="(option, index) in options" :value="option.value" :key="index">{{ option.label }}</option>
        </select>
    </div>
</template>
  
<script>
import { defineEmits, ref, watch } from 'vue'

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
            required: true,
            default: ""
        }
    },

    emits: defineEmits(['update:modelValue']),

    setup(props, { emit }) {
        const selected = ref(props.value)

        watch(selected, (newValue) => {
            emit('update:modelValue', newValue)
        })

        return {
            selected,
        }
    }
}
</script>
<style scoped>
.form-group {
  display: flex;
  flex-direction: column;
  margin-bottom: 16px;
}

.form-label {
  margin-bottom: 8px;
  font-weight: bold;
  font-size: 16px;
}

.form-select {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  color: #333;
  background-color: #fff;
  box-shadow: none;
}
</style>
