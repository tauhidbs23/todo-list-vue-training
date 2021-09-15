<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
    <!-- <router-view/> -->
    <div class="container">
      <h1 class="header">Todo List</h1>
      <div class="todo-container">
        <div class="input-container">
          <input
            type="text"
            class="input-todo"
            placeholder="What needs to be done? "
            v-model="item.text"
          />
          <button @click="taskEntry">Add to Task</button>
        </div>
        <Tasks :tasks="tasks" />
        
      </div>
    </div>
  </div>
</template>

<script>
import Tasks from "./components/Tasks.vue";
export default {
  name: "App",
  components: {
    Tasks,
  },
  data() {
    return {
      tasks: [],
      item: {
        id: Math.floor(Math.random() * 100),
        text: "",
        reminder: true,
      },
    };
  },
  methods: {
    taskEntry() {
      this.tasks.push(this.item);
    },
  },
  created() {
    // this.tasks.push(this.item)
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        reminder: true,
      },
      {
        id: 2,
        text: "Meeting at school",
        reminder: true,
      },
    ];
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 22px;
}

.container {
  min-width: 230px;
  max-width: 550px;
  background: #fff;
  margin: 10px 0 40px 0;
  position: relative;
  margin-left: auto;
  margin-right: auto;
}
.header {
  width: 100%;
  font-size: 100px;
  text-align: center;
  color: rgba(175, 47, 47, 0.15);
  text-rendering: optimizeLegibility;
}
.container .todo-container {
  box-shadow: 0 2px 4px 0 rgb(0 0 0 /20%), 0 25px 50px 0 rgb(0 0 0/10%);
}
.input-container {
  padding-right: 40px;
  border-bottom: 1px solid #d3d3d3;
}
.input-todo {
  width: 100%;
  padding: 10px 20px;
  font-size: 18px;
  border: none;
}
</style>
