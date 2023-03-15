<script>

export default {
  data() {
    return {
      word: true,
      page: false,
      


      ///////////////////////
      questions: [
      {
        question: "Que signifie PHP?",
        choice1: "Personal Home Page Hypertext Preprocessor", 
        choice2: "Pretext Hypertext Processor", 
        choice3: "Preprocessor Home Page", 
        choice4: "Pretext Hypertext Processor",
        answer: 1
      },
      
     
     
      {
        question: "Les espaces de noms ou « namespaces » sont disponibles depuis quelle version ?",
        choice1: "PHP 4", 
        choice2: "PHP 5", 
        choice3: "PHP 5.3", 
        choice4: "PHP 6",
        answer: 4
      },
      {
        question: "qustion",
        choice1: "answer", 
        choice2: "false", 
        choice3: "false", 
        choice4: "false",
        answer: 1
      }
    ],
    // currentQuestion: null,
    selectedAnswer: null,
    correctAnswers: 0,
    conteur:0,
    btn:true,
  questionlist:true,
  showButton:false,
  progress: 0,


    }
  },
  computed:{
    initial(){
      return (1/this.questions.length)*100;
    }
  },
  created(){
    this.progress=this.initial
  },
  methods: {
    
    changeValue() {

    },

    generateQuestion() {
      this.word = !this.word;
      this.page = !this.page;
      // const availableQuestions = this.questions.filter(q => q !== this.currentQuestion);
      // this.currentQuestion = availableQuestions[Math.floor(Math.random() * availableQuestions.length)];
      // this.selectedAnswer = null; 
    },
    generateQuestion1() {
      const availableQuestions = this.questions.filter(q => q !== this.currentQuestion);
      this.currentQuestion = availableQuestions[Math.floor(Math.random() * availableQuestions.length)];
      this.selectedAnswer = null; 
      this.conteur++;
      this.progress += this.initial;
      console.log(this.conteur);
      // return this.conteur;
    },
    combinedmethod(){

      this.generateQuestion();
      this.generateQuestion1();

    },
    checkAnswer() {
      this.showButton = !this.showButton;
      if (this.selectedAnswer === this.currentQuestion.answer) {
        this.correctAnswers++;
        console.log(this.correctAnswers);
        
      }
      
      this.generateQuestion1(); // Generate the next question
    },

    showresult(){
      // this.result==true;
    // this.questionlist==null;
    if (this.selectedAnswer === this.currentQuestion.answer) {
        this.correctAnswers++;
        console.log(this.correctAnswers);
      }
    this.questionlist = !this.questionlist;
    this.btn = !this.btn;
    
    
    }
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
    <button @click="combinedmethod" v-if="currentQuestion == null" class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center">
  <span>start quiz</span>
</button>
</section>




<section class="pageQue1" v-if="page">



<div >
  <form>
    <div v-if="currentQuestion,questionlist" >
   
      <p>{{ currentQuestion.question }}</p>
      <label><input type="radio" @focus="showButton = true" v-model="selectedAnswer" :value="1">{{ currentQuestion.choice1 }}</label><br>
      <label><input type="radio" @focus="showButton = true" v-model="selectedAnswer" :value="2">{{ currentQuestion.choice2 }}</label><br>
      <label><input type="radio" @focus="showButton = true" v-model="selectedAnswer" :value="3">{{ currentQuestion.choice3 }}</label><br>
      <label><input type="radio" @focus="showButton = true" v-model="selectedAnswer" :value="4">{{ currentQuestion.choice4 }}</label><br>
      <!-- <div class="progress">
        <div class="progress-bar" role="progressbar"  :aria-valuenow="progress" aria-valuemin="0" aria-valuemax="100"></div>
      </div> -->

      
<div class="w-full bg-gray-200 rounded-full h-2.5 dark:bg-gray-700">
  <div class="bg-blue-600 h-2.5 rounded-full" :style="{width: progress + '%'}"></div>
</div>



    </div>
    <div v-else>
      <p>Congratulations! You have completed the quiz. with result {{ correctAnswers }}/{{questions.length}}</p>
    </div>
  </form>
  <button class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center" type="button" @click="generateQuestion" v-if="currentQuestion == null">Start Quiz</button>
  <button class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center" @click="changeValue" >exit Quiz</button>

<button v-if="conteur < questions.length-1" @click="checkAnswer" v-show="showButton" class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center">next question</button>

<button v-else-if="btn" @click="showresult"  class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center">show your Result</button>
</div>

</section>
</template>

<style scoped>

</style>
