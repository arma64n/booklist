<template>
  <div class="modal" tabindex="-1" role="dialog" style="display: block">
    <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
      <h5 class="modal-title">
          <slot name="header"></slot>
      </h5>
      <button type="button" class="close" data-dismiss="modal" aria-label="Close" @click="closeModal">
          <span aria-hidden="true">&times;</span>
      </button>
      </div>
      <div class="modal-body">
      <slot name="body"></slot>
      </div>
      <div class="modal-footer">
      <slot name="footer"></slot>
      <button type="button" class="btn btn-secondary" data-dismiss="modal" @click="closeModal">Close</button>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['toggleModal'],
  methods: {
    closeModal () {
      this.$emit('toggleModal')
    }
  }
}
</script>
