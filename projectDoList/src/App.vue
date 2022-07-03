<template>
  <div id="app">
    <div id="root">
      <div class="todo-container">
        <div class="todo-wrap">
<!--          把receive传给MyHeader-->
          <MyHeader  :receive="receive"  />
<!--          <MyList/>-->
          <!-- 把数据传给list -->
          <MyList :todos="todos" :checkTodo="checkTodo" :test="666" :deleteTodo="deleteTodo"/>
          <MyFooter  :todos="todos"
                     :isAllTodo="isAllTodo"
                     :clearAllTodo="clearAllTodo" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
   import  MyHeader from './components/MyHeader'
   import  MyFooter from './components/MyFooter'
   import  MyItem from './components/MyItem'
   import  MyList from './components/MyList'
   import Test from "./components/Test";
export default {
  name: 'app',
  components:{MyList, Test, MyHeader,MyFooter},
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      todos:[
        {id:'0001',title:'吃饭',done:true},
        {id:'0002',title:'开车',done:false},
        {id:'0003',title:'开飞机',done:true}
      ]
    }
  },
  methods:{
    receive(x){
      console.log("我是App组件,我收到了数据:",x);
      this.todos.unshift(x);
    },
    //勾选或者取消勾选
    checkTodo(id){
      this.todos.forEach((item)=>{
        if(item.id === id){
          item.done=!item.done;
        }
      })
    },
    test(name){
      console.log("name",name);
    },
    deleteTodo(id){
      this.todos= this.todos.filter(item=>{
       return   item.id !==id
      })
    },
    isAllTodo(value){
      this.todos.forEach(item=>{
        item.done=value;
      })
    },
    clearAllTodo(){
      this.todos =this.todos.filter(item=>{
        return !item.done
      })
    },
    // getName(name,x,y,z){
    //后面的所有参数全部都装进a这个数组中了
    getName(name,...a){
      console.log("自定义事件收到了数据",name,a);
    },
    m1(name,...a){
      console.log("自定义事件收到了数据",name,a);
    }
  },
  mounted() {
    setTimeout(()=>{
      //函数体
      // this.$refs.test.$on('dyk',this.getName);
    },3000)
    // this.$refs.test.$on('dyk',this.getName);

    //设置只触发一次自定义事件
    // this.$refs.test.$once('dyk',this.getName);
  }
}
</script>

<style>
/*base*/
body {
  background: #fff;
}
.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2),
  0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}
.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}
.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}
.btn:focus {
  outline: none;
}
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
