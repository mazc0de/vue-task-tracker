<template>
    <div @dblclick="onReminder(task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>
            {{ task.text }}
            <i @click="onDelete(task.id)" class="fas fa-times"></i>
        </h3>
        <p>{{ task.day }}</p>
    </div>
</template>

<script>
export default {
    name: "Task",
    props: {
        task: Object,
    },
    methods: {
        // emit berguna untuk mengirim data dari child components ke parent
        onDelete(id) {
            this.$emit("delete-task", id);
        },
        onReminder(id) {
            this.$emit("reminder-task", id);
        },
    },
};
</script>

<style scoped>
.fas {
    color: red;
}

.task {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}

.task.reminder {
    border-left: 5px solid green;
}

.task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>
