<template>
  <div class="wyr">
    <h2>Would you rather...</h2>
    <h3>{{question}}</h3>
    <input type="radio" v-model="choice" 
    v-bind:value="answer1"
    v-on:change="choiceMade">
    <label> {{answer1}} </label>
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
    choiceMade(choice) {
      this.$emit('answer-changed', choice)
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
  border: 5px hotpink double;
  background-color: lightskyblue;
  margin: 15px
}
</style>
