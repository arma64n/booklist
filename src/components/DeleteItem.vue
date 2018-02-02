<template>
  <div class="modal" tabindex="-1" role="dialog" style="display: block">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">Delete Item?</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close" @click="closeModalDelete">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-danger" @click="deleteItem">Delete</button>
        <button type="button" class="btn btn-secondary" data-dismiss="modal" @click="closeModalDelete">Close</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'DeleteItem',
  props: ['passedIndex'],
  methods: {
    deleteItem (passedIndex) {
      this.$emit('deleteItem', this.passedIndex)
    },
    closeModalDelete () {
      this.$emit('closeModalDelete')
    }
  }
}
</script>