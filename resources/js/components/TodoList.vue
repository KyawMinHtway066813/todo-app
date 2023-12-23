<template>
    <div>
      <h2>Todo List</h2>
      <ul>
        <li v-for="task in tasks" :key="task.id">
          {{ task.title }}
        </li>
      </ul>
    </div>
  </template>

  <script>
  export default {
    data() {
      return {
        tasks: [],
      };
    },
    mounted() {
      // Fetch tasks from the Laravel backend when the component is mounted
      this.fetchTasks();
    },
    methods: {
      async fetchTasks() {
        // Make an API request to Laravel backend to get tasks
        try {
          const response = await axios.get('/api/tasks');
          this.tasks = response.data;
        } catch (error) {
          console.error('Error fetching tasks', error);
        }
      },
    },
  };
  </script>

  <style scoped>
  /* Add some styling if needed */
  </style>
