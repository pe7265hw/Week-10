<script setup>
import { ref, watch } from 'vue'

defineProps({
  question: String,
  answer1: String,
  answer2: String
})

const emit = defineEmits([
  'answer-selected'
])

const choice = ref('')

//emits event to tell parent that user has made a choice
// function choiceMade(){
//   emit('answer-selected', choice.value)
// }

//if choice has changed, change value in choice
watch(choice, () =>{
  emit('answer-selected',choice.value)
})
</script>

<template>

<div id="wyr">

    <h2>Make your choice!</h2>

  <p>{{ question }}</p>
  <div>
    <input v-model="choice" v-bind:value="answer1" type="radio" id="answer-1">
    <label for="answer-1">{{ answer1 }}</label>
    
    <input v-model="choice" v-bind:value="answer2" type="radio" id="answer-2">
    <label for="answer-2">{{ answer2 }}</label>
  </div>
</div>
  
</template>

<style scoped>
#wyr{
  background-color: lightblue;
}

p{
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
}
</style>
