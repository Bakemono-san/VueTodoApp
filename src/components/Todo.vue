<script>
export default {
  props: ["todo", "selected"],
};
</script>

<template>
  <li>
    <p>
      {{ todo }}
    </p>
    <div class="actions">
      <button
        @click="
          () => {
            selected = selected === 'todo' ? 'completed' : 'todo';
          }
        "
      >
        {{ selected }}
      </button>
      <button @click="$emit('delete')">x</button>
    </div>
  </li>
</template>

<style>
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
  color: rgb(0, 184, 184);
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
</style>
