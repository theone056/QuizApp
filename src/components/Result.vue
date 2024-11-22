<template>
    <div class="result">
        <div class="title">{{props.results[resultIndex].title}}</div>
        <div class="desc">
            {{ props.results[resultIndex].desc }}
        </div>
    </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    totalCorrect:{
        type:Number
    },
    results:{
        type:Array
    }
})

const resultIndex = computed(()=>{
    let index = 0;

    props.results.forEach((e,i)=>{
        if(e.min >= props.totalCorrect && e.max <= props.totalCorrect){
            index = 1
        }
    });

    return index;
})
</script>

<style lang="scss" scoped>

</style>