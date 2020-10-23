<template>
  <div class='list-container'>
    <h1 class='list-title'>{{ title }}</h1>
    <h3 class='list-description'>{{ description }} </h3>
    <div class='task-queue' v-if=tasks.length>
    </div>
    <p v-else><i>No Tasks Yet!</i></p>
  </div>
</template>

<script>
  export default {
    name: 'TaskList',
    props: {
      title: {
        type: String,
        default: 'New Task List'
      }, 
      description: {
        type: String,
        default: 'Add a Description'
      } 
    },
    data: function () {
      return {
        tasks: []
      }
    }
  }
</script>

<style>
.list-container {
  height: 100%;
  min-height: 500px;
  max-width: 350px;
  border-width: 2px;
  border-style: solid;
  border-color: #000000;
}
</style>