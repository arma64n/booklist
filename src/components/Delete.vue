<template>
  <div>
    <modal v-on:closeModal="closeModal">
      <h5 slot="header" class="modal-title">Delete item?</h5>
      <p slot="body">The book will be permanently removed</p>
      <button slot="footer" type="button" class="btn btn-danger" @click="deleteItem">Delete</button>
    </modal>
  </div>
</template>

<script>
import Modal from '@/components/Modal'

export default {
  name: 'Delete',
  components: {Modal},
  props: ['index'],
  methods: {
    closeModal () {
      this.$emit('closeModal')
    },
    deleteItem () {
      this.$emit('deleteItem', this.index)
    }
  }
}
</script>
