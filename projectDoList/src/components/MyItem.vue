<template>
  <li>
    <label>
      <input type="checkbox" :checked="todo.done" @click="handleChange(todo.id)"
      />
      <span>{{ todo.title }}</span>
    </label>
    <button class="btn btn-danger" @click="deleteHandle(todo.id)">删除</button>
  </li>
</template>

<script>
export default {
  name: "MyItem",
  //声明接收todo对象
  props: ['todo', 'checkTodo','deleteTodo'],
  mounted() {
    // console.log(this.qwe)
  },
  methods: {
    handleChange(id) {
      console.log("id", id);
      //通知将App组件对应的TODO对象的done值取反
      this.checkTodo(id)
    },
    deleteHandle(id){
      this.deleteTodo(id);
    }
  },
}
</script>

<style scoped>
li {
  list-style: none;
  height: 50px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}

/*悬浮效果 鼠标滑到当前的item时候，会出现的背景色*/
li:hover {
  background-color: #ddd;
}

li:hover button {
  display: block;
}
</style>
