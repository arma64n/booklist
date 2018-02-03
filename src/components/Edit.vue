<template>
  <div>
      <modal v-on:closeModal="closeModal">
        <h5 slot="header" class="modal-title">Edit book</h5>
        <div slot="body">
            <div class="input-group mb-3">
              <input type="text" class="form-control" :value="clickedItem.isbn" @input="editedItem.isbn = $event.target.value" placeholder="ISBN" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" :value="clickedItem.title" @input="editedItem.title = $event.target.value" placeholder="Title" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" :value="clickedItem.year" @input="editedItem.year = $event.target.value" placeholder="Year" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" :value="clickedItem.author" @input="editedItem.author = $event.target.value" placeholder="Author" aria-label="Username" aria-describedby="basic-addon1">
            </div>
          </div>
        <button slot="footer" type="button" class="btn btn-primary" @click="editItem">Save changes</button>
      </modal>
  </div>
</template>

<script>
import Modal from '@/components/Modal'

export default {
  name: 'Edit',
  components: {Modal},
  props: ['clickedItem'],
  data () {
    return {
      editedItem: {
        isbn: this.clickedItem.isbn,
        title: this.clickedItem.title,
        year: this.clickedItem.year,
        author: this.clickedItem.author
      }
    }
  },
  methods: {
    editItem () {
      this.$emit('editItem', this.editedItem)
    },
    closeModal () {
      this.$emit('closeModal')
    }
  }
}
</script>
