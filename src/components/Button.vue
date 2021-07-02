<template>
    <button
        @click="onClick()"
        class="btn"
        :style="{ background: show_add_task ? 'red' : color }"
    >
        {{ show_add_task ? "Close" : text }}
    </button>
</template>
<script>
export default {
    name: "Button",
    props: {
        text: String,
        color: String,
        show_add_task: Boolean,
    },
    methods: {
        onClick() {
            this.$emit("btn-click");
        },
    },
};
</script>
