<template>
    <!-- ALL TASKS -->
    <div :class="[allTask ? 'show' : 'hide', 'task']">
        <div :class="[task.complete ? 'complete' : '', 'task']">
            <Button 
                class="btn" 
                text="" 
                :bg_color="[task.complete ? 'black' : 'transparent']" 
                @btn-click="$emit('toggle-complete', task.id)"
            />
            <h3>{{ task.text }}</h3>

            <Button 
                class="delete-task-btn" 
                text="Delete"
                bg_color="rgb(255, 65, 65)"
                @btn-click="$emit('delete-task', task.id)"
            />
        </div>
    </div>

    <!-- ACTIVE TASKS -->
    <div :class="[showActive ? 'show' : 'hide', 'task']">
        <div :class="[!task.complete ? '' : 'hide', 'task']">
            <Button 
                class="btn" 
                @btn-click="$emit('toggle-complete', task.id)"
                text="" 
                :bg_color="[task.complete ? 'black' : 'transparent']" 
            />
            <h3>{{ task.text }}</h3>

            <Button 
                class="delete-task-btn" 
                text="Delete"
                bg_color="rgb(255, 65, 65)"
                @btn-click="$emit('delete-task', task.id)"
            />
        </div>
    </div>

    <!-- COMPLETE TASKS -->
    <div :class="[showCompleted ? 'show' : 'hide', 'task']">
        <div :class="[task.complete ? 'complete' : 'hide', 'task']">
            <Button 
                class="btn" 
                @btn-click="$emit('toggle-complete', task.id)"
                text="" 
                :bg_color="[task.complete ? 'black' : 'transparent']" 
            />
            <h3>{{ task.text }}</h3>

            <Button 
                class="delete-task-btn" 
                text="Delete"
                bg_color="rgb(255, 65, 65)"
                @btn-click="$emit('delete-task', task.id)"
            />
        </div>
    </div>
</template>

<script>
    import Button from './Button.vue';

    export default {
        name: 'Task',
        props: {
            task: Object,
            allTask: Boolean,
            showActive: Boolean,
            showCompleted: Boolean,
        },
        components: {
            Button,
        },
        emits: ['toggle-complete', 'delete-task']
    }
</script>

<style lang="scss" scoped>
    .task {
        display: flex;
        align-items: center;
        justify-content: start;
        gap: 24px;
        margin-bottom: 8px;
    }

    .complete {
        color: rgb(112, 112, 112);
        h3 {
            text-decoration: line-through;
        }
    }

    .btn {
        padding: 12px;
        border: 1px solid #444;
        border-radius: 50px;
    }

    .delete-task-btn {
        margin-left: auto;
        border: none;
        border-radius: 8px;
        color: white;
    }

    .show {
        display: block;
    }

    .hide {
        display: none;
    }
</style>