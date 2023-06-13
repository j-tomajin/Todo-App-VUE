<template>
    <div class="footer">
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
    </div>
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
    .footer {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: {
            inline: 1rem;
            bottom: .5rem;
        };
        
        position: relative;
    }

    .btn {
        color: var(--clr-text);
        padding: 0;
        transition: color 150ms ease-in;

        &:hover {
            color: var(--clr-hover);
        }
    }

    .buttons {
        background-color: var(--clr-background-todo);
        padding: 1rem;
        width: 100%;

        display: flex;
        align-items: center;
        justify-content: center;
        gap: 8px;

        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        bottom: -5rem;

        transition: all 500ms ease-in;

        @media only screen and (min-width: 600px) {
            padding: unset;
            width: auto;

            position: unset;
            transform: unset;
        }
    }

    .items-left {
        color: var(--clr-text);
    }
    
    .active {
        color: var(--clr-accent);
        font-weight: bold;
    }
</style>