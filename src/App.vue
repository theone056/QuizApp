<script setup>
import { reactive } from 'vue';
import Question from './components/Question.vue';
import Result from './components/Result.vue';

const data = reactive({
    questionAnswered: 0,
    totalCorrect: 0,
    questions: [
        {
            q: 'What is 2 + 2?', 
            answers: [
                {
                    text: '4',
                    is_correct: true
                },
                {
                    text: '3',
                    is_correct: false 
                },
                {
                    text: 'Fish',
                    is_correct: false 
                },
                {
                    text: '5',
                    is_correct: false 
                }
            ] 
        },
        { 
            q: 'How many letters are in the word "Banana"?', 
            answers: [
                {
                    text: '5',
                    is_correct: false
                },
                {
                    text: '7',
                    is_correct: false 
                },
                {
                    text: '6',
                    is_correct: true 
                },
                {
                    text: '12',
                    is_correct: false 
                }
            ] 
        },
        { 
            q: 'Find the missing letter: C_ke', 
            answers: [
                {
                    text: 'e',
                    is_correct: false
                },
                {
                    text: 'a',
                    is_correct: true 
                },
                {
                    text: 'i',
                    is_correct: false 
                }
            ] 
        },
    ],
    results: [
        {
            min: 0,
            max: 2,
            title: "Try again!",
            desc: "Do a little more studying and you may succeed!"
        },
        {
            min: 3,
            max: 3,
            title: "Wow, you're a genius!",
            desc: "Studying has definitely paid off for you!"
        }
    ]
})

const questionAnswered = (is_correct) => {
  if(is_correct){
    data.totalCorrect++;
  }

  data.questionAnswered++;
}

const resetQuestion = () => {
  data.questionAnswered = 0;
  data.totalCorrect = 0;
}
</script>

<template>
<div class="ctr">
   <Question v-if="data.questionAnswered < data.questions.length" 
                  :questions="data.questions" 
                  :questionAnswered="data.questionAnswered"
                  @question-answered="questionAnswered"/>
   <Result v-else :results="data.results" :totalCorrect="data.totalCorrect"/>
   
    <button type="button" class="reset-btn" @click="resetQuestion">Reset</button>
</div>
</template>

<style scoped>

</style>
