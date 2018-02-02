<template>
  <div class="modal" tabindex="-1" role="dialog" style="display: block">
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Add new book</h5>
          <button type="button" class="close" data-dismiss="modal" aria-label="Close" @click="closeModalEdit">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">
          <div class="input-group mb-3">
            <input type="text" class="form-control" :value="books[passedIndex].isbn" placeholder="ISBN" aria-label="Username" aria-describedby="basic-addon1">
          </div>
          <div class="input-group mb-3">
            <input type="text" class="form-control" :value="books[passedIndex].title" placeholder="Title" aria-label="Username" aria-describedby="basic-addon1">
          </div>
          <div class="input-group mb-3">
            <input type="text" class="form-control" :value="books[passedIndex].year" placeholder="Year" aria-label="Username" aria-describedby="basic-addon1">
          </div>
          <div class="input-group mb-3">
            <input type="text" class="form-control" :value="books[passedIndex].author" placeholder="Author" aria-label="Username" aria-describedby="basic-addon1">
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-primary" @click="saveNew">Save changes</button>
          <button type="button" class="btn btn-secondary" data-dismiss="modal" @click="closeModalEdit">Close</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'EditItem',
  props: ['passedIndex', 'books'],
  data () {
    return {
      newBook: {}
    }
  },
  methods: {
    saveNew () {
      this.$emit('saveNew', this.newBook)
      this.newBook = {}
    },
    closeModalEdit () {
      this.$emit('closeModalEdit')
    }
  }
}
</script>