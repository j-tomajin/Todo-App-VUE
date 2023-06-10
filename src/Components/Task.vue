<template>
    <!-- ALL TASK -->
    <div :class="[allTask ? 'show' : 'hide', 'task']">
        <div :class="[task.complete ? 'complete' : '', 'task']">
            <Button 
                class="btn" 
                text="" 
                :bg_color="[task.complete ? 'black' : 'transparent']" 
                @btn-click="$emit('toggle-complete', task.id)"
            />
            <h3>{{ task.text }}</h3>
        </div>
    </div>

    <div :class="[showCompleted ? 'show' : 'hide', 'task']">
        <div :class="[task.complete ? 'complete' : 'hide', 'task']">
            <Button 
                class="btn" 
                @btn-click="$emit('toggle-complete', task.id)"
                text="" 
                :bg_color="[task.complete ? 'black' : 'transparent']" 
            />
            <h3>{{ task.text }}</h3>
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
            showCompleted: Boolean,
        },
        components: {
            Button,
        },
        emits: ['toggle-complete']
    }
</script>

<style lang="scss" scoped>
    .task {
        display: flex;
        align-items: center;
        justify-content: start;
        gap: 24px;
    }

    .complete {
        color: rgb(112, 112, 112);
        text-decoration: line-through;
    }

    .btn {
        padding: 12px;
        border: 1px solid #444;
        border-radius: 50px;
    }

    .show {
        display: block;
    }

    .hide {
        display: none;
    }
</style>