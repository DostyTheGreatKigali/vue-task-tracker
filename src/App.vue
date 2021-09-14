<template>
<div class="container">
<Header title="Task Tracker" />
<AddTask @add-task="addTask" />
<Tasks :tasks="tasks" @delete-task="deleteTask" 
        @toggle-reminder="toggleReminder"
/>
</div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
    Header,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: []
    }
  },
  methods: {
    addTask(task) {
    this.tasks = [...this.tasks, task]
  },
  deleteTask(id) {
    // console.log('task', id)
    if(confirm("Are you sure?")) {
    this.tasks = this.tasks.filter((task) => task.id !== id)
    }
  },
  toggleReminder(id) {
    // console.log('remider', id)
    this.tasks = this.tasks.map((task) => 
    task.id === id ? { ...task, reminder : !task.reminder} : task)
  },
  
}, 
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Buy foodstuffs",
        day: '20th September, 2021 at 10 am',
        reminder: true
      },
      {
        id: 2,
        text: "Visit friends",
        day: '15th October, 2021 at 17: 15 pm',
        reminder: true
      },
      {
        id: 3,
        text: "Go for lab results",
        day: '1st December at 8 am',
        reminder: false
      },
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}

/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
