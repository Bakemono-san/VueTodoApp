<script>
import TodoHeader from "./components/TodoHeader.vue";
import Todo from "./components/Todo.vue";

export default {
  components: {
    TodoHeader,
    Todo,
  },
  data() {
    return {
      todos: [],
      selected: "all",
      filteredData: [],
    };
  },

  mounted() {
    this.filteredData = this.todos;
  },

  methods: {
    createTodo(todo) {
      this.todos = [...this.todos, { title: todo, status: "todo" }];
    },

    delet(index) {
      this.todos.splice(index, 1);
    },
  },
  computed: {
    filterCompleted() {
      if (this.selected === "all") {
        return (this.filteredData = this.todos);
      }
      this.filteredData = this.todos.filter(
        (data) => data.status === this.selected
      );
    },
  },
};
</script>

<template>
  <h1>To-do list</h1>
  <p>simple app to manage your daily todos</p>

  <div class="container">
    <TodoHeader
      @addTodo="
        (todo) => {
          createTodo(todo);
        }
      "
    />
    <div class="filtre">
      <div v-if="selected.length">
        <input
          type="radio"
          id="all"
          value="all"
          v-model="selected"
          :onSelect="filterCompleted"
        />
        <label for="all">all</label>
      </div>
      <div>
        <input
          type="radio"
          id="completed"
          value="completed"
          v-model="selected"
        />
        <label for="completed">completed</label>
      </div>
      <div>
        <input type="radio" id="todo" value="todo" v-model="selected" />
        <label for="todo">todo</label>
      </div>
    </div>
    <div class="todoList">
      <Todo
        v-if="filteredData.length > 0"
        v-for="(todo, index) in filteredData"
        @delete="delet(index)"
        :todo="todo.title"
        :selected="todo.status"
        :key="index"
        @edit="
          (status) => {
            todo.status = status;
          }
        "
      />
      <p v-else style="font-size: 24px; height: 100%">it's quite here...</p>
    </div>
  </div>
</template>

<style scoped>
h1 {
  color: rgb(255, 162, 178);
}
.container {
  max-width: 500px;
  height: 500px;
  background-color: rgb(218, 255, 255);
  border-radius: 5px;
  overflow: scroll;
}
.filtre {
  padding: 16px;
  display: flex;
  gap: 24px;
  align-items: center;
  justify-content: space-around;
  border-radius: 5px;
}

.filtre div {
  display: flex;
  gap: 8px;
}

.todoList {
  display: flex;
  flex-direction: column;

  gap: 0.7rem;

  padding: 1rem 2rem;
}
</style>
