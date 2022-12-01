<template>

  <section class="src-components-container">
      <div id="container">
        <div v-for="(square, index) in colors" :key="index">
        <div class="square"  @click="comparar(square,index)" :style="'backgroundColor:'+colors[index]"></div>
    </div>
    
	</div>

  <br>
  </section>

</template>

<script>

  export default  {
    name: 'src-components-container',
    props: ['colors','colorDisplay'],
    mounted () {
    },
    data () {
      return {
        colorsSquare:[],
      }
    },
    methods: {
     comparar(square,index){
      if(square == this.colorDisplay){
      console.log("gano")
      this.$emit('win')
      this.$forceUpdate()
      }else{
      console.log("siga intentando")
      this.$emit('notWin', index)
      this.$forceUpdate()
      }
     }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .square {
	width: 30%;
	background: blue;
	padding-bottom: 30%;
	float: left;
	margin: 1.66%;
	border-radius: 10%;
	transition: background 0.8s;
	-webkit-transition: background 0.8s;
	-moz-transition: background 0.8s;

}
#container {
	margin: 20px auto;
	max-width: 600px;
}


</style>
