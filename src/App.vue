<template>
    <div class="container">
        <h1>Todo List hahahah</h1>
        <Header
            @toggle-add-task-view="toggleAddTaskView"
            :show_add_task="showAddTasksView"
        />

        <router-view :showAddTasksView="showAddTasksView"></router-view>
        <Footer />
    </div>
</template>

<script>
import Header from "./components/Header";
import Footer from "./components/Footer.vue";
export default {
    name: "App",
    components: {
        Header,
        Footer,
    },
    data() {
        return {
            showAddTasksView: false,
        };
    },
    methods: {
        toggleAddTaskView() {
            this.showAddTasksView = !this.showAddTasksView;
        },
    },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
body {
    font-family: "Poppins", sans-serif;
}
.container {
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
}
.btn {
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
}
</style>
