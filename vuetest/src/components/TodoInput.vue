<template>
	<div class="todo-input">
		<input type="text" v-model="text" @keyup.enter="addTodo"/>
		<button class="btn btn-primary" @click="addTodo">Submit</button>
	</div>
</template>

<script>
export default {
  name:'todo-input',
  data(){
  	return{
  		text:""
  	}
  },
  methods:{
  	addTodo(){
  		this.$emit('todo:add',this.text);
  		this.text = '';
  	}
  }
}
</script>

<style>
  .todo-input-wrapper{
  	margin-bottom: 20px;
  }
  .btn{
  	outline: none;
  	border-width: 2px;
  	border-radius: 3px;
  	border-style: solid;
  	padding: 8px;
  }
  .btn-primary{
  	color:rgba(73,204,249,1.0);
  	border-color: rgba(73,204,249,1.0);
  	background-color: transparent;
  }
  input{
  	width: 80%;
  	border-top: 2px solid rgb(73,204,249,1.0);
  	border-bottom: 2px solid rgb(73,204,249,1.0);
  	margin-right: 10px;
  	padding: 5px;
  	line-height: 17px;
  }
  input:focus{
  	border-top: 2px solid rgb(73,204,249,1.0);
  	border-bottom: 2px solid rgb(73,204,249,1.0);
  }
</style>