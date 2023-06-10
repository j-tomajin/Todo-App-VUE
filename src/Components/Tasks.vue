<template>
     <div 
        :class="[allTask ? 'all-task' : 'hide', 'task']"
        v-for="task in tasks"
        :key="task.id"
    >
        <Task 
            @toggle-complete="$emit('toggle-complete', task.id)"
            :allTask="allTask"
            :task="task" /> 
    </div>
    
    <div 
        :class="[showCompleted ? 'complete-task' : 'hide', 'task']"
        v-for="task in completedTask"
        :key="task.id"
    >
        <Task 
            @toggle-complete="$emit('toggle-complete', task.id)"
            :showCompleted="showCompleted"
            :task="task" />
    </div>
</template>

<script>
    import Task from './Task.vue';

    export default {
        name: 'Tasks',
        props: {
            tasks: Array,
            completedTask: Array,
            allTask: Boolean,
            showCompleted: Boolean,
        },
        components: {
            Task,
        },
        emits: ['toggle-complete']
    }
</script>

<style lang="scss" scoped>
    .hide {
        display: none;
    }

    .complete-task, .all-task {
        display: block;
    }
</style>