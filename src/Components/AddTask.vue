<template>
    <form 
        @submit="newTask" 
        class="form"
    >
        <input 
            v-model="text"
            name="text"
            type="text"
            placeholder="e.g Edit a video"
            class="new-task"
        >
        <input 
            type="submit"
            class="submit-btn"
            >
    </form>
</template>

<script>
    export default {
        name: 'AddTask',
        data() {
            return {
                text: '',
                complete: false,
            }
        },
        methods: {
            newTask(e) {
                e.preventDefault()

                if(!this.text) {
                    alert('You can\'t submit blank task...')
                    return
                }

                const newTask = {
                    id: Math.floor(Math.random() * 1000000),
                    text: this.text,
                    complete: this.complete,
                }

                this.$emit('new-task', newTask)

                this.text = ''
                this.complete = false

                this.$emit('save-to-local-storage')
            }
        }
    }
</script>

<style lang="scss" scoped>
    .form {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 4px;

        margin-block: 2rem 1.5rem;
        border-radius: 8px;
    }

    .new-task {
        width: 100%;
        background-color: var(--clr-background-todo);
        color: var(--clr-text-task);
        border-top-left-radius: 8px;
        padding: 16px 20px;
    }
    
    .submit-btn {
        background-color: hsl(128, 100%, 51%);
        color: white;
        font-family: inherit;
        font-weight: bold;
        border-top-right-radius: 8px;
        padding: 17px 20px;
        
        cursor: pointer;
    }
    
    .new-task, .submit-btn {
        outline: 0;
        border: none;
        font-size: inherit;
    }
</style>