<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <MyHeader :receive="receive"/>
      <MyList :todos="todos" :checkTodo="checkTodo" :deleteItem="deleteItem"/>
      <MyFooter :todos="todos" />
    </div>
  </div>
</template>

<script>
import MyHeader from "@/components/MyHeader.vue";
import MyFooter from "@/components/MyFooter.vue";
import MyList from "@/components/MyList.vue";

export default {
  name: "App",
  components: {
    MyHeader,
    MyFooter,
    MyList,
  },
  data() {
    // 数据存放在 App 中
    return {
      todos: [
        {
          id: "001",
          title: "吃饭",
          done: true,
        },
        {
          id: "002",
          title: "睡觉",
          done: false,
        },
        {
          id: "003",
          title: "开车",
          done: true,
        },
      ],
    };
  },
  methods:{
    // 添加一个元素
    receive(item){
      this.todos.unshift(item)
    },
    // 勾选 or 取消勾选一个 todo
    checkTodo(id){
      this.todos.forEach((todo) => {
        if(todo.id === id)
          todo.done = !todo.done
      })
    },
    // 删除一个元素
    deleteItem(id){
      this.todos = this.todos.filter((item) =>{
        return item.id != id
      })
    }


  }
};
</script>

<style>
/*base*/
body {
  background: #fff;
}
/* 按钮的样式 */
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
/* 按钮的样式完 */

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