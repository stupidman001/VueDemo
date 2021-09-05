<template>
  <div>
    <li>
      <label>
        <input type="checkbox" :checked="todo.done" @change="changeStatus(todo.id)"/>
        <span>{{todo.title}}</span>
      </label>
      <button class="btn btn-danger" style="display: none">删除</button>
    </li>
  </div>
</template>

<script>
export default {
  name: "MyItem",
  props:['todo','checkTodo'],
  created(){
    console.log(this.todo)
  },
  methods:{
    changeStatus(id){
      // 通知 App 组件将对应的 todo 对象的 done 值取反
      this.checkTodo(id)
    }
  }
};
</script>

<style scoped>
/*item*/
li {
  list-style: none;
  height: 36px;
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
</style>