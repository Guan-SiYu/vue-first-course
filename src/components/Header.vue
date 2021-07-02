<template>
    <header>
        <h1>{{ title }}</h1>
        <Button
            v-show="homePage"
            @btn-click="$emit('toggle-add-task-view')"
            text="Add Task"
            color="green"
            :show_add_task="show_add_task"
        />
    </header>
</template>

<script>
import Button from "./Button";
export default {
    name: "Header",
    props: {
        title: {
            type: String,
            default: "写一个计划吧",
        },
        show_add_task: Boolean,
    },
    components: {
        Button,
    },
    computed: {
        homePage() {
            return this.$route.path === "/";
        },
    },
};
</script>
<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>
