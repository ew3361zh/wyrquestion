<template>
<div id="app">

<h1>Philosophical Questions of Our Time</h1>

<!-- use v-for to run through the multiple wyr Qs in the questions array in data -->
<!-- key is the question and each element in the questions array is v-bound based on the key -->
<would-you-rather-question
  v-for="question in questions"
  v-bind:key="question"
  v-bind:question="question.wyrQuestion"
  v-bind:answer1="question.wyrAnswer1"
  v-bind:answer2="question.wyrAnswer2"
  v-on:answer-changed="answerChanged"
></would-you-rather-question> 
<!-- div element to hold the resulting user choices for the wyr questions -->
<div>
    <h1>You would rather...</h1>
    <ul class="user-choices">
      <!-- v-for to cycle through the userSelectionMessage array in data which
      holds all of the "choice" strings based on user selections -->
      <li v-for="answer in userSelectionMessage"
      v-bind:key="answer"
      >{{answer}}</li>
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
      // not sure what the id is doing here but it was in Clara's 
      // example so I may try to revisit to see if 
      // it would be useful to the way I've got things set up
      questions: [
      {
        id: 0,
        wyrQuestion: '...have edible spaghetti hair that regrows every night or sweat (not sweet) maple syrup?',
        wyrAnswer1: 'Spaghetti hair',
        wyrAnswer2: 'Maple sweat',
      },
      {
        id: 1,
        wyrQuestion: '...be a reverse centaur or a reverse mermaid/merman?',
        wyrAnswer1: 'Reverse centaur',
        wyrAnswer2: 'Reverse mermaid/merman',
      },
      {
        id: 2,
        wyrQuestion: '...have to fart loudly every time you have a serious conversation or have to burp after every kiss?',
        wyrAnswer1: 'Farty conversation',
        wyrAnswer2: 'Burpy kiss',
      },
      

    ],
    // array of userSelectionMessages with specific array #s to collect messages
    // as user is making their selections
    userSelectionMessage: []
    }
    
  },
  methods: {
    answerChanged(choice) {
      // for (let answer in questions) {
        // possibly use for loop to loop through questions array and do what
        // the numerous if statements are doing below tbd
      // }

      // if statements broken up into pairs that takes the choice data sent 
      // from WYRQ that checks the choice against the answers in the App.vue
      // questions array of objects

      // if the choice matches the answer in the questions array, assign the custom
      // choice userselection message to the userSelectionMessages array so it can
      // eventually be used in the ul above
      if (choice == this.questions[0].wyrAnswer1) {
        this.userSelectionMessage[0] = `have ${choice}`
        // this.userSelectionMessage.push(`have ${choice}`)
      }
      if (choice == this.questions[0].wyrAnswer2) {
        this.userSelectionMessage[0] = `sweat ${choice}`
        // this.userSelectionMessage.push(`sweat ${choice}`)
      }
      if (choice == this.questions[1].wyrAnswer1) {
        this.userSelectionMessage[1] = `be a ${choice}`
        // this.userSelectionMessage.push(`be a ${choice}`)
      }
      if (choice == this.questions[1].wyrAnswer2) {
        this.userSelectionMessage[1] = `be a ${choice}`
        // this.userSelectionMessage.push(`be a ${choice}`)
      }
      if (choice == this.questions[2].wyrAnswer1) {
        this.userSelectionMessage[2] = `have a ${choice}`
        // this.userSelectionMessage.push(`have a ${choice}`)
      }
      if (choice == this.questions[2].wyrAnswer2) {
        this.userSelectionMessage[2] = `have a ${choice}`
        // this.userSelectionMessage.push(`have a ${choice}`)
      }
      
    }
  }
}
</script>

<style>

body {
  background: greenyellow;
}

.user-choices {
  text-align: left;
  font-size: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: orange;
}
</style>
