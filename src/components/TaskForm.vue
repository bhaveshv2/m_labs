<!-- src/components/TaskForm.vue -->
<template>
    <form @submit.prevent="handleSubmit" class="mb-8">
        <div class="mb-4">
            <label for="title" class="block font-semibold">Task Title:</label>
            <input v-model="title" type="text" id="title" class="border border-gray-300 px-3 py-2 w-full">
        </div>
        <div class="mb-4">
            <label for="description" class="block font-semibold">Task Description:</label>
            <textarea v-model="description" id="description"
                class="border border-gray-300 px-3 py-2 w-full"></textarea>
        </div>
        <div>
            <button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium text-sm px-5 py-2.5 me-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">Add Task</button>
        </div>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: '',
            description: '',
        };
    },
    methods: {
        handleSubmit() {
            this.$emit('add-task', {
                title: this.title,
                description: this.description,
            });
            this.title = '';
            this.description = '';
        },
    },
};
</script>
