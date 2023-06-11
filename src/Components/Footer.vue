<template>
    <div class="items-left">
        <p>{{ items }} item/s left</p>
    </div>
    
    <div class="buttons">
        <!-- Show All -->
        <Button
            @click="$emit('show-all')"
            text="All"
            bg_color="transparent"
            :class="[allTask ? 'active' : '']" 
        />

        <!-- Show Active -->
        <Button
            @click="$emit('show-active')"
            text="Active"
            bg_color="transparent"
            :class="[showActive ? 'active' : '']"
        /> 
        
        <!-- Show Completed -->
        <Button 
            @click="$emit('show-completed')"
            text="Completed" 
            bg_color="transparent" 
            :class="[showCompleted ? 'active' : '']"    
        /> 
    </div>

    <!-- Clear completed -->
    <Button 
        @click="$emit('clear-completed')"
        text="Clear completed" 
        bg_color="transparent" 
        class="btn" />
</template>

<script>
    import Button from './Button.vue';
    
    export default {
        name: 'Footer',
        components: {
            Button,
        },
        props: {
            items: Number,
            allTask: Boolean,
            showActive: Boolean,
            showCompleted: Boolean,
        },
        emits: ['show-completed', 'show-all', 'show-active', 'clear-completed']
    }
</script>

<style lang="scss" scoped>
    .btn {
        color: white;
        padding: 0;
    }

    .buttons {
        display: flex;
        align-items: center;
        gap: 8px;
    }

    .active {
        color: rgb(0, 162, 255);
        font-weight: bold;
    }
</style>