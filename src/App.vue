<template>
  <div id="app">  
    <div>
    <Navigator/>
    </div>
     
  </div>
</template>

<script>
import Navigator from './components/Navigator.vue'

export default {
  name: 'App',
  components: {
    Navigator
  }
}
</script>

<style>
body {
	background: #232323 !important;
}
</style>
