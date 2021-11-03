<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Daily Task App" 
      :showAddTask="showAddTask"
    />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
  <!-- <HelloWorld msg="Daily Task App"/> -->
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: [],
      // use lifecycle method to hook - created()
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      // console.log('task', id)
      if (confirm('are you sure to want to delete this tasK?')) {
        this.tasks = this.tasks.filter(() => task.id !== id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task
      )
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Eye Follow-up',
        day: 'Mon Nov 1 at 4:30pm',
        reminder: false,
      },
      {
        id: 2,
        text: 'Vivosun Tent - Garden Grove',
        day: 'Tues Nov 2 at 12pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'Bipen & Ghost - Long Beach',
        day: 'Wed Nov 3 at 2pm',
        reminder: true,
      },
      {
        id: 4,
        text: 'Milsbo & Plants - Thousand Oaks',
        day: 'Thurs Nov 4 at 11am',
        reminder: true,
      },
      {
        id: 5,
        text: 'Monstera Esquelito Node - Westminster',
        day: 'Sat Nov 6 at 9am',
        reminder: false,
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
</style>
