<template>
  <div class="container">
    <b-button v-b-modal.header>
      Insert New To-Do-List
    </b-button>

    <b-modal id="header" title="Note Title" @ok="insertToDo">
      <b-form-input v-model="title" placeholder="Insert title here..." />
      <hr>
      <b-row>
        <b-col sm="11" offset="1">
          <b-form-input v-for="detail in details" :key="detail" v-model="detail.todo" placeholder="Insert to do here..." />
          <b-button size="sm" @click="addDetails">
            Add
          </b-button>
        </b-col>
      </b-row>
    </b-modal>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title: '',
      details: [
        {
          todo: ''
        }
      ]
    }
  },
  methods: {
    addDetails () {
      this.details.push({ todo: '' })
    },
    insertToDo () {
      this.$axios.$post('/note', { title: this.title }).then((data) => {
        alert(data.id)
      })
    }
  }
}
</script>

<style>

</style>
