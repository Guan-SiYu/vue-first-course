<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label for="">你的下一下一项计划✏️</label>
            <input
                type="text"
                v-model="text"
                name="text"
                placeholder="想干啥..."
            />
        </div>
        <div class="form-control">
            <label for="">⏱ 日期 & 时间</label>
            <input
                type="text"
                v-model="day"
                name="day"
                placeholder="打算啥时候整"
            />
        </div>
        <div class="form-control form-control-check">
            <label for="">⏰设置提醒</label>
            <input type="checkbox" v-model="reminder" name="reminder" />
        </div>
        <input type="submit" value="我好了" class="btn btn-block" />
    </form>
</template>
<script>
export default {
    name: "AddTask",
    props: {
        now_tasks_length: Number,
    },
    data() {
        return {
            text: "",
            day: "",
            reminder: false,
        };
    },
    methods: {
        onSubmit(e) {
            e.preventDefault();
            if (!this.text) {
                alert("Please add a task");
                return;
            }
            const new_task = {
                id: this.now_tasks_length + 1,
                text: this.text,
                day: this.day,
                reminder: this.reminder,
            };
            console.log("new_task=>", new_task);
            this.text = "";
            this.day = "";
            this.reminder = false;

            this.$emit("add-new-task", new_task);
        },
    },
};
</script>
<style scoped>
.add-form {
    margin-bottom: 40px;
}
.form-control {
    margin: 20px 0;
}
.form-control label {
    display: block;
}
.form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}
.form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.form-control-check label {
    flex: 1;
}
.form-control-check input {
    flex: 2;
    height: 20px;
}
</style>
