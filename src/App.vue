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

        this.activeTask = this.activeTask.map((task) => task.id === id ? { ...task, complete: !task.complete } : task)

        this.items = this.tasks.filter((task) => !task.complete).length
        this.tasks.sort((a, b) => a.complete - b.complete)
      },

      addNewTask(task) {
        this.tasks = [...this.tasks, task]

        this.items = this.tasks.filter((task) => !task.complete).length
      },

      deleteTask(id) {
          this.tasks = this.tasks.filter((task) => task.id !== id)
          this.completedTask = this.completedTask.filter((task) => task.id !== id)
          this.activeTask = this.activeTask.filter((task) => task.id !== id)

          this.items = this.tasks.filter((task) => !task.complete).length
      },

      clearCompleted() {
        this.tasks = this.tasks.filter((task) => !task.complete)

        this.items = this.tasks.filter((task) => !task.complete).length
        
        this.completedTask =  this.completedTask.filter((task) => !task.complete)
      },

      // FOOTER FUNCTIONS
      showAllTask() {
        this.allTask = true
        this.showActive = false
        this.showCompleted = false
      },
      
      showActiveTask() {
        this.allTask = false
        this.showActive = true
        this.showCompleted = false

        this.activeTask = this.tasks.filter((task) => !task.complete)
      },
      
      showCompletedTask() {
        this.allTask = false
        this.showActive = false
        this.showCompleted = true

        this.completedTask =  this.tasks.filter((task) => task.complete)
      },
    },
    data() {
        return {
            tasks: [],
            items: 0,
            allTask: true,
            showActive: false,
            showCompleted: false,
            activeTask: [],
            completedTask: [],
        }
    },
    created() {
        this.tasks = [
          // {
          //   id: 1,
          //   text: 'Test',
          //   complete: false,
          // },
          // {
          //   id: 2,
          //   text: 'Test 2',
          //   complete: true,
          // },
        ]

        this.items = this.tasks.length

        this.activeTask = []
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
    :activeTask="activeTask"

    @delete-task="deleteTask"

    :allTask="allTask"
    :showActive="showActive"
    :showCompleted="showCompleted"
  />

  <!-- <p>{{ this.tasks.length }} item/s left</p> -->

  <Footer 
    :items="items"
    @clear-completed="clearCompleted" 
    
    @show-all="showAllTask"
    @show-active="showActiveTask"
    @show-completed="showCompletedTask"

    :allTask="allTask"
    :showActive="showActive"
    :showCompleted="showCompleted"
  />
</template>

<style scoped>
</style>
