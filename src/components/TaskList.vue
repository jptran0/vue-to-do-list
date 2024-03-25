<template>
  <li>
    <p>{{ task }}</p>
    <button @click="$emit('delete', id)">X</button>
  </li>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
    },
    task: {
      type: String,
      required: true,
    },
    status: {
      type: Boolean,
      default: false,
    },
  },
  emits: ["delete"],
};
</script>

<style scoped>
button {
  color: red;
}
li {
  list-style: none;
}
</style>
