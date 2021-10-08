<template>
  <div class="container">
    <Header title="Task Tracker" />
    <AddTask @add-task = "addTask" class="collapse" id="collapseExample" />
    <Tasks @togrem="togglerem" @del-task="deltask" :tasks="tasks" />
    <Footer />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import Header from './components/Header.vue'
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
import Footer from "./components/Footer.vue";

export default defineComponent({
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
    Footer
  },

  data() {
    return {
      tasks: [{id:0, text:"Sample Task", day:"Sample", reminder: false}]
    }
  },

  methods: {
    deltask(id: any) {
      if(confirm("Delete task ?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },

    togglerem(id: any) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    },

    addTask(newtask: any) {
      this.tasks.push(newtask);
    }
  },

  // created() {
  //   this.tasks = [
  //     {
  //       id: 1,
  //       text: "Doctors Appointment",
  //       day: "March 5th at 2:30pm",
  //       reminder: true
  //     },

  //     {
  //       id: 2,
  //       text: "Meeting with boss",
  //       day: "March 6th at 1:30pm",
  //       reminder: true
  //     },

  //     {
  //       id: 3,
  //       text: "Food shopping",
  //       day: "March 7th at 2:00pm",
  //       reminder: false
  //     },
  //   ]
  // }

});
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
