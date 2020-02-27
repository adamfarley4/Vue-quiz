<template>
  <div id="app">
    <div class="offset-3 col-6">
      <div class="card">
        <div class="card-body">
          <p class="question title">Question {{ questionIndex + 1 }}</p>
          <br>
          <h4 class="questionname">{{ currentQuestion.question }}</h4>
          <hr>
          <button
            style="background-color:white"
            type="button"
            class="btn btn-primary btn-lg btn-block text-left"
            v-for="(answer, index) in currentQuestion.answers"
            v-bind:key="index"
            @click="addAnswer(index);"
          >{{ index }}-{{ answer }}</button>
          <hr>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function() {
    return {
      answers: [],
      questionIndex: 0,
      questions: [
        {
          question: "Are you a developer",
          answers: ["Yes", "No"],
          answer: 0
        },
        {
          question: "How would you rate vue",
          answers: ["OK", "GOOD", "GREAT"],
          answer: 2
        },
        {
          question: "who was the second president of the usa",
          answers: ["george washington", "Abe Lincoln", "John Adams"],
          answer: 2
        },
        {
          question: "where is the effiel tower located?",
          answers: ["Paris", "London", "Toronto"],
          answer: 0
        },
        {
          question: "how many letters are in the english alphabet?",
          answers: ["24", "25", "26", "27"],
          answer: 2
        }
      ]
    };
  },
  methods: {
    addAnswer: function(index) {
      this.answers.push(index);

      if (this.questions.length == this.answers.length) {
        var correctCount = 0;

        for (var i in this.answers) {
          var answer = this.answers[i];

          if (answer == this.questions[i].answer) {
            correctCount++;
          }
        }
        alert("amount you got correct " + correctCount);
        for (let i = 0; i < 5; i++) {
          alert(
            "Question " +
              (i + 1) +
              " " +
              this.questions[i].question +
              " The answer is " +
              this.questions[i].answer
          );
        }
      } else {
        this.questionIndex++;
      }
    }
  },
  computed: {
    currentQuestion: function() {
      return this.questions[this.questionIndex];
    }
  }
};
</script>

<style>
#app {
  background-color: rgb(33, 170, 170);
  font-family: "Times New Roman", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: block;
  -moz-osx-font-smoothing: Black;
  text-align: center;
  color: black;
  margin-top: 120px;
}
.questionname {
  background-color: white;
}
</style>