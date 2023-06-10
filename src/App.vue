<script>
  import Header from './Components/Header.vue';
  import Tasks from './Components/Tasks.vue';
  import AddTask from './Components/AddTask.vue';
  import Footer from './Components/Footer.vue';

  export default {
    name: 'App',
    components: {
      Header,
      Tasks,
      AddTask,
      Footer,
    },
    methods: {
      toggleComplete(id) {
        this.tasks = this.tasks.map((task) => task.id === id ? { ...task, complete: !task.complete } : task)

        this.completedTask = this.completedTask.map((task) => task.id === id ? { ...task, complete: !task.complete } : task)

        this.items = this.tasks.filter((task) => !task.complete).length
        this.tasks.sort((a, b) => a.complete - b.complete)
      },

      addNewTask(task) {
        this.tasks = [...this.tasks, task]

        this.items++
      },

      clearCompleted() {
        this.tasks = this.tasks.filter((task) => !task.complete)

        this.items = this.tasks.length
      },

      showAllTask() {
        this.allTask = !this.allTask
        this.showCompleted = !this.showCompleted
      },

      showCompletedTask() {
        this.showCompleted = !this.showCompleted
        this.allTask = !this.allTask

        this.completedTask =  this.tasks.filter((task) => task.complete)
      },
    },
    data() {
        return {
            tasks: [],
            items: 0,
            allTask: true,
            showCompleted: false,
            completedTask: [],
        }
    },
    created() {
        this.tasks = []

        this.items = this.tasks.length

        this.completedTask = []
    }
  }
</script>

<template>
  <Header />

  <AddTask
    @new-task="addNewTask"
  />

  <Tasks 
    @toggle-complete="toggleComplete"
    :tasks="tasks" 
    :completedTask="completedTask"

    :allTask="allTask"
    :showCompleted="showCompleted"
  />

  <!-- <p>{{ this.tasks.length }} item/s left</p> -->

  <Footer 
    :items="items"
    @clear-completed="clearCompleted" 
    
    @show-all="showAllTask"
    @show-completed="showCompletedTask"
  />
</template>

<style scoped>
</style>
