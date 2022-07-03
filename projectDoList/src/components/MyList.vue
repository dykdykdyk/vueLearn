<template>
  <ul class="todo-main">
    <MyItem v-for="item in todos" :key="item.id" :todo="item" :checkTodo="checkTodo"
    :deleteTodo="deleteTodo"/>
<!--    <button @click="test1">6666</button>-->
<!--    {{}}-->
  </ul>
</template>

<script>
import MyItem  from './MyItem'
export default {
  name: "MyList",
  components:{MyItem},
  props:['todos','checkTodo','test','deleteTodo'],  //接收APP传来的数据
  data(){
    return{
       "t1":""
    }
  },
  methods:{
    test1(){
     console.log("test",this.test);
     console.log("todos",this.todos);
    }
  }
}
</script>

<style scoped>
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}
.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>
