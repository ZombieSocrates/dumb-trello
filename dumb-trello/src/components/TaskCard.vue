<template>
  <div class='task-card'>
    <h4 class='card-title'> {{ currentTitle }}</h4>
    <p class='card-description'> {{ currentDescrip }} </p>
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
        description: '',
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