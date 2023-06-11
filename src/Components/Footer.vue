<template>
    <div class="items-left">
        <p>{{ items }} item/s left</p>
    </div>
    
    <div class="buttons">
        <!-- Show All -->
        <Button
            @click="$emit('show-all')"
            text="All"
            bg_color="transparent" />

        <!-- Show Active -->
        <Button
            @click="$emit('show-active')"
            text="Active"
            bg_color="transparent"
        /> 
        
        <!-- Show Completed -->
        <Button 
            @click="$emit('show-completed')"
            text="Completed" 
            bg_color="transparent" /> 
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
</style>