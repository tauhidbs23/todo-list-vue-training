<template>
  <div>
    <div :key="task.id" v-for="task in tasks">
      <div class="todo-item">
        <div class="todo-item-left">
          <input type="checkbox" :checked="task.completed" v-on:change="$emit('update-check',task.id)" />
          <!-- <input type="checkbox" v-if="task.completed == false" /> -->
          <!-- <div class="todo-item-label">{{ task.text }}</div>
          <div class="todo-item-label">{{ task.text }}</div> -->
          <strike class="todo-item-label" v-if="task.completed">{{ task.text }}</strike>
          <span class="todo-item-label" v-else>{{ task.text }}</span>
        </div>
        <div class="remove-item" @click="$emit('delete-task', task.id)">x</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
};
</script>

<style>
.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 20px;
  border-bottom: 1px solid #d3d3d3;
}
.todo-item-left {
  display: flex;
  align-items: center;
}
input[type="checkbox" i] {
  background: initial;
  cursor: default;
  appearance: auto;
  box-sizing: border-box;
  margin: 3px 3px 3px 4px;
  padding: initial;
  border: initial;
}
.todo-item-label {
  margin-left: 12px;
}
.remove-item {
  cursor: pointer;
  color: black;
}
</style>