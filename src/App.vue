<template>
<div id="app">

<h1>Would you rather...</h1>

<would-you-rather-question
  v-for="question in questions"
  v-bind:key="question"
  v-bind:question="question.wyrQuestion"
  v-bind:answer1="question.wyrAnswer1"
  v-bind:answer2="question.wyrAnswer2"
  v-on:answer-changed="answerChanged"
></would-you-rather-question> 
<div id="user-choices">
    <h1>You would rather...</h1>
    <ul>
      <li v-for="question in questions"
      v-bind:key="question"
      v-bind:userSelectionMessage="question.userSelectionMessage"
      
      >{{userSelectionMessage}}</li>
    </ul>
    
</div>

  </div>  
</template>

<script>
import WouldYouRatherQuestion from './components/WouldYouRatherQuestion.vue'

export default {
  name: 'App',
  components: {
    WouldYouRatherQuestion
  },
  data() {
    return {
      questions: [
      {
        id: 0,
        wyrQuestion: 'Would you rather have edible spaghetti hair that regrows every night or sweat (not sweet) maple syrup?',
        wyrAnswer1: 'Spaghetti hair',
        wyrAnswer2: 'Maple sweat',
        userSelectionMessage: ''
      },
      {
        id: 1,
        wyrQuestion: 'Would you rather be a reverse centaur or a reverse mermaid/merman?',
        wyrAnswer1: 'Reverse centaur',
        wyrAnswer2: 'Reverse mermaid/merman',
        userSelectionMessage: ''
      },
      {
        id: 2,
        wyrQuestion: 'Would you rather have to fart loudly every time you have a serious conversation or have to burp after every kiss?',
        wyrAnswer1: 'Farty conversation',
        wyrAnswer2: 'Burpy kiss',
        userSelectionMessage: ''
      }

    ]}
  },
  methods: {
    answerChanged(choice) {
      this.userSelectionMessage = `Gross! You would rather ${choice}`
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
