<template>
<!-- wyr div displays the questions in 3 separate elements since there are three
of them in the App.vue data and App.vue v-for loops through the questions array -->
  <div class="wyr">
    <h2>Would you rather...</h2>
    <h3>{{question}}</h3>
    <!-- v-bind value of answer1 and answer2 for each question from the questions array from app.vue -->
    <input type="radio" v-model="choice" 
    v-bind:value="answer1"
    v-on:change="choiceMade">
    <label> {{answer1}} </label>
    <!-- v-model choice for radio buttons to make sure only one is selected and v-bind
    the value. Also using the v-on:change with the choiceMade method to send selection
    changes to app.vue for its use -->
    <input type="radio" v-model="choice" 
    v-bind:value="answer2" 
    v-on:change="choiceMade">
    <label> {{answer2}} </label>
  </div>
</template>

<script>
export default {
  name: 'WouldYouRatherQuestion',
  props: {
    id: Number,
    question: String,
    answer1: String,
    answer2: String
  },
  emits: ['answer-changed'], //added this line to emit the change selected to app.vue parent
  data () {
    return {
      choice: ''
    }
  },
  methods: {
    choiceMade() {
      // sending the choice made for each particular question back to app.vue for its use there
      this.$emit('answer-changed', this.choice)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

.wyr {
  border: 5px darkolivegreen dotted;
  background-color: honeydew;
  margin: 15px;
  padding:5px;
}
</style>
