<template>
  <div class='task-card'>
    <h4 class='card-title' v-if=!editingTitle @click=revealTitle> {{ currentTitle }}</h4>
      <form v-else id='edit-title' @submit=updateTitle>
        <input id='new-title' type='text' :placeholder='currentTitle'>
      </form>
    <p class='card-description' v-if=!editingDescription @click=revealDescription> {{ currentDescrip }} </p>
    <form v-else id='edit-descrip' @submit=updateDescription>
        <input id='new-descrip' type='text' :placeholder='currentDescrip'>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'TaskCard',
    props: {
      baseTitle: {
        type: String,
        default: 'New Task'
      },
      baseDescription: {
        type: String,
        default: 'Describe Me'
      }
    },
    data: function () {
      return {
        title: '',
        editingTitle: false,
        description: '',
        editingDescription: false,
        focused: false
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
  .task-card {
    color: #000000;
    background-color: #ffffff;
    min-height: 150px;
    min-width: 250px;
    border-width: 2px;
    border-radius: 5px;
    border-style: solid;
    border-color: #000000;
    margin-bottom: 20px;
  }
</style>