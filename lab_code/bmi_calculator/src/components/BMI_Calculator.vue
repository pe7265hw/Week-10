<script setup>
//imports objects to be used by Vue
import { ref, watch } from 'vue'

//defines props to be recieved from parent
defineProps({
  mainStatement: String,
  heightQuestion: String,
  weightQuestion: String,

})

//variables to be used
const userWeight = ref('')
const userHeight = ref('')
const errors = ref([])
const bMI = ref('')

//function which checks for errors and determines users BMI
const determineUserBMI =() => {
  errors.value= []
  if (userHeight.value.length == 0){
    errors.value.push('You must enter a height in meters.')
  }
  if(userWeight.value.length == 0){
    errors.value.push('You must enter a weight in Kilograms')
  }
  if (errors.value.length > 0){
    alert(errors.value.join('\n'))
  }else{
    bMI.value = Math.round(userWeight.value / (userHeight.value * userHeight.value))
  }

//defines what will be emitted to parent
}
const emit = defineEmits([
  'stats-entered'
])

//watches for value to be given to variable that will be emitted to parent
watch(bMI, () => {
  emit('stats-entered', bMI.value)
} )

</script>

<template>

  <!--HTML to display text, set up input and buttons as well as funciton that will be called when button is clicked-->
  <h2>{{mainStatement}}</h2>
  <div>
    <label for="weightInput">{{ weightQuestion }}</label>
    <input v-model="userWeight" id="weightInput">
    <br>
    <label for="heightInput">{{ heightQuestion }}</label>
    <input v-model="userHeight" id="heightInput">
    <br>
    <button v-on:click="determineUserBMI()">Calculate</button>

  </div>

</template>

<style scoped>

</style>
