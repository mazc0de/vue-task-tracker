<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label for="task">Task</label>
            <input type="text" v-model="text" name="text" placeholder="Add Task" />
        </div>
        <div class="form-control">
            <label for="day">Day & Time</label>
            <input type="text" v-model="day" name="day" placeholder="Add Day & Time" />
        </div>
        <div class="form-control form-control-check">
            <label for="reminder">Set Reminder</label>
            <input type="checkbox" v-model="reminder" name="reminder" />
        </div>
        <button type="submit" class="btn btn-block">Save Task</button>
    </form>
</template>
<script>
export default {
    name: "AddTask",
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
                alert("Please add the task!");
                return;
            }

            const newTask = {
                // id: Math.floor(Math.random() * 100000),
                text: this.text,
                day: this.day,
                reminder: this.reminder,
            };

            // data dikirim menggunakan emit, karena dari child components ke parent components
            this.$emit("add-task", newTask);

            this.text = "";
            this.day = "";
            this.reminder = false;
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
