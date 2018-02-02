<template>
  <div id="app" class="container">
    <table class="table">
      <thead>
        <tr>
          <th scope="col">ISBN</th>
          <th scope="col">Title</th>
          <th scope="col">Year</th>
          <th scope="col">Authors</th>
          <th scope="col"></th>
          <th scope="col"></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(book, index) in books" :key="book.id">
          <td>{{book.isbn}}</td>
          <td>{{book.title}}</td>
          <td>{{book.year}}</td>
          <td>{{book.author}}</td>
          <td><button type="button" class="btn btn-primary" @click="toggleModal(index)">Edit</button></td>
          <td><button type="button" class="btn btn-danger" @click="toggleModal(index)">Delete</button></td>
        </tr>
      </tbody>
    </table>
    <button type="button" class="btn btn-success" @click="toggleModal">Add new book</button>
    <transition name="modal">
      <modal v-if="visible"
             v-on:toggleModal="toggleModal">
      </modal>
    </transition>
  </div>
</template>

<script>
import Modal from '@/components/Modal'

export default {
  name: 'App',
  data () {
    return {
      books: [
        {title: 'Lord of The Rings', year: '2002', isbn: '145908562986', author: 'Tolkien'},
        {title: 'Turkish gambit', year: '2014', isbn: '520239525231', author: 'Boris Akunin'},
        {title: 'Batman', year: '2006', isbn: '3453463437', author: 'DC'},
        {title: 'Superman', year: '1986', isbn: '7554754548548', author: 'Marvel'}
      ],
      visible: false,
      currentView: ''
    }
  },
  methods: {
    toggleModal () {
      this.visible = !this.visible
    }
  },
  components: { Modal }
}
</script>

<style>
.modal-enter-active, .modal-leave-active {
  transition: opacity .5s;
}
.modal-enter, .modal-leave-to {
  opacity: 0;
}
.modal {
  background: rgba(0,0,0,0.5)
}
</style>
