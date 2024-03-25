<template>
  <div>
    <input
      type="text"
      placeholder="Enter a new task"
      ref="inputTask"
      v-on:keyup.enter="submitTask"
    />
  </div>
</template>

<script>
export default {
  methods: {
    submitTask() {
      const newTask = this.$refs.inputTask.value;
      if (newTask.trim() !== "") {
        this.addTask(newTask);
      }
      this.$refs.inputTask.value = "";
    },
  },
  inject: ["addTask"],
};
</script>
