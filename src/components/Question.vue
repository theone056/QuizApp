<template>
    <div class="questions-ctr">
        <div class="progress">
            <div class="bar" 
                 :style="{width: `${(questionAnswered / props.questions.length) * 100}%`}"></div>
            <div class="status">{{ props.questionAnswered }} out of {{ props.questions.length }} questions answered</div>
        </div>
        <div class="single-question" v-for="(question,qi) in props.questions" 
                                     :key="question.q"
                                     v-show="props.questionAnswered === qi  ">
            <div class="question">{{ question.q }}</div>
            <div class="answers">
                <div class="answer" v-for="answer in question.answers" 
                                    :key="answer.text"
                                    @click.prevent="SelectAnswer(answer.is_correct)">
                    {{ answer.text }}
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    questions:{
        type:Array
    },
    questionAnswered:{
        type: Number
    }
})

const emit = defineEmits(['question-answered']);

const SelectAnswer = (is_correct) => {
    emit('question-answered', is_correct)
}
</script>

<style lang="scss" scoped>

</style>