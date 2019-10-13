<template>
  <div class="todoWrapper">
    <input type="checkbox" name="check" style="width: 50px;" v-model="todo.completed">
  	<button class="removeTodo" @click="removeTodo">remove</button>{{todo.text}}
  </div>
</template>

<script>
export default {
  name:'todo-item',
  data(){
    return{
      checked:[]
    }
  },
  props:["todo","index"],
  methods:{
  	removeTodo(){
  		this.$emit('todo:remove',this.index);
  	}
  }
}
</script>

<style>
  .todoWrapper{
  	border-bottom: 1px solid #efefef;
  	text-align: left;
  	margin-bottom: 10px;
  	margin-top: 20px;
  }
  .removeTodo{
  	margin-right: 20px;
  	margin-bottom: 10px;
  	outline: none;
  	border-width: 2px;
  	border-radius: 3px;
  	border-style: solid;
  	padding: 8px;
  	color: rgba(203,20,32,0.4);
  	border-color: rgba(203,20,32,0.4);
  	background-color: transparent;
  }
</style>
