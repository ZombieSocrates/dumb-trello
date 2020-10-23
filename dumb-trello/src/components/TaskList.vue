<template>
  <div class='list-container'>
    <h1 class='list-title' v-if=!editingTitle @click=revealTitle>{{ currentTitle }}</h1>
      <form v-else id='edit-title' @submit=updateTitle>
        <input id='new-title' type='text' :placeholder='currentTitle'>
      </form>
    <h3 class='list-description' v-if=!editingDescription @click=revealDescription>{{ currentDescrip }}</h3>
      <form v-else id='edit-descrip' @submit=updateDescription>
        <input id='new-descrip' type='text' :placeholder='currentDescrip'>
      </form>
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
        editingTitle: false,
        description: '',
        editingDescription: false
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
    },
    methods: {
      revealTitle: function () {
        this.editingTitle = true
      },
      updateTitle: function () {
        const newTitle = document.getElementById('new-title').value
        this.title = newTitle
        this.editingTitle = false
      },
      revealDescription: function () {
        this.editingDescription = true
      },
      updateDescription: function () {
        const newDescrip = document.getElementById('new-descrip').value
        this.description = newDescrip
        this.editingDescription = false
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