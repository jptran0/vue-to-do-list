<template>
  <li>
    <p @click="toggleStatus">{{ task }} {{ status ? "Done" : "" }}</p>
    <button @click="deleteTask(id)">X</button>
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
  inject: ["deleteTask"],
  methods: {
    toggleStatus() {
      this.$emit("toggle-status", this.id);
    },
  },
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
