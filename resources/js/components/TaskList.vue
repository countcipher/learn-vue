<template>
    <div class="task-list">
        <h2>{{ title }}</h2>
        <p>You have {{ taskCount }} tasks</p>

        <ul>
            <li v-for="task in tasks" :key="task.id">{{ task.name }}</li>
        </ul>
    </div>
</template>

<script setup>
// Import ref and computed from Vue
// ref: for reactive data
// computed: for values derived from other reactive data
import { ref, computed } from "vue";

// Define props - these are inputs that can be passed to this component from a parent
// Props are read-only and come from outside the component
const props = defineProps({
    title: {
        type: String, // Validates that 'title' must be a string
        default: "My tasks", // Default value if no title is provided
    },
});

// Create a reactive array of tasks
// ref() wraps the data and makes it reactive
// To access the actual value, you use .value in JavaScript (but not in the template)
const tasks = ref([
    { id: 1, name: "Learn Vue basics" },
    { id: 2, name: "Create first component" },
    { id: 3, name: "Integrate with Laravel" },
]);

// Create a computed property for the task count
// computed() automatically updates whenever its dependencies (tasks.value) change
// This is the "best practice" way to handle derived state
const taskCount = computed(() => tasks.value.length);
</script>

<style scoped>
.task-list {
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 8px;
}

h2{
    color: #2c3e50;
}

ul{
    list-style: none;
    padding: 0;
}

li{
    padding: 10px;
    margin: 5px 0;
    background: #f5f5f5;
    border-radius: 4px;
}
</style>

/**
this is just a comment
*/
