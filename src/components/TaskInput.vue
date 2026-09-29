<template>
    <div class="task-input">
        <input type="text" v-model="newTask" placeholder="Enter new task" @keyup.enter="addTask">
        <select v-model="priority">
            <option value="Low">Low</option>
            <option value="Medium">Medium</option>
            <option value="High">High</option>
        </select>
        <button @click="addTask">Add task</button>
    </div>
</template>

<script>
export default {
    name: "TaskInput",

    data() {
        return {
            newTask: "",
            priority: "Medium"
        };
    },

    methods: {
        addTask() {
            if (this.newTask.trim() !== "") {
                this.$emit("add-task", {
                    title: this.newTask,
                    priority: this.priority
                });

                this.newTask = "";
                this.priority = "Medium";
            }
        }
    }
};
</script>

<style>
.task-input {
    display: grid;
    grid-template-columns: 6fr 1fr 1fr;
    gap: 10px;
    align-items: center;
    margin-bottom: 18px;
}

.task-input input,
.task-input select,
.task-input button {
    padding: 10px;
    box-sizing: border-box;
    border-radius: 8px;
    cursor: pointer;
}

.task-input input {
    border: 1px solid #aaa;
}

.task-input input:focus {
    border: 2px solid black;
    outline: none;
}

.task-input button {
    background-color: black;
    color: white;
    border: none;
    padding: 12px;
}

.task-input button:hover {
    opacity: 0.6;
}
</style>