<script>
export default {
  props: ["todo", "selected"],
};
</script>

<template>
  <li v-if="todo">
    <p>
      {{ todo }}
    </p>
    <div class="actions">
      <button
        @click="
          () => {
            selected = selected === 'todo' ? 'completed' : 'todo';
            $emit('edit', selected);
          }
        "
      >
        {{ selected }}
      </button>
      <button @click="$emit('delete')">x</button>
    </div>
  </li>
</template>

<style scoped>
li {
  padding: 12px;
  display: flex;
  align-items: center;
  background-color: #b9f4f4;
  justify-content: space-between;

  box-shadow: 1px 2.5px #85cccc;
  border-radius: 5px;
}

p {
  padding-left: 2rem;
  overflow-x: hidden;
}

button {
  padding: 4px 8px;
  background-color: rgb(255, 99, 125);
  color: white;
  border: none;
  border-radius: 5px;
}

.actions {
  display: flex;
  gap: 16px;
}
@media screen and (width<500px) {
  li {
    padding: 6px;
    gap: 1rem;
    min-width: 308px;
  }
  p {
    max-width: 10rem;
    padding-left: 0px;
  }
}
</style>
