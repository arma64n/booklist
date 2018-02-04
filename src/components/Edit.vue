<template>
  <div>
      <modal v-on:closeModal="closeModal">
        <h5 slot="header" class="modal-title">Edit book</h5>
        <div slot="body">
            <div class="input-group mb-3">
              <input type="text" class="form-control" :value="clickedItem.title" @input="editedItem.title = $event.target.value" placeholder="Title" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" :value="clickedItem.author" @input="editedItem.author = $event.target.value" placeholder="Author" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" :value="clickedItem.year" @input="editedItem.year = $event.target.value" placeholder="Year" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" :value="clickedItem.country" @input="editedItem.country = $event.target.value" placeholder="Year" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" :value="clickedItem.pages" @input="editedItem.pages = $event.target.value" placeholder="Year" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <div class="input-group-text">
                  <input type="checkbox" id="illustrated" v-model="clickedItem.read" @change="editedItem.read = !editedItem.read" aria-label="Checkbox for following text input">
                </div>
              </div>
              <input type="text" class="form-control" :value="clickedItem.read ? 'Read!': 'Not yet'" aria-label="Text input with checkbox" disabled>
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
        title: this.clickedItem.title,
        author: this.clickedItem.author,
        year: this.clickedItem.year,
        country: this.clickedItem.country,
        pages: this.clickedItem.pages,
        read: this.clickedItem.read
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
