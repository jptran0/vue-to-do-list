<template>
  <li :class="['task-item', { completed: status }]">
    <p @click="toggleStatus">{{ status ? "✔ " : "" }}{{ task }}</p>
    <button @click="deleteTask(id)">x</button>
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
  border-radius: 25px;
  border: 1.5px solid rgb(231, 50, 50);
  background-color: #fff;
  cursor: pointer;
  overflow: hidden;
  color: red;
}
li {
  list-style: none;
}
.task-item {
  width: calc(100% - 32px);
  height: 50px;
  margin: 10px;
  border: 1.5px solid #ccc;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-radius: 10px;
}
.completed {
  color: green;
  text-decoration: line-through;
}
p {
  margin: 10px;
}
button {
  margin: 10px;
  align-items: center;
}
</style>
