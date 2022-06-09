<template>
  <div class="main">
    
    <h1 class="title">Gra Kamień Papier Nożyce</h1>

    <div class="container">
    <div class="choiceBox">
    <h2 class="title-h2">Wybierz element</h2>
      <div class="blocks">
        <div class="pick" @click="getResults('rock')">
          <i class="icon fa-solid fa-hand-back-fist"></i>
          <h1 class="pick-title-icon">Kamień</h1>
        </div>
          
        <div class="pick" @click="getResults('paper')">
          <i class="icon fa-solid fa-hand"></i>
          <h1 class="pick-title-icon">Papier</h1>
        </div>

        <div class="pick" @click="getResults('scissors')">
          <i class="icon fa-solid fa-hand-scissors"></i>
          <h1 class="pick-title-icon">Nożyce</h1>
        </div>
      </div>
      </div>
    

    
      <div class="compBox">
      <h2 class="title-h2">Komputer wybrał</h2>
      <div class="blocks">
          <div class="pick">
            <div class="comp">
              <i class="icon fa-solid fa-computer"></i>
              <h1 class="pick-title">{{compChoice}}</h1>
            </div>
          </div>
      </div>

      <div class="scoreBoard">
        <h2 class="title-h2">Wynik:</h2>
        <h2 class="title-h2">{{resultDisplay}}</h2>
        <h1 class="title">{{me}} : {{draw}} : {{comp}}</h1>
      </div>
      
      <div class="reset">
        <div class="blocks">
            <div class="pick" @click="resetScore">
              <h1 class="pick-title">Wyzeruj wynik</h1>
            </div>
        </div>
      </div>
      </div>
      </div>

    </div>

</template>

<script>


export default {
  name: 'App',

  data () {
    return {
      computerChoice: '',
      resultDisplay: 'Powodzenia !',
      me: 0,
      comp: 0,
      draw: 0
    }
  },
  methods: {
    
    getResults (userChoice) {

      const choices = ['rock', 'paper', 'scissors'];
      const computerChoice = Math.floor(Math.random() * choices.length);

      switch (choices[computerChoice]) {
        case 'rock' : 
          this.compChoice = "Kamień"
          break;
        case 'paper' : 
          this.compChoice = "Papier"
          break;
        case 'scissors' : 
          this.compChoice = "Nożyce"
          break;

      }

      switch (userChoice + choices[computerChoice]) {
        case 'scissorspaper':
        case 'rockscissors':
        case 'paperrock':
          this.resultDisplay = "Wygrałeś !"
          this.me++
          break;
        case 'paperscissors':
        case 'scissorsrock':
        case 'rockpaper':
          this.resultDisplay = "Przegrałeś"
          this.comp++
          break;
        case 'scissorsscissors':
        case 'rockrock':
        case 'paperpaper':
          this.resultDisplay = "Remis"
          this.draw++
          break;
      }
    },

    resetScore () {
      this.me = 0;
      this.comp = 0;
      this.draw = 0;
      this.resultDisplay = "Powodzenia !"
      this.compChoice = ""
    }
  }
}

</script>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Lobster&display=swap');

* {
  font-family: 'Lobster', cursive;

  margin: 0;
	padding: 0;
	box-sizing: border-box;
}

.main {
  display: flexbox;
  padding: 1rem;
  min-height: 100vh;
  justify-content: center;

  background-image: linear-gradient(to right top, 
  #6b70d1, #ac6dc1, #d371ab, 
  #e77e96, #ed9288, #ef9684, 
  #f09a80, #f19e7c, #f78f7b, 
  #fc7f7f, #fd6f88, #fb5f96
  );

  transition: 0.4s;
}

.container {
  display: flex;
  justify-content: center;
  height: 690px;
  flex-flow: row wrap;

  .compBox {
    flex: 0 0 0;
  }
}

.scoreBoard {
  margin: 3.3rem 0;
}

.title {
  text-align: center;
  font-size: 3rem;
  margin: 1rem;

  color: #FFF;
  text-shadow: 4px 4px 10px rgba(66, 68, 90, 1);
}

.title-h2 {
  text-align: center;
  font-size: 2rem;
  margin: 1rem;

  color: #FFF;
  text-shadow: 4px 4px 10px rgba(66, 68, 90, 1);
  transition: 0.4s;
}

.blocks {
  display: flexbox;
  transition: 0.4s;

  .pick {
    padding: 2rem 3rem;
    margin: 1rem 2rem;
    text-align: center;
    cursor: pointer;
    transition: 0.4s;

    color: #FFF;
    text-shadow: 4px 4px 10px rgba(66, 68, 90, 1);

    border-style: solid;
    border-color: #000 ;
    border-radius: 2rem;
    box-shadow: 1rem 1rem 2rem rgba(0, 0, 0, 0.5);

    background-image: linear-gradient(to left bottom, 
    #6b70d1, #ac6dc1, #d371ab, 
    #e77e96, #ed9288, #ef9684, 
    #f09a80, #f19e7c, #f78f7b, 
    #fc7f7f, #fd6f88, #fb5f96
    );

      .icon {
        font-size: 4rem;
      }

      .pick-title-icon {
        margin-top: 1rem;
      }
      
      .comp {
        min-height: 104px;
        min-width: 97px;
      }
  }

  .pick:hover {
    box-shadow: 1.5rem 1.5rem 2rem rgba(0, 0, 0, 0.8);

    background-image: linear-gradient(to right top, 
    #6b70d1, #ac6dc1, #d371ab, 
    #e77e96, #ed9288, #ef9684, 
    #f09a80, #f19e7c, #f78f7b, 
    #fc7f7f, #fd6f88, #fb5f96
  );

  }

  
}

</style>
