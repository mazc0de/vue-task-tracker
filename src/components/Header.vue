<template>
    <header>
        <h1>{{ title }}</h1>
        <Button v-show="homePage" @btn-click="toggleAddTask" :text="showAddTask ? 'Close' : 'Add Task'" :color="showAddTask ? 'red' : 'green'" />
    </header>
</template>

<script>
import Button from "../components/Button.vue";

export default {
    name: "Header",
    props: {
        title: String,
        showAddTask: Boolean,
    },
    components: {
        Button,
    },
    computed: {
        homePage() {
            if (this.$route.path === "/") {
                return true;
            }
        },
    },
    methods: {
        toggleAddTask() {
            this.$emit("toggle-add-task");
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
