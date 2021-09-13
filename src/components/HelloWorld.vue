<template>
  <div class="hello">
    <div class="container">
      <h1 class="header">Todo List</h1>
      <div class="todo-container">
        <div class="input-container">
          <input type="text" class="input-todo" placeholder="What needs to be done ?" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
.input-todo{
  width: 100%;
  padding: 10px 20px;
  font-size: 18px;
  border: none;
}

</style>
