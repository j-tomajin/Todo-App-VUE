<template>
    <!-- ALL TASKS -->
    <div :class="[allTask ? 'show' : 'hide', 'task']">
        <div :class="[task.complete ? 'complete' : '', 'task']">
            <Button 
                class="btn" 
                @btn-click="toggleComplete(task.id)"
                text="" 
                :bg_color="[task.complete ? 'black' : 'transparent']" 
            />

            <h3 @click="toggleComplete(task.id)">{{ task.text }}</h3>

            <button 
                type="button" 
                class="delete-task-btn hide-btn" 
                @click="$emit('delete-task', task.id)"
            >
                <img src="../assets/icons/icon-cross.svg" alt="cross/delete task">
            </button>
        </div>
    </div>

    <!-- ACTIVE TASKS -->
    <div :class="[showActive ? 'show' : 'hide', 'task']">
        <div :class="[!task.complete ? '' : 'hide', 'task']">
            <Button 
                class="btn" 
                @btn-click="toggleComplete(task.id)"
                text="" 
                :bg_color="[task.complete ? 'black' : 'transparent']" 
            />

            <h3 @click="toggleComplete(task.id)">{{ task.text }}</h3>

            <button 
                type="button" 
                class="delete-task-btn hide-btn" 
                @click="$emit('delete-task', task.id)"
            >
                <img src="../assets/icons/icon-cross.svg" alt="cross/delete task">
            </button>
        </div>
    </div>

    <!-- COMPLETE TASKS -->
    <div :class="[showCompleted ? 'show' : 'hide', 'task']">
        <div :class="[task.complete ? 'complete' : 'hide', 'task']">
            <Button 
                class="btn" 
                @btn-click="toggleComplete(task.id)"
                text="" 
                :bg_color="[task.complete ? 'black' : 'transparent']" 
            />

            <h3 @click="toggleComplete(task.id)">{{ task.text }}</h3>

            <button 
                type="button" 
                class="delete-task-btn hide-btn" 
                @click="$emit('delete-task', task.id)"
            >
                <img src="../assets/icons/icon-cross.svg" alt="cross/delete task">
            </button>
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
        methods: {
            toggleComplete(id) {
                this.$emit('toggle-complete', id)
            },
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

        color: var(--clr-text-task);

        h3 {
            font-weight: bold;
            cursor: pointer;
        }

        &:hover > .hide-btn {
            display: block;
        }
    }
    
    .complete {
        color: var(--clr-text-task-complete);
        
        h3 {
            text-decoration: line-through;
        }
    }

    .btn {
        padding: 12px;
        border: 1px solid #444;
        border-radius: 50px;
    }

    .hide-btn {
        display: none;
    }

    .delete-task-btn {
        margin-left: auto;
        border: none;
        border-radius: 8px;
        color: var(--clr-text);
        border: none;
        outline: 0;
        background-color: transparent;
    }

    .show {
        display: block;
    }

    .hide {
        display: none;
    }
</style>