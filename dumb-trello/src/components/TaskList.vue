<template>
  <div class='list-container'>
    <h1 class='list-title'>{{ currentTitle }}</h1>
    <h3 class='list-description'>{{ currentDescrip }} </h3>
    <div class='task-container' v-if=tasks.length>
    </div>
    <p v-else><i>No Tasks Yet!</i></p>
  <button class='task-button'>Add Another Task</button>
  </div>
</template>

<script>
  export default {
    name: 'TaskList',
    props: {
      baseTitle: {
        type: String,
        default: 'New Task List'
      }, 
      baseDescription: {
        type: String,
        default: 'Add a Description'
      } 
    },
    data: function () {
      return {
        tasks: [],
        title: '',
        description: ''
      }
    },
    computed: {
      currentTitle: function () {
        if (this.title === '') {
          return this.baseTitle
        }
        return this.title
      },
      currentDescrip: function () {
        if (this.description === '') {
          return this.baseDescription
        }
        return this.description
      }
    }
  }
</script>

<style>
.list-container {
  height: 100%;
  position: relative;
  min-height: 750px;
  max-width: 350px;
  border-width: 2px;
  border-style: solid;
  border-color: #000000;
}

.list-title:hover {
  cursor: pointer;
}

.list-description:hover {
  cursor: pointer;
}

.task-button {
  position: absolute;
  bottom: 10px;
  background-color: #A9A9A9;
  color: #FFFFFF;
}
</style>