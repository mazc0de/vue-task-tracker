<template>
    <div :key="task.id" v-for="task in tasks">
        <Task @delete-task="onDelete(task.id)" @reminder-task="onReminder(task.id)" :task="task" />
    </div>
</template>

<script>
import Task from "./Task.vue";

export default {
    name: "Tasks",
    props: {
        tasks: Array,
    },
    components: {
        Task,
    },
    emits: ["delete-task", "reminder-task"],
    methods: {
        onDelete(id) {
            this.$emit("delete-task", id);
        },
        onReminder(id) {
            this.$emit("reminder-task", id);
        },
    },
};
</script>
