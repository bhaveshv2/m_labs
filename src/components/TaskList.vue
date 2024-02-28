<!-- src/components/TaskList.vue -->
<template>
    <div>
        <h2 class="text-2xl font-bold mb-4">Task List</h2>
        <ul>
            <li v-for="task in tasks" :key="task.id">
                <TaskItem :isDarkMode="isDarkMode" :task="task" @edit-task="editTask" @delete-task="deleteTask" />
            </li>
        </ul>
    </div>
</template>

<script>
import TaskItem from './TaskItem.vue';

export default {
    props: ['tasks','isDarkMode'],
    components: {
        TaskItem,
    },
    methods: {
        editTask(task) {
            this.$emit('edit-task', task);
        },
        deleteTask(task) {
            this.$emit('delete-task', task);
        },
    },
};
</script>
