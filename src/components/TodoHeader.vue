<script>
export default {
  data() {
    return {
      todo: this.$props.todo,
    };
  },
};
</script>

<template>
  <header>
    <div>
      <input type="text" v-model="todo" />
      <button
        @click="
          () => {
            if (todo !== '') {
              $emit('addTodo', todo);
              todo = '';
            }
          }
        "
      >
        create todo
      </button>
    </div>
  </header>
</template>

<style scoped>
div {
  padding: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
}

input {
  padding: 1rem;
  border-radius: 0.3rem;
  margin: 0 1rem;
  border: none;
}

input:focus-visible {
  outline: none;
}

button {
  padding: 1rem;
  background-color: pink;
  border: none;
  border-radius: 5px;
  color: black;
}

@media screen and (width<500px) {
  div {
    justify-content: space-around;
    gap: 1rem;
  }

  input {
    margin: 0px;
    height: 3rem;
    padding: 0px;
    padding: 0px 4px;
  }

  button {
    padding: 0 1rem;
    height: 3rem;
  }
}
</style>
