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
          <!--<td><button type="button" class="btn btn-primary" @click="editItem(index)">Edit</button></td>-->
          <td><button type="button" class="btn btn-danger" @click="deleteItem(index)">Delete</button></td>
        </tr>
      </tbody>
    </table>
    <button type="button" class="btn btn-success" @click="visibleNew = true">Add new book</button>
    <transition name="modal">
      <new-book-form v-if="visibleNew" v-on:closeModalNew="closeModalNew" v-on:saveNew="saveNew"></new-book-form>
    </transition>
    <!--<edit-book-form
      v-if="visible"
      :selectedBook="selectedBook"
      v-on:saveEdit="newBookValue">
    </edit-book-form> -->
  </div>
</template>

<script>
import NewBookForm from '@/components/NewBookForm'
import EditBookForm from '@/components/EditBookForm'

export default {
  name: 'App',
  data () {
    return {
      books: [
        {title: 'Lord of The Rings', year: '2002', isbn: '145908562986', author: 'Tolkien'},
        {title: 'Turkish gambit', year: '2014', isbn: '520239525231', author: 'Boris Akunin'}
      ],
      selectedBook: null,
      visible: false,
      visibleNew: false
    }
  },
  methods: {
    deleteItem (index) {
      this.books.splice(index, 1)
    },
    editItem (index) {
      this.visible = true
      this.selectedBook = this.books[index]
    },
    newBookValue (value) {
      this.books.push(value)
    },
    saveNew (value) {
      this.books.push(value)
    },
    closeModalNew () {
      this.visibleNew = false
    }
  },
  components: { NewBookForm, EditBookForm }
}
</script>

<style>
.modal-enter-active, .modal-leave-active {
  transition: opacity .5s;
}
.modal-enter, .modal-leave-to {
  opacity: 0;
}
</style>
