<template>
<div v-for="task in tasks" :key="task.id">
<!-- <h3>{{ task.text }}</h3> -->
<Task :task="task" @delete-task="$emit('delete-task', task.id)" 
    @toggle-reminder="$emit('toggle-reminder', task.id)"
/>
</div>
</template>

<script>
import Task from './Task.vue'

export default {
    name: 'Tasks',
    components: {
      Task
    },
    props: {
        tasks: Array
    },
    emits: ['delete-task', 'toggle-reminder']

}
</script>

<style scoped>

</style>