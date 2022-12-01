<template >

  <section class="src-components-header">
    <div class="header" :style='" background : "+ headerStyle'>
      <h1>The Great <br>
			<span>{{colorDisplay}}</span>
			<br>
			Guessing Game</h1>
    </div>
    
  </section>

</template>

<script>

  export default  {
    name: 'src-components-header',
    props: ['colorDisplay','headerStyle'],
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .header {
	transition: all 0.3s;
	text-transform: uppercase;
	text-align: center;
	margin: 0;
	color: white;
	
}
</style>
