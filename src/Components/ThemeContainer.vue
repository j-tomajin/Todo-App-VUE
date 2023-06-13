<!-- <template>
    <div :class="currentTheme">
        <ThemeSwitcher
            @theme-toggle="toggleTheme"
        />
    </div>
</template>

<script>
    import ThemeSwitcher from './ThemeSwitcher.vue';

    export default {
    name: "ThemeContainer",
    data() {
        return {
            currentTheme: "dark",
        };
    },
    components: { ThemeSwitcher },
    methods: {
        toggleTheme() {
            this.currentTheme = this.currentTheme === 'dark' ? 'light' : 'dark'
        }
    }
}
</script>

<style lang="scss">
    :root.dark {
        --clr-accent: hsl(220, 98%, 61%);
        --clr-hover: hsl(0, 0%, 100%);
        --clr-head: hsl(0, 0%, 96%);

        --clr-line: hsl(233, 14%, 35%);

        --clr-text-task: hsl(0, 0%, 100%);
        --clr-text-task-complete: hsl(233, 14%, 26%);
        --clr-text: hsl(233, 14%, 35%);

        --clr-background-main: hsl(235, 21%, 11%);
        --clr-background-todo: hsl(235, 24%, 19%);
    }

    .dark {
        --clr-accent: hsl(220, 98%, 61%);
        --clr-hover: hsl(0, 0%, 100%);
        --clr-head: hsl(0, 0%, 96%);

        --clr-line: hsl(233, 14%, 35%);

        --clr-text-task: hsl(0, 0%, 100%);
        --clr-text-task-complete: hsl(233, 14%, 26%);
        --clr-text: hsl(233, 14%, 35%);

        --clr-background-main: hsl(235, 21%, 11%);
        --clr-background-todo: hsl(235, 24%, 19%);
    }
</style> -->