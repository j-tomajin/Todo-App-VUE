<template>
    <header class="header">
        <h1 class="text-head">{{ text }}</h1>
        <Button text="" bg_color="black" />
    </header>
</template>

<script>
    import Button from './Button.vue';

    export default {
        name: 'Header',
        components: {
            Button,
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
        color: white;
        letter-spacing: 3px;
        font-size: 3rem;
    }
</style>