<template>
  <div>
      <modal v-on:closeModal="closeModal">
        <h5 slot="header" class="modal-title">Add new book</h5>
        <div slot="body">
            <div class="input-group mb-3">
              <input type="text" class="form-control" placeholder="ISBN" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" placeholder="Title" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" placeholder="Year" aria-label="Username" aria-describedby="basic-addon1">
            </div>
            <div class="input-group mb-3">
              <input type="text" class="form-control" placeholder="Author" aria-label="Username" aria-describedby="basic-addon1">
            </div>
          </div>
        <button slot="footer" type="button" class="btn btn-success">Add book</button>
      </modal>
  </div>
</template>

<script>
import Modal from '@/components/Modal'

export default {
  name: 'Add',
  components: {Modal},
  methods: {
    closeModal () {
      this.$emit('closeModal')
    }
  }
}
</script>
