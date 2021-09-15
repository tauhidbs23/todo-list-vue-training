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
            @keyup.enter="addTask"
          />
        </div>
        <Tasks :tasks="tasks" @delete-task="deleteTask" />
        <Footer v-if="tasks.length > 0" />
      </div>
    </div>
  </div>
</template>

<script>
import Tasks from "./components/Tasks.vue";
import Footer from "./components/Footer.vue";
export default {
  name: "App",
  components: {
    Tasks,
    Footer,
  },
  data() {
    return {
      tasks: [],
      item: {
        id: "",
        text: "",
        reminder: true,
      },
    };
  },
  methods: {
    addTask(e) {
      e.preventDefault();

      if (!this.item.text) {
        console.log("please add a task");
        return;
      }
      const newTask = {
        id: Math.floor(Math.random() * 1000),
        text: this.item.text,
        reminder: this.item.reminder,
      };

      console.log(newTask);

      this.tasks = [...this.tasks, newTask];

      this.item.text = "";
      this.item.id = "";
      this.item.reminder = true;
    },
    deleteTask(id) {
      console.log("from app.vue ->", id);
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
  },
  emits: ["delete-task"],
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
