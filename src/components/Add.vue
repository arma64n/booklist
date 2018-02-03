<template>
  <div>
      <modal v-on:closeModal="closeModal">
        <h5 slot="header" class="modal-title">Add new book</h5>
        <div slot="body">
            <div class="input-group mb-3">
              <input type="text" class="form-control" v-model="newItem.isbn" placeholder="ISBN" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" v-model="newItem.title" placeholder="Title" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" v-model="newItem.year" placeholder="Year" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" v-model="newItem.author" placeholder="Author" aria-label="Username" aria-describedby="basic-addon1">
            </div>
          </div>
        <button slot="footer" type="button" class="btn btn-success" @click="addItem">Add book</button>
      </modal>
  </div>
</template>

<script>
import Modal from '@/components/Modal'

export default {
  name: 'Add',
  components: {Modal},
  data () {
    return {
      newItem: {
        isbn: '',
        title: '',
        year: '',
        author: ''
      }
    }
  },
  methods: {
    closeModal () {
      this.$emit('closeModal')
    },
    addItem () {
      this.$emit('addItem', this.newItem)
    }
  }
}
</script>
