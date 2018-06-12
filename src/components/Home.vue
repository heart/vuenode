<template>
	<div v-bind:style="bgcolor" >
		<p>HOME</p>
		  <div v-for="(item, index) in wordList">
		    <div>{{item}}</div>
		  </div>
		<button v-on:click="onClick" >CLICK</button>
	</div>

</template>

<script>
import axios from 'axios'

export default {
  name: 'Home',
  data () {
    return {
      bgcolor: 'background-color:#FF0000',
      wordList:[]
    }
  },
  methods:{
  	onClick(){
  		this.bgcolor = 'background-color:#00FF00';
  	}
  },
  created() {
    var api_url = "http://localhost:8081/movies"
    var _this = this;
    axios
      .get(api_url)
      .then(function(response){
      	_this.wordList = response.data.words;
      })
  }
}
</script>

<style scoped>
</style>