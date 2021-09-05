<template>
  <ul class="todo-main">
    <MyItem
      v-for="item in todos"
      :key="item.id"
      :todo="item"
      :checkTodo="checkTodo"
      :deleteItem="deleteItem"
    />
  </ul>
</template>

<script>
import MyItem from "@/components/MyItem.vue";
export default {
  name: "MyList",
  props: ["todos", 
          "checkTodo",
          "deleteItem"
          ],
  components: {
    MyItem,
  },
  created() {
    console.log(this.todos);
  },
};
</script>

<style scoped>
/*main*/
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