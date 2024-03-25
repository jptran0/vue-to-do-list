<template>
  <li>
    <p @click="toggleStatus" :class="['task-item', { completed: status }]">
      {{ status ? "✔ " : "" }}{{ task }}
    </p>
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
.task-item {
  width: calc(100% - 32px);
  height: 70px;
  margin: 16px;
  border: 2px solid #ccc;
}
.completed {
  color: green;
  text-decoration: line-through;
}
</style>
