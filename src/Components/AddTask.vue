<template>
    <form @submit="newTask" class="form">
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

        background-color: rgb(143, 143, 143);
        padding: 40px 8px;
        border-radius: 8px;

        margin-bottom: 24px;
    }

    .new-task {
        width: 100%;
    }

    .submit-btn {
        background-color: hsl(120, 51%, 41%);
        color: white;
        font-weight: bold;
        cursor: pointer;
    }

    .new-task, .submit-btn {
        outline: 0;
        border: none;
        padding: 12px 16px;
        border-radius: 4px;
    }
</style>