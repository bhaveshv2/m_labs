<template>
  <div :class="{ 'dark': isDarkMode }" class="min-h-screen bg-gray-200 dark:bg-gray-900 p-8">
    <h1 class="text-3xl font-bold mb-8">Task Tracker</h1>
    <div class="flex justify-end mb-4">
      <button @click="toggleDarkMode" v-bind:class="isDarkMode?'text-gray-900 bg-white border border-gray-300 focus:outline-none hover:bg-gray-100 focus:ring-4 focus:ring-gray-100 font-medium text-sm px-5 py-2.5 me-2 mb-2 dark:bg-gray-800 dark:text-white dark:border-gray-600 dark:hover:bg-gray-700 dark:hover:border-gray-600 dark:focus:ring-gray-700'
  :'text-white bg-gray-800 hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium text-sm px-5 py-2.5 me-2 mb-2 dark:bg-gray-800 dark:hover:bg-gray-700 dark:focus:ring-gray-700 dark:border-gray-700'"
  >{{ isDarkMode ? 'Light Mode' :
        'Dark Mode' }}</button>
    </div>
    <task-form @add-task="addTask" />
    <task-list :tasks="tasks" :isDarkMode="isDarkMode" @edit-task="setEditingTask" @delete-task="deleteTask"  />
    <edit-task-form v-if="editingTask" :isDarkMode="isDarkMode" :task="editingTask" @edit-task="updateTask" />
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue';
import TaskForm from './components/TaskForm.vue';
import EditTaskForm from './components/EditTaskForm.vue';

export default {
  components: {
    TaskList,
    TaskForm,
    EditTaskForm,
  },
  data() {
    return {
      tasks: [
        { id: 1, title: "Task 1", description: "Description for Task 1" },
        { id: 2, title: "Task 2", description: "Description for Task 2" },
        { id: 3, title: "Task 3", description: "Description for Task 3" },
      ],
      editingTask: null,
      isDarkMode: false,
    };
  },
  methods: {
    addTask(task) {
      if(task.title!=="" && task.description!==""){
        this.tasks.push({ id: Date.now(), ...task });
      }
    },
    setEditingTask(task) {
      this.editingTask = task;
    },
    updateTask(editedTask) {
      const index = this.tasks.findIndex(task => task.id === editedTask.id);
      if (index !== -1) {
        this.tasks.splice(index, 1, editedTask);
        this.editingTask = null;
      }
    },
    deleteTask(task) {
      const index = this.tasks.findIndex(t => t.id === task.id);
      if (index !== -1) {
        this.tasks.splice(index, 1);
      }
    },
    toggleDarkMode() {
      this.isDarkMode = !this.isDarkMode;
    },
  },
};
</script>

<style>
/* Customize dark mode styles here */
.dark {
  background-color: #1a202c;
  color: #e2e8f0;
}
</style>
