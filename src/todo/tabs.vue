<template>
  <div class="helper">
    <span class="left">{{unFinishedTodoLength}} item left</span>

    <span class="tabs">
      <span
        v-for="state in states"
        :key="state"
        :class="[state, filter === state ? 'actived' : '']"
        @click="toggleFilter(state)"
      >{{state}}</span>
    </span>
    <span class="clear" @click="clearAllCompleted">Clear Completed</span>
  </div>
</template>
<script>
//filter:代表选中的状态
export default {
  props: {
    filter: {
      type: String,
      required: true
    },
    todos: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      states: ["all", "active", "completed"]
    };
  },
  computed: {
    unFinishedTodoLength() {
      return this.todos.filter(todo => !todo.completed).length;
    }
  },

  methods: {
    toggleFilter(state) {
      console.log("state儿子", state);
      this.$emit("togole", state);
    },
    clearAllCompleted() {
      this.$emit("clearAll");
    }
  },
  created() {
    console.log(this.filter);
  }
};
</script>
<style scoped>
.helper {
  border-top: 1px solid #cccccc40;
  padding: 10px 0 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.tabs span {
  padding: 4px;
  border-radius: 4px;
  cursor: pointer;
}
.tabs span.actived {
  border: 2px solid #ffc800;
}
.clear {
  cursor: pointer;
}
</style>