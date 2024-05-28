<template>
    <header>
        <h1 id="title">QuizVue</h1>
        <input type="text" id="search-input" v-model.trim="search">
    </header>
    <section id="quiz-container">
        <QuizCard v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
    </section>
</template>

<script setup>
import { ref, watch } from "vue";
import srcQuiz from "../data/quizes.json";
import QuizCard from "../components/QuizCard.vue";

const search = ref("")
const quizes = ref(srcQuiz);

watch(search, () => {
    quizes.value = srcQuiz.filter((quiz) => {
        return quiz.title.toLowerCase().includes(search.value.toLowerCase())
    })
})
</script>

<style scoped>
header {
    margin-top: 30px;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
}

#title {
    font-weight: bold;
    margin-right: 30px;
}

#search-input {
    border: none;
    background-color: #c9c9c9;
    padding: 10px;
    border-radius: 5px;
}

#quiz-container {
    display: flex;
    flex-wrap: wrap;
    margin-top: 20px;
}
</style>