<template>
    <div class="card" @click="goToQuiz">
        <img :src="quiz.img" :alt="quiz.title" loading="lazy">
        <div class="card-body">
            <h2 class="card-title">{{ quiz.title }}</h2>
            <p>{{ quiz.questions.length }} Questions</p>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue'
import { useRouter } from 'vue-router';

const router = useRouter();
const props = defineProps({
    quiz: Object
})

function goToQuiz() {
    router.push({ name: 'quiz', params: { id: props.quiz.id } })
}
</script>

<style scoped>
.card {
    width: 270px;
    margin-right: 30px;
    margin-bottom: 30px;
    border-radius: 5px;
    overflow: hidden;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
}

.card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    margin: 0;
}

.card-body {
    padding: 0 15px;
}

.card-body h2 {
    font-weight: bold;
}
</style>