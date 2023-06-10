<template>
    <header class="header">
        <h1 class="text-head">TODO</h1>
        <Button text="" bg_color="black" />
    </header>
</template>

<script>
    import Button from './Button.vue';

    export default {
        name: 'Header',
        components: {
            Button,
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