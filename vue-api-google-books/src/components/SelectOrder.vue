<template>
    <div class="select">
        <label :for="name">{{ name }}</label>
        <select :name="name" v-model="selected">
            <option class="group" v-for="(option, index) in options" :value="option.value" :key="index">{{ option.label }}</option>
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
            default: "relevance"
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
.select {
    margin-top: 15px;
}
.group {
  display: flex;
  flex-direction: column;
  margin-bottom: 16px;
}

label {
  margin-bottom: 8px;
  font-weight: bold;
  font-size: 18px;
  
}

select {
  padding: 6px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  color: #333;
  background-color: #fff;
  box-shadow: none;
}
</style>
