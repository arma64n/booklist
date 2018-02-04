<template>
  <div>
      <modal v-on:closeModal="closeModal">
        <h5 slot="header" class="modal-title">Add new book</h5>
        <div slot="body">
            <div class="input-group mb-3">
              <input type="text" class="form-control" v-model="newItem.title" placeholder="Title">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" v-model="newItem.author" placeholder="Author">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" v-model="newItem.year" placeholder="Year">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" v-model="newItem.country" placeholder="Country">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" v-model="newItem.pages" placeholder="Pages">
            </div>
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <div class="input-group-text">
                  <input type="checkbox" v-model="newItem.read">
                </div>
              </div>
              <input type="text" class="form-control" :value="newItem.read ? 'Read!': 'Not yeat'" disabled>
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
        title: '',
        author: '',
        year: '',
        country: '',
        pages: '',
        read: ''
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
