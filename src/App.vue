<script>

export default {
  data() {
    return {
      word: true,
      page: false,


      ///////////////////////
    //   questions: [
    //   {
    //     question: "Que signifie PHP?",
    //     choice1: "Personal Home Page Hypertext Preprocessor", 
    //     choice2: "Pretext Hypertext Processor", 
    //     choice3: "Preprocessor Home Page", 
    //     choice4: "Pretext Hypertext Processor",
    //     answer: 1
    //   },
    //   {
    //     question: "Les fichiers PHP ont l’extension …. ?",
    //     choice1: ".html", 
    //     choice2: ".xml", 
    //     choice3: ".php", 
    //     choice4: ".ph",
    //     answer: 3
    //   },
    //   {
    //     question: "Un script PHP devrait commencer par ___ ?",
    //     choice1: "<php", 
    //     choice2: "<?", 
    //     choice3: "<?php", 
    //     choice4: "php",
    //     answer: 3
    //   },
    //   {
    //     question: "Quelle version de PHP a introduit Try/catch Exception?",
    //     choice1: "PHP 4", 
    //     choice2: "PHP 5", 
    //     choice3: "PHP 5.3", 
    //     choice4: "PHP 7.2",
    //     answer: 2
    //   },
    //   {
    //     question: "Les espaces de noms ou « namespaces » sont disponibles depuis quelle version ?",
    //     choice1: "PHP 4", 
    //     choice2: "PHP 5", 
    //     choice3: "PHP 5.3", 
    //     choice4: "PHP 6",
    //     answer: 4
    //   }
    // ],
    // currentQuestion: null,
    // selectedAnswer: null,
    // correctAnswers: 0,


  //////////////////


    }
  },
  methods: {
    changeValue() {
      this.word = !this.word;
      this.page = !this.page;
    },

    // generateQuestion() {
    //   // Pick a random question that hasn't been asked yet
    //   const availableQuestions = this.questions.filter(q => q !== this.currentQuestion);
    //   this.currentQuestion = availableQuestions[Math.floor(Math.random() * availableQuestions.length)];
    //   this.selectedAnswer = null; // Reset the selected answer
    // },
    // checkAnswer() {
    //   if (this.selectedAnswer === this.currentQuestion.answer) {
    //     this.correctAnswers++;
    //   }
    //   this.generateQuestion(); // Generate the next question
    // }


  }
};










  </script>

<template>
<!-- flex items-center w-full flex-col -->
<section class="border border-gray-600 w-screen text-center p-0 m-0" v-if="word">
    <h1 class="textTitle">Bienvenue au quiz PHP</h1>
    <ul class="textInfo">
        <li>Dans ce quiz, vous obtiendrez votre résultat à la fin</li>
        <li>Vous ne pourrez pas ignorer la question ou revenir à la question à laquelle vous avez répondu</li>
        <li>vous pouvez terminer le test quand vous le souhaitez</li>
        <li>Si vous ne pouvez pas répondre avant 15 secondes, votre réponse est considérée comme fausse</li>
        <li>Les questions s'affichent dans un ordre aléatoire. Vous ferez de nouvelles découvertes à chaque fois!</li>
        <li>Si vous êtes prêt, cliquez sur start quiz</li>
    </ul>
    <button @click="changeValue" class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center">
  <span>start quiz</span>
</button>
</section>




<section class="pageQue1" v-if="page">



<div >
  <form>
    <div v-if="currentQuestion">
      <p>{{ currentQuestion.question }}</p>
      <label><input type="radio" v-model="selectedAnswer" :value="1">{{ currentQuestion.choice1 }}</label><br>
      <label><input type="radio" v-model="selectedAnswer" :value="2">{{ currentQuestion.choice2 }}</label><br>
      <label><input type="radio" v-model="selectedAnswer" :value="3">{{ currentQuestion.choice3 }}</label><br>
      <label><input type="radio" v-model="selectedAnswer" :value="4">{{ currentQuestion.choice4 }}</label><br>
      <button type="button" @click="checkAnswer">Submit</button>
    </div>
    <div v-else>
      <p>Congratulations! You have completed the quiz.</p>
    </div>
  </form>
  <button type="button" @click="generateQuestion" v-if="currentQuestion == null">Start Quiz</button>
  <button class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center" @click="changeValue" >exit Quiz</button>
<button class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center">next question</button>
<button class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center">show your Result</button>
</div>



</section>



</template>

<style scoped>

</style>
