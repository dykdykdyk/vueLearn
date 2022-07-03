<template>
  <div class="todo-footer" >

    <button @click="clearAll">自定义事件测试</button>
    <button @click="unbind">解绑自定义事件</button>
  </div>
</template>

<script>
export default {
  name: 'Test',
  props:['todos'],
  data(){
    return{
    }
  },
  computed:{

  },
  methods:{
    clearAll(){
       this.$emit('dyk','dyk666',666,888,999);
       this.$emit('demo');
    },
    unbind(){
      this.$off(['dyk','demo']);// 解绑一个自定义事件
      this.off(); //全部解绑
    }
  },
}
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}
.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}
.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}
.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>
