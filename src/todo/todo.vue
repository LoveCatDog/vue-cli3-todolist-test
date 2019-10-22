<template>
  <div id="input_todo_input">
    <section class="real-app">
      <input
        type="text"
        class="add_input"
        autofocus="autofocus"
        placeholder="接下来要做什么"
        @keyup.enter="addTodo"
      />
      <div id="todo_overflow">
        <Item :todo="item" v-for="(item,index) in filteredToDos" :key="index" @del="deleteToDo()" />
      </div>

      <Tabs :filter="filter" :todos="todos" @togole="togoleFilter" @clearAll="clearAllCompleted" />
    </section>
  </div>
</template>
<script>
import Item from "./item.vue";
import Tabs from "./tabs.vue";
let id = 0;
export default {
  data() {
    return {
      // todo: { //顶层数据
      //   id: 0,
      //   content: "this is todo",
      //   completed: false
      // },
      filter: "all",
      todos: []
    };
  },
  computed: {
    filteredToDos() {
      if (this.filter === "all") {
        return this.todos;
      }
      const completed = this.filter === "completed";
      return this.todos.filter(todo => completed === todo.completed);
    }
  },
  methods: {
    addTodo(e) {
      this.todos.unshift({
        id: id++,
        content: e.target.value.trim(),
        completed: false
      });
      e.target.value = "";
    },
    deleteToDo(id) {
      this.todos.splice(this.todos.findIndex(todo => todo.id === id), 1);
    },
    togoleFilter(state) {
      console.log("state父亲", state);
      this.filter = state;
    },
    clearAllCompleted() {
      this.todos = this.todos.filter(todo => !todo.completed);
    }
  },
  components: {
    Item,
    Tabs
  }
};
</script>
<style scoped>
#input_todo_input {
  width: 800px;
  background: #fff;
  margin: 20px auto;
  padding: 20px;
}
.add_input {
  width: 300px;
  border: transparent;
  padding: 4px 10px;
  font-size: 20px;
  margin-bottom: 10px;
  box-shadow: 1px 1px 10px #4caf50;
}
#todo_overflow {
  overflow-y: scroll;
  max-height: 420px;
}
</style>