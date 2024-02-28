<template>
    <form @submit.prevent="handleSubmit">
        <div class="mb-4">
            <label for="editTitle" class="block font-semibold">Task Title:</label>
            <input v-model="editedTask.title" type="text" id="editTitle"
                v-bind:class="isDarkMode? 'border border-gray-300 px-3 py-2 w-full text-black':'border border-gray-300 px-3 py-2 w-full text-black'">
        </div>
        <div class="mb-4">
            <label for="editDescription" class="block font-semibold">Task Description:</label>
            <textarea v-model="editedTask.description" id="editDescription"
                v-bind:class="isDarkMode ? 'border border-gray-300 px-3 py-2 w-full text-black' : 'border border-gray-300 px-3 py-2 w-full text-black'"></textarea>
        </div>
        <div>
            <button type="submit" class="text-white bg-green-700 hover:bg-green-800 focus:outline-none focus:ring-4 focus:ring-green-300 font-medium text-sm px-5 py-2.5 text-center me-2 mb-2 dark:bg-green-600 dark:hover:bg-green-700 dark:focus:ring-green-800">Save Changes</button>
        </div>
    </form>
</template>

<script>
export default {
    props: ['task'],
    data() {
        return {
            editedTask: { ...this.task },
        };
    },
    methods: {
        handleSubmit() {
            this.$emit('edit-task', this.editedTask);
        },
    },
};
</script>
