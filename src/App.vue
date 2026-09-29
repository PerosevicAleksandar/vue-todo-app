<template>
  <div id="app">
    <h2>ToDo App</h2>
    <TaskInput @add-task="addTask" />
    <p v-if="tasks.length === 0">No tasks available.</p>
    <ul v-else>
      <TaskItem v-for="task in tasks" :key="task.id" :task="task" @complete-task="completeTask"
        @delete-task="deleteTask" />
    </ul>
  </div>
</template>

<script>
import TaskItem from "./components/TaskItem.vue";
import TaskInput from "./components/TaskInput.vue";

export default {
  name: "App",
  components: {
    TaskItem,
    TaskInput
  },
  data() {
    return {
      tasks: [
        { id: 1, title: "Learn Vue basics", completed: true, priority: "High" },
        { id: 2, title: "Practice Vue directives", completed: false, priority: "Medium" },
        { id: 3, title: "Create To Do App", completed: false, priority: "Low" }
      ]
    };
  },
  methods: {
    completeTask(task) {
      task.completed = true;
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id);
    },
    addTask(task) {
      this.tasks.push({
        id: Date.now(),
        title: task.title,
        completed: false,
        priority: task.priority
      });
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  max-width: 800px;
  margin: 0 auto;
  background-color: white;
  border-radius: 24px;
  padding: 12px;
}
</style>
