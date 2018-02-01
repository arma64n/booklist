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
          <td>{{book.authors}}</td>
          <td><button type="button" class="btn btn-primary">Edit</button></td>
          <td><button type="button" class="btn btn-danger" @click="deleteItem(index)">Delete</button></td>
        </tr>
      </tbody>
    </table>
    <button type="button" class="btn btn-success">Add new book</button>
    <new-book-form></new-book-form>
    <router-view/>
  </div>
</template>

<script>
import NewBookForm from '@/components/NewBookForm'

export default {
  name: 'App',
  data () {
    return {
      books: [
        {title: 'Lord of The Rings', year: '2002', isbn: '145908562986', authors: 'Tolkien'},
        {title: 'Turkish gambit', year: '2014', isbn: '520239525231', authors: 'Boris Akunin'}
      ]
    }
  },
  methods: {
    deleteItem (index) {
      this.books.splice(index, 1)
    }
  },
  components: { NewBookForm }
}
</script>

<style>

</style>
