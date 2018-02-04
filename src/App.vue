<template>
  <div id="app" class="container">
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Title</th>
          <th scope="col">Author</th>
          <th scope="col">Year</th>
          <th scope="col">Country</th>
          <th scope="col">Pages</th>
          <th scope="col">Read</th>
          <th scope="col"></th>
          <th scope="col"></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(book, index) in books" :key="book.id">
          <td>{{book.title}}</td>
          <td>{{book.author}}</td>
          <td>{{book.year}}</td>
          <td>{{book.country}}</td>
          <td>{{book.pages}}</td>
          <td>{{book.read ? 'Read!' : ''}}</td>
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
      books: [],
      currentView: '',
      visible: false,
      clickedIndex: '',
      clickedItem: {
        title: '',
        author: '',
        year: '',
        country: '',
        pages: '',
        read: ''
      }
    }
  },
  created () {
    fetch('https://my-json-server.typicode.com/arma64n/demo/books')
      .then(response => response.json())
      .then(json => {
        this.books = json
      })
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
      this.clickedItem.title = this.books[index].title
      this.clickedItem.author = this.books[index].author
      this.clickedItem.year = this.books[index].year
      this.clickedItem.country = this.books[index].country
      this.clickedItem.pages = this.books[index].pages
      this.clickedItem.read = this.books[index].read
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
