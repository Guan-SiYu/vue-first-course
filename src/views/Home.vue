<template>
    <div v-show="showAddTasksView">
        <AddTask :now_tasks_length="tasks.length" @add-new-task="addNewTask" />
    </div>
    <Tasks
        @toggle-reminder="toggleReminder"
        :tasks="tasks"
        @delete-task="deleteTask"
    />
</template>
<script>
import Tasks from "../components/Tasks.vue";
import AddTask from "../components/AddTask.vue";
export default {
    name: "Home",
    components: {
        Tasks,
        AddTask,
    },
    data() {
        return { tasks: [] };
    },
    props: ["showAddTasksView"],
    methods: {
        async deleteTask(id) {
            if (confirm("Are you sure?")) {
                const res = await fetch(`api/tasks/${id}`, {
                    method: "DELETE",
                });
                res.status === 200
                    ? (this.tasks = this.tasks.filter((item) => item.id !== id))
                    : alert("Error deleting task");
            }
        },
        async toggleReminder(id) {
            console.log("id=>", id);
            const target_item = await this.fetchOneTask(id);
            const res = await fetch(`api/tasks/${id}`, {
                method: "PUT",
                headers: {
                    "Content-type": "application/json",
                },
                body: JSON.stringify({
                    ...target_item,
                    reminder: !target_item.reminder,
                }),
            });

            const tasks = await this.fetchTasks();

            this.tasks = tasks;
        },
        async addNewTask(new_task) {
            const res = await fetch("api/tasks", {
                method: "POST",
                headers: {
                    "Content-type": "application/json",
                },
                body: JSON.stringify(new_task),
            });
            const newTask = await res.json();
            this.tasks = this.tasks.concat(newTask);
        },
        async fetchTasks() {
            const data = await fetch("api/tasks");
            return data.json();
        },
        async fetchOneTask(id) {
            const item = await fetch(`api/tasks/${id}`);
            return item.json();
        },
    },
    async created() {
        this.tasks = await this.fetchTasks();
    },
};
</script>
