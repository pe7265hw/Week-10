<script setup>
//import child file
import WouldYouRather from './components/WouldYouRather.vue'

//imports ref object from vue
import {ref} from 'vue'

//define variables
const wyrQuestion = ref('Would you rather have homemade pizza or homemade pasta?')
const wyrAnswer1 = ref('Homemade pizza')
const wyrAnswer2 = ref('Homemade pasta')

//user input
const userSelection = ref('')

//process user input for display
function updateUserSelection(userChoice){
    userSelection.value = `I see, you would rather have ${userChoice}.`
}

</script>

<template>
<div id="app-components">

<h1>Would You Rather?</h1>
<!--binds information in parent to what is expect to be recieved in child-->
    <WouldYouRather 
    v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-selected="updateUserSelection"></WouldYouRather>

    <p>{{ userSelection }}</p>
</div>
</template>


<!--css styling-->
<style scoped>
p{
    font-family: Arial, Helvetica, sans-serif;
}
#app-components{
    /*font-size: 3em;*/
    background-color: aqua;
    padding: 40px;
}
</style>
