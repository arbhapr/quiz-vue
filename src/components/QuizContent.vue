<template>
    <section id="question-container">
        <h1 class="question-title">{{ question.text }}</h1>
    </section>
    <section id="options-container">
        <div class="option" v-for="option in question.answers" :key="option.id" @click="emitSelectedOption(option)">
            <p class="option-label">{{ option.label }}</p>
            <div class="option-value">{{ option.text }}</div>
        </div>
    </section>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const { question } = defineProps(['question'])
const emit = defineEmits(['selectOption'])

function emitSelectedOption(option) {
    emit('selectOption', option)
}
</script>

<style scoped>
#question-container {
    margin-top: 30px;
}

.question-title {
    font-size: 30px;
    font-weight: bold;
    margin-bottom: 20px;
}

.option {
    display: flex;
    align-items: center;
    cursor: pointer;
}

.option-label {
    font-size: 20px;
    font-weight: bold;
    width: 50px;
    height: 50px;
    background-color: #a0ced9;
    display: flex;
    justify-content: center;
    align-items: center;
}

.option-value {
    font-size: 20px;
    font-weight: bold;
    padding: 0 20px;
    background-color: #e2e2e2;
    height: 50px;
    width: 100%;
    display: flex;
    align-items: center;
}
</style>