<!-- src/components/TaskItem.vue -->
<template>
    <div v-bind:class="isDarkMode ? 'flex justify-between items-center bg-gray-100 p-4 mb-2':'flex justify-between items-center bg-gray-800 p-4 mb-2'">
        <div>
            <h3 v-bind:class="isDarkMode?'text-black':'text-white'">{{ task.title }}</h3>
            <p v-bind:class="isDarkMode ? 'text-black' : 'text-white'">{{ task.description }}</p>
        </div>
        <div>
            <button @click="editTask" class="text-white bg-yellow-400 hover:bg-yellow-500 focus:outline-none focus:ring-4 focus:ring-yellow-300 font-medium text-sm px-5 py-2.5 text-center me-2 mb-2 mr-2 dark:focus:ring-yellow-900">Edit</button>
            <button @click="deleteTask" class="focus:outline-none text-white bg-red-700 hover:bg-red-800 focus:ring-4 focus:ring-red-300 font-medium text-sm px-5 py-2.5 me-2 mb-2 dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-900">Delete</button>
        </div>
    </div>
</template>

<script>
export default {
    props: ['task','isDarkMode'],
    methods: {
        editTask() {
            this.$emit('edit-task', this.task);
        },
        deleteTask() {
            this.$emit('delete-task', this.task);
        },
    },
};
</script>
