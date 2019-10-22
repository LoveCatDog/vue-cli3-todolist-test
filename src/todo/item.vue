<template>
  <div :class="['todo_item',todo.completed ? 'completed' :'']">
    <input type="checkbox" class="toggle" v-model="todo.completed" />
    <label>{{todo.content}}</label>
    <button class="destory" @click="deleteToDo">删除</button>
  </div>
</template>
<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  methods: {
    deleteToDo() {
      this.$emit("del", this.todo.id);
    }
  }
};
</script>
<style scoped>
.todo_item {
  padding: 10px;
  border-top: 1px solid #cccccc40;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.completed label {
  text-decoration: line-through;
  color: #99999952;
}
button {
  cursor: pointer;
}
</style>