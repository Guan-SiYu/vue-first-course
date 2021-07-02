<template>
    <h1>hiiii</h1>
    <Tasks :tasks="tasks" />
</template>
<script>
import Tasks from "../components/Tasks.vue";
export default {
    name: "Home",
    components: {
        Tasks,
    },
    data() {
        return { tasks: [] };
    },
    props: [],
    methods: {
        async fetchTasks() {
            const data = await fetch("http://localhost:5001/tasks");
            return data.json();
        },
    },
    async created() {
        console.log("tasks rendering");
        this.tasks = await this.fetchTasks();
    },
};
</script>
