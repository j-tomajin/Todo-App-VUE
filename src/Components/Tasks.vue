<template>
    <!-- All Tasks -->
     <div 
        :class="[allTask ? 'all-task' : 'hide', 'task']"
        v-for="task in tasks"
        :key="task.id"
    >
        <Task 
            @toggle-complete="toggleComplete(task.id)"
            @delete-task="$emit('delete-task', task.id)"
            :allTask="allTask"
            :task="task" /> 
    </div>
    
    <!-- Active Tasks -->
    <div 
        :class="[showActive ? 'active-task' : 'hide', 'task']"
        v-for="task in activeTask"
        :key="task.id"
    >
        <Task 
            @toggle-complete="toggleComplete(task.id)"
            @delete-task="$emit('delete-task', task.id)"
            :showActive="showActive"
            :task="task" />
        <!-- <p>sadfsdf</p> -->
    </div>

    <!-- Complete Tasks -->
    <div 
        :class="[showCompleted ? 'complete-task' : 'hide', 'task']"
        v-for="task in completedTask"
        :key="task.id"
    >
        <Task 
            @toggle-complete="toggleComplete(task.id)"
            @delete-task="$emit('delete-task', task.id)"
            :showCompleted="showCompleted"
            :task="task" />
    </div>

    <div class="line">
        <span>Nothing Follows</span>
    </div>
</template>

<script>
    import Task from './Task.vue';

    export default {
        name: 'Tasks',
        props: {
            tasks: Array,
            activeTask: Array,
            completedTask: Array,
            allTask: Boolean,
            showActive: Boolean,
            showCompleted: Boolean,
        },
        components: {
            Task,
        },
        methods: {
            toggleComplete(id) {
                this.$emit('toggle-complete', id)
            }
        },
        emits: ['toggle-complete', 'delete-task']
    }
</script>

<style lang="scss" scoped>
    .hide {
        display: none;
    }

    .task {
        padding: {
            inline: 1rem;
            top: 5px;
        };
        
        border-bottom: 1px solid var(--clr-line);
    }

    .complete-task, .all-task, .active-task {
        display: block;

        
    }

    .line {
        width: 100%;
        background-color: white;
        height: 2px;
        margin-block: 24px;
        text-align: center;
        border-radius: 50px;

        position: relative;

        span {
            background-color: var(--clr-background-todo);
            color: var(--clr-text-task);
            padding-inline: 16px;

            position: absolute;
            left: 50%;
            top: -12px;

            transform: translateX(-50%);
        }
    }
</style>