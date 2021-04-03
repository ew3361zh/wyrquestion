<template>
<div id="app">

<h1>Would you rather...</h1>
<!-- also would work as WouldYouRather/WouldYouRather -->
<would-you-rather 
v-bind:question="wyrQuestion"
v-bind:answer1="wyrAnswer1"
v-bind:answer2="wyrAnswer2"
v-on:answer-changed="answerChanged"
></would-you-rather> 
<p> {{ userSelectionMessage }}</p>

  </div>  
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      wyrQuestion: 'Would you rather have edible spaghetti hair that regrows every night or sweat (not sweet) maple syrup?',
      wyrAnswer1: 'Spaghetti hair',
      wyrAnswer2: 'Maple sweat',
      userSelectionMessage: ''
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectionMessage = `Gross! You chose ${choice}`
    }
  }
}
</script>

<style>

body {
  background: yellow;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: tomato;
}
</style>
