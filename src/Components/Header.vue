<template>
    <header class="header">
        <h1 class="text-head">{{ text }}</h1>
        <Button text="" />
        <!-- <ThemeContainer /> -->
    </header>
</template>

<script>
    import Button from './Button.vue';
    // import ThemeContainer from './ThemeContainer.vue';

    export default {
        name: 'Header',
        components: {
            Button,
            // ThemeContainer
        },
        props: {
            text: {
                type: String,
                default: 'This is header'
            }
        }
    }
</script>

<style lang="scss" scoped>
    .header {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .text-head {
        color: var(--clr-head);
        letter-spacing: 5px;
        font-size: 2rem;
    }
</style>