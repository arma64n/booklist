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
          <td><button type="button" class="btn btn-primary" @click="clickedEdit(index)">Edit</button></td>
          <td><button type="button" class="btn btn-danger" @click="clickedDelete(index)">Delete</button></td>
        </tr>
      </tbody>
    </table>
    <button type="button" class="btn btn-success" @click="clickedAdd">Add new book</button>
    <transition name="modal">
      <div v-if="visible"
           v-bind:is="currentView"
           v-on:closeModal="toggleModal"
           @addItem="addItem"
           @editItem="editItem"
           @deleteItem="deleteItem"
           :clickedItem="clickedItem"></div>
    </transition>
  </div>
</template>

<script>
import Add from '@/components/Add'
import Edit from '@/components/Edit'
import Delete from '@/components/Delete'

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
      currentView: '',
      visible: false,
      clickedIndex: '',
      clickedItem: {
        isbn: '',
        title: '',
        year: '',
        author: ''
      }
    }
  },
  methods: {
    toggleModal () {
      this.visible = !this.visible
    },
    clickedAdd () {
      this.currentView = 'add'
      this.toggleModal()
    },
    clickedEdit (index) {
      this.currentView = 'edit'
      this.toggleModal()
      this.clickedIndex = index
      this.clickedItem.isbn = this.books[index].isbn
      this.clickedItem.title = this.books[index].title
      this.clickedItem.year = this.books[index].year
      this.clickedItem.author = this.books[index].author
    },
    clickedDelete (index) {
      this.currentView = 'delete'
      this.toggleModal()
      this.clickedIndex = index
    },
    addItem (item) {
      this.books.push(item)
      this.toggleModal()
    },
    editItem (item) {
      this.books.splice(this.clickedIndex, 1, item)
      this.toggleModal()
    },
    deleteItem () {
      this.books.splice(this.clickedIndex, 1)
      this.toggleModal()
    }
  },
  components: { Add, Edit, Delete }
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
