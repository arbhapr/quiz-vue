<template>
    <section class="results">
        <p>Score:</p>
        <h1>{{ numberOfCorrectAnswers }} / {{ quizLength }}</h1>
        <RouterLink to="/">Go Back</RouterLink>
    </section>
</template>

<script setup>
import { defineProps } from 'vue';
import { RouterLink } from 'vue-router';

const { quizLength, numberOfCorrectAnswers } = defineProps(['quizLength', 'numberOfCorrectAnswers'])
</script>

<style scoped>
.results {
    text-align: center;
    padding: 100px 0;
}

p {
    font-size: 25px;
}

h1 {
    font-size: 80px;
}
</style>