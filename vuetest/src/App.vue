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
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  data(){
    return{
      items:[1,3,4,6,2],
        i:-1,
        msg:'',
        show:true
    }
  },
  methods:{
        changeColor(index){
          this.i = index
        },
        sort(){
          this.items.sort(function(a,b){
            return a-b;
          })
            
          
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
</style>
