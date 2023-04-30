<template>
    <div class="radio">
        <label v-for="(option, index) in options" :key="index">
        <input type="radio" :name="name" :value="option.value" v-model="selected">
        {{ option.label }}
        </label>
    </div>
</template>

<script>
import { ref, watch } from 'vue'

export default {
    name: "RadioInput",
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
            default: "title"
        }
    },
    setup(props, { emit }) {
        const selected = ref(props.value)

        watch(selected, (newValue) => {
            emit('update:modelValue', newValue)
        })

        return {
            selected,
            watch
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
