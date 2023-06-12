<template>
    <div>
        <Button @btn-click="toggleTheme" />
    </div>
</template>

<script>
    import Button from './Button.vue';

    export default {
        name: 'ThemeSwitcher',
        components: {
            Button,
        },
        methods: {
            toggleTheme() {
                this.$emit('toggle-theme')
            }
        },
    }
</script>

<style lang="scss">
    .dark {
        --clr-red: red;
    }

    p {
        color: var(--clr-red);
    }
</style>