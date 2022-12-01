<template lang="html">

  <section class="src-components-navigator">
    <Header :colorDisplay="colorDisplay" :headerStyle="headerStyle"/>
    <br>
    <div id="navigator">
		<button @click="newGame()"> {{messageDisplay}}</button>
		<span id="message">{{messageDisplay2}}</span>
		<button @click="easy()" :class="[{ 'selected': !isHard}]">easy</button>
		<button @click="hard()" :class="[{ 'selected': isHard}]"> hard</button>

    <Container :colors = "colors" 
    :colorDisplay="colorDisplay" 
    @win="winGame()"
    @notWin ="tryAgain($event)"
    />

	</div>
  </section>

</template>

<script lang="js">
import Header from './Header.vue'
import Container from './Container.vue'
  export default  {
    name: 'src-components-navigator',
    components:{
      Header,
      Container
    },
    props: [],
    mounted () {
     this.newGame()
    
    },
    data () {
      return {
      restart:false,
      colorCount : 6,
      isHard : true,
      colors : [],
      colorDisplay:"" ,
      messageDisplay2 :"",
      messageDisplay:"",
      isDisplay:true,
      headerStyle : "",

      }
    },
    methods: {
      easy(){
      if (this.isHard) {
      this.isHard = false   
      this.colorCount = 3;
      this.newGame()
       }
     },
      hard(){
        if (!this.isHard) {
          this.isHard = true
          this.colorCount = 6;
          this.newGame()
       }
      },
      createColors(){
        this.colors = []
        for(var i = 0; i < this.colorCount; i++){
        this.colors.push(this.createRandomStringColor())
        }  
      },
      createRandomStringColor(){
      return "rgb(" + this.randomInt() + ", " + this.randomInt() + ", " + this.randomInt() + ")" 
      },
      newGame(){
        this.headerStyle = "steelblue"
        this.messageDisplay = "new Colors !"
        this.messageDisplay2 = ""
        this.createColors()
        this.PickColor()
      },
      randomInt(){
        return Math.floor(Math.random() * 256);
      },
      PickColor(){
        this.colorDisplay= this.colors[Math.floor(Math.random() * this.colorCount )]
        },   
      winGame(){
        this.messageDisplay = 'play again !'
        this.messageDisplay2 = 'You Picked Right!'
        this.setAllCollors()   
        this.headerStyle = this.colorDisplay    
      },
      setAllCollors(){
        for(var i = 0 ; i< this.colorCount; i++){
          this.colors[i] = this.colorDisplay
        }
      },
      tryAgain(index){
      this.messageDisplay2 = 'Try Again!'
      this.colors[index] = '#232323'
      },
    },
     computed: {

     }
  }



</script>

<style scoped lang="css">
#navigator {
  background: #ffffff;
  height: 30px;
  text-align: center;
  margin: 0;
  margin-top: -30px;
}
.selected {
  background-color: steelblue;
  color: white;
}
button {
  border: none;
  background-color: white;
  font-family: "Montserrat", "Avenir";
  text-transform: uppercase;
  height: 100%;
  font-weight: 700;
  letter-spacing: 1px;
  color: steelblue;
  transition: all 0.3s;
  outline: none;
}
button:hover {
  color: white;
  background-color: steelblue;
}
#message {
	display: inline-block;
	width: 20%;
}

</style>
