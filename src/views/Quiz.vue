<template>
    <QuizHeader :questionPage="questionPage" :barPercentage="barPercentage" />
    <QuizContent v-if="!showResult" :question="quiz.questions[currentQuestionIndex]" @selectOption="onSelectOption" />
    <QuizResult v-else  :quizLength="quiz.questions.length" :numberOfCorrectAnswers="numberOfCorrectAnswer" />
</template>

<script setup>
import quizes from "@/data/quizes.json"
import { ref, computed } from "vue";
import QuizHeader from "@/components/QuizHeader.vue"
import QuizResult from "@/components/QuizResult.vue"
import QuizContent from "@/components/QuizContent.vue"
import { useRoute } from "vue-router";

const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = quizes.find((q) => q.id === quizId)

const currentQuestionIndex = ref(0)
const numberOfCorrectAnswer = ref(0)
const showResult = ref(false)
const questionPage = computed(() => {
    return `${currentQuestionIndex.value + 1} / ${quiz.questions.length}`
})
const barPercentage = computed(() => {
    return `${((currentQuestionIndex.value + 1) / quiz.questions.length) * 100}%`
})

function onSelectOption(option) {
    if (option.correct) {
        numberOfCorrectAnswer.value++
    }
    if (currentQuestionIndex.value == quiz.questions.length - 1) {
        showResult.value = true
        return;
    }
    currentQuestionIndex.value++
}
</script>

<style scoped></style>