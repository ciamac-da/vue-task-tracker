<template>
<div class="container">
<!--Toogle add task event! -->
<Header
@toggle-add-task="toggleAddTask"
title="Task Tracker" 
:showAddTask="showAddTask"
/>
<!---->
<div v-show="showAddTask">
<AddTask @add-task="addTask" />
</div>
<!--Toggle true/false the reminder-->
<!--Delete Task event-->
<Tasks 
@toggle-reminder="toggleReminder" 
@delete-task="deleteTask" 
:tasks="tasks"
/>
</div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

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
    // We loop through ids and filter the Id that we clicked on! 
    deleteTask(id) {
    if(confirm("Are you sure?")) {
      this.tasks = this.tasks.filter((task) => task.id !== id) 
    }
    },
    // Map through tasks and first of all we make a copy of previous tasks and set the reminder to opposite of what reminder is
    // So if ots  false we switch it to true if its false we switch it to true! 
    toggleReminder(id) {
     this.tasks = this.tasks.map((task)=> {
      return task.id === id ? {...task, reminder: !task.reminder} : task
     })
    },
  },
  created() {
    // Dummy tasks !!!
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        day: "March 1st at 2:30pm",
        reminder: true
      },
      {
        id: 2,
        text: "Gym",
        day: "March 11st at 2:30pm",
        reminder: true
      },
      {
        id: 3,
        text: "Meeting",
        day: "March 2st at 2:30pm",
        reminder: false
      }
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
  font-family: 'Ubuntu', sans-serif !important;
  background: gray;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 5px solid green;
  padding: 30px;
  border-radius: 10px;
  background: white;
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