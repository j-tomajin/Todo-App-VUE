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
        
        this.tasks.sort((a, b) => a.complete - b.complete)
        this.items = this.tasks.filter((task) => !task.complete).length
        
        this.saveToLocalStorage()
      },
      
      addNewTask(task) {
        this.tasks = [...this.tasks, task]

        this.tasks.sort((a, b) => a.complete - b.complete)
        
        this.items = this.tasks.filter((task) => !task.complete).length
      },
      
      deleteTask(id) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
        this.completedTask = this.completedTask.filter((task) => task.id !== id)
        this.activeTask = this.activeTask.filter((task) => task.id !== id)
        
        this.items = this.tasks.filter((task) => !task.complete).length

        this.saveToLocalStorage()
      },
      
      clearCompleted() {
        this.tasks = this.tasks.filter((task) => !task.complete)
        
        this.items = this.tasks.filter((task) => !task.complete).length
        
        this.completedTask =  this.completedTask.filter((task) => !task.complete)

        this.saveToLocalStorage()
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

      saveToLocalStorage() {
        localStorage.setItem('tasks', JSON.stringify(this.tasks))
        localStorage.setItem('items', this.items)
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
        this.tasks = []

        this.items = this.tasks.length

        this.activeTask = []
        this.completedTask = []

        const prevAllTask = JSON.parse(localStorage.getItem('tasks'))
        const prevItemCount = JSON.parse(localStorage.items || 0)

        if(prevAllTask) {
          this.tasks = prevAllTask
          this.items = prevItemCount
        }
    }
  }
</script>

<template>
  <main class="main">
    <Header 
      text="TODO"
    />
  
    <AddTask
      @new-task="addNewTask"
      @save-to-local-storage="saveToLocalStorage"
    />
  
    <div class="todo-body">
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
    </div>
  </main>
</template>

<style lang="scss" scoped>
  .main {
    padding-block: 2rem;
  }
  
  .todo-body {
    background-color: var(--clr-background-todo);
    padding-top: 1px;
    border-radius: 0 0 8px 8px;
  }
</style>
