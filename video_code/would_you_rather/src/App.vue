<script setup>
import WouldYouRather from './components/WouldYouRather.vue'

import {ref} from 'vue'

const wyrQuestion = ref('Would you rather have homemade pizza or homemade pasta?')
const wyrAnswer1 = ref('Homemade pizza')
const wyrAnswer2 = ref('Homemade pasta')

const userSelection = ref('')

function updateUserSelection(userChoice){
    userSelection.value = `I see, you would rather have ${userChoice}.`
}

</script>

<template>
<div id="app-components">

<h1>Would You Rather?</h1>

    <WouldYouRather 
    v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-selected="updateUserSelection"></WouldYouRather>

    <p>{{ userSelection }}</p>
</div>
</template>



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
