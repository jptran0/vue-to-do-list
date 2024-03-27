<template>
  <section>
    <header>
      <h2>To-Do List</h2>
    </header>
    <div>
      <new-task></new-task>
      <ul>
        <task-list
          v-for="task in tasks"
          :key="task.id"
          :id="task.id"
          :task="task.task"
          :status="task.status"
          @toggle-status="toggleStatus"
        ></task-list>
      </ul>
    </div>
  </section>
</template>

<script>
import NewTask from "./components/NewTask.vue";
import TaskList from "./components/TaskList.vue";

export default {
  name: "App",
  components: {
    NewTask,
    TaskList,
  },
  data() {
    return {
      tasks: [
        {
          id: "course",
          task: "Complete the Vue.js Udemy course",
          status: false,
        },
        {
          id: "project",
          task: "Complete first Vue.js project",
          status: false,
        },
        {
          id: "review",
          task: "Review notes",
          status: false,
        },
      ],
    };
  },
  methods: {
    deleteTask(taskId) {
      // todos = todos.filter((x) => x.id !== todoId);
      const taskIndex = this.tasks.findIndex((task) => task.id === taskId);
      this.tasks.splice(taskIndex, 1);
    },
    addTask(task) {
      const newTask = {
        id: new Date().toISOString(),
        task: task,
      };
      this.tasks.unshift(newTask);
    },
    toggleStatus(taskId) {
      const identifiedTask = this.tasks.find((task) => task.id === taskId);
      identifiedTask.status = !identifiedTask.status;
    },
  },
  provide() {
    return {
      addTask: this.addTask,
      deleteTask: this.deleteTask,
      toggleStatus: this.toggleStatus,
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
section {
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  margin: 2rem auto;
  max-width: 50%;
}
ul {
  padding-left: 10px;
  justify-content: center;
}
</style>
