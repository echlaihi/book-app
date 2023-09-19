<template>

    <section class="container mb-5"> <!-- create book section =============================================================-->
        <div class="row">
<!-- 
          <div class="col-md-6">
             <form class="border p-4">
                <h3>Add book</h3>
                <fieldset class="form-group">
                  <label class="d-block text-start mt-4 mb-2"><b>Title: </b></label>
                  <input type="text" class="form-control" v-model="book.title">
                </fieldset>

                <fieldset>
                  <label class="d-block text-start mt-4 mb-2"><b>Author: </b></label>
                  <input type="text" class="form-control" v-model="book.author">
                </fieldset>

                <fieldset>
                  <label class="d-block text-start mt-4 mb-2"><b>Description: </b></label>
                  <input type="text" class="form-control" v-model="book.description">
                </fieldset>

                <fieldset class="form-group mt-4">
                  <button class="form-control btn btn-primary" @click.prevent="saveBook">Save</button>
                </fieldset>

             </form>
          </div> -->

        </div>
    </section><!-- end create book section ==========================================================================-->


    <section class="container"> <!-- books section ===================================================================-->

          <div class="row" v-if="thereAreBooks">
                <div class="col-md-4" v-for="book in books" :key="book.id">
                  <BookCard :book="book" @deleteClicked="deleteBook"/>
                </div>
          </div>

              <div v-else class="alert alert-danger">there are no books!</div>

    </section><!-- end books section ================================================================================-->

</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import BookCard from '@/components/BookCard.vue'

export default {
  name: 'HomeView',
  components: {
    BookCard
    // HelloWorld

  },

  data: function(){
    return {
      books: [
        {
          id: 0, 
          title: "book title",
          description: "book description",
          author: "book author"
        },

        {
          id: ``, 
          title: "book 1 title",
          description: "book 1 description",
          author: "book 1 author"
        }
      ],

      book: {
        title: "",
        author: "",
        description: ""
      }
    }
  },

  computed: {
    thereAreBooks: function(){
      return (this.books.length != 0)
    }
  },

  methods: {

    deleteBook: function(id)
    {
      if (id == this.book.length - 1) {
        this.books.pop()
      } else {

            for (var i = id; i < this.books.length - 1; i++)
          {

            this.books[i] = this.books[i + 1]

          }

          this.books.pop()

      }
     
    },

    saveBook: function(){
      var newBook = {
        id: this.books.length,
        title: this.title,
        author: this.author,
        description: this.description
      }

      // this.books.push(newBook)
      console.log(newBook)
    }
   

  }

 
}
</script>
