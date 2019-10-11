<template>
  <div id="app">
    <ul>
      <li v-for='(item,index) in items' :style='{width:"100px",height:"100px"}' class="yellow" :class='{red:i===index}'
      @click='changeColor(index)'>{{item}}</li>
    </ul>
    <button @click='sort'>排序</button>
    <input type="text" v-model='msg'>
    <button v-on:click = "show = !show">点我</button>
    <transition>
        <p style="border: 1px solid yellow;width: 50px;height: 30px;" v-if="show">你好呀</p>
    </transition>
    <div class="todo-wrapper">
      <app-header></app-header>
      <todo-input @todo:add="addTodo"></todo-input> 
      <todo-item v-for="todo in todos" :todo="todo" @todo:remove="removeTodo" :key='todo.id'></todo-item>
    </div>
  </div>
</template>

<script>

import AppHeader from './components/AppHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoItem from './components/TodoItem.vue';

export default {
  name: 'App',
  components:{
    AppHeader,
    TodoInput,
    TodoItem
  },
  data(){
    return{
      items:[1,3,4,6,2],
        i:-1,
        msg:'',
        show:true,
        todos:[
          {id:0,text:"eat"},
          {id:1,text:"play"},
          {id:2,text:"learn"}
        ],
        nextId:3
    };
  },
  methods:{
        changeColor(index){
          this.i = index
        },
        sort(){
          this.items.sort(function(a,b){
            return a-b;
          })
        },
        addTodo(text){
          this.todos.push({id:this.nextId,text:text});
          this.nextId++;
        },
        removeTodo(id){
          let todos = this.todos;
          this.todos = todos.filter((todo) => todo.id != id)
        }
      },
      watch:{
        msg:function(newValue,oldValue){
          console.log(newValue)
        }
      }
  
}
</script>

<style>
  .yellow{
      color:yellow;
    }
    .red{
      color: red;
    }
    .v-enter-active{

      animation:color 2s;
    }
    .v-leave-active{
      animation:color 1s;
    }
    @keyframes color{
      from{
        transform: scale(0);
        background-color: red
      }
      to{
        background-color: green;
         transform: scale(1);
      }
    }

    .todo-wrapper{
      margin: 20px auto;
      width: 500px;
      min-height: 600px;
      border: 3px solid green;
      padding: 20px;
    }
</style>
