<template>
	<div class="todo-footer">
		<label>
      <input type="checkbox" v-model="checkAll"/>  
    </label>
    <span>
      <span>已选{{completeSize}}</span>/全部{{todos.length}}
    </span>
    <button v-show="completeSize>0" @click="clearAllComplete">清除已完成任务</button>
	</div>
</template>

<script>
export default {
  name:'Footer',
  props:{
    todos:Array,
    selectAll:Function,
    clearAllComplete:Function
  },
  computed:{
    completeSize(){
      return this.todos.reduce((pre,todo) => pre+(todo.completed ? 1:0),0)
    },
    checkAll:{
      get(){
        return this.todos.length===this.completeSize
      },
      set(value){ //value是checkAll的最新值
        this.selectAll(value)
      }
    }
  }
  
}
</script>

<style scoped>
  .todo-footer{
    height: 50px;
    line-height: 50px;
    padding-left: 6px;
    margin-top: 5px;
    border:1px solid rgba(192,192,192,0.5);
  }
  .todo-footer label{
    display: inline-block;
    margin-right: 20px;
    width: 50px;
  }
  .todo-footer button{
    float: right;
    margin-top: 5px;
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