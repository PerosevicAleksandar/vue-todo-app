<template>
    <li :class="{ completedTask: task.completed, highPriority: task.priority === 'High' }">
        <div class="task-info">
            <h4>{{ task.title }}</h4>
            <p><span>Priority: </span>{{ task.priority }}</p>
            <p><span>Status: </span>{{ task.completed ? "Completed" : "Active" }}</p>
        </div>
        <div class="actions">
            <button v-if="!task.completed" @click="completeTask" class="complete-btn">Complete</button>
            <button @click="deleteTask" class="delete-btn">Delete</button>
        </div>
    </li>
</template>

<script>
export default {
  name: "TaskItem",
  props: ["task"],
  methods: {
    completeTask() {
      this.$emit("complete-task", this.task);
    },

    deleteTask() {
      this.$emit("delete-task", this.task.id);
    }
  }
};
</script>

<style>
    .completedTask {
  opacity: 0.6;
}

.completedTask h4:first-child {
  text-decoration: line-through;
}

ul {
  padding: 0;
}

li {
  list-style: none;
  border: 1px solid #aaa;
  border-radius: 24px;
  margin: 10px auto;
  display: flex;
  justify-content: space-between;
  padding: 8px 12px;
}

.task-info h4, 
.task-info p {
  font-weight: bold;
}

.task-info span {
  color: #aaa;
  font-weight: normal;
}

.highPriority {
  border-left: 4px solid #d9534f;
  background-color: #fff5f5;
}

.actions {
  display: flex;
  align-items: center;
  gap: 6px;
}

.complete-btn {
  border: none;
  border-radius: 8px;
  color: white;
  background-color: #2c7d34;
  padding: 8px 10px;
  cursor: pointer;
}

.delete-btn {
  border: none;
  border-radius: 8px;
  color: white;
  background-color: #c8282b;
  padding: 8px 10px;
  cursor: pointer;
}

button:hover {
    opacity: 0.6;
}
</style>