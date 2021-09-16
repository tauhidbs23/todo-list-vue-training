<template>
  <div>
    <div class="lower-part">
      <input type="checkbox" v-on:change="$emit('all-selected')" />Check All

      <div>{{ notCom }} Item left</div>
    </div>
    <div class="lower-part">
      <button class="active" @click="$emit('show-all-task')">All</button>
      <button @click="$emit('active-task')">Active</button>
      <button @click="$emit('completed-task')">Completed</button>
    </div>
  </div>
</template>

<script>
export default {
  // count task remainder true
  props: {
    tasks: Array,
    notCom: Number,
  },
};
</script>

<style>
.lower-part {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 16px;
  border-bottom: 1px solid #d3d3d3;
  padding: 10px 20px;
}
button {
  font-size: 14px;
  margin: 0 5px;
  padding: 3px 7px;
  border-radius: 3px;
  cursor: pointer;
  text-decoration: none;
  color: inherit;
}
.active {
  border: 1px solid transparent;
  border-color: rgba(175, 47, 47, 0.2);
}
</style>