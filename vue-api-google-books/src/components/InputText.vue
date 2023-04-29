<template>
    <input v-model="inputValue" :type="type" :placeholder="placeholder">
</template>

<script>
import { ref } from 'vue'

export default {
    setup() {
        const inputValue = ref("")

        return {
            inputValue
        }
    },
    props: {
        type: {
            type: String,
            default: "text",
            required: true
        },
        placeholder: {
            type: String
        }
    }
}
</script>
<style scoped>
    input {
        border: 0;
        border-bottom: 2px solid #9e9e9e;
        outline: none;
        transition: 0.2s ease-in-out;
        box-sizing: border-box;
    }
    label {
        top: 0;
        left: 0;
        right: 0;
        color: #616161;
        display: flex;
        align-items: center;
        position: absolute;
        font-size: 1rem;
        cursor: text;
        transition: 0.2s ease-in-out;
        box-sizing: border-box;
    }
    input, label {
        width: 100%;
        height: 3rem;
        font-size: 1rem;
    }
</style>