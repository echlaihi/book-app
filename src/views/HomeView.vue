<template>

    <section class="container mb-5"> <!-- create book section =============================================================-->
        <div class="row">

          <div class="col-md-6"  v-if="formShowen">
            <BookForm @saveClicked="saveBook"/>
          </div>

          <div class="col-md-6">
              <button class="btn btn-primary" @click="showForm">
                {{ button }}
              </button>
          </div>

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
import BookForm from '@/components/BookForm.vue'

export default {
  name: 'HomeView',
  components: {
    BookCard,
    BookForm

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
      },

      formShowen: false,
      button: "Create a book"
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


    saveBook: function(book){
      var newBook = {
        id: this.books.length,
        title: book.title,
        author: book.author,
        description: book.description
      }

      this.books.push(newBook)
    },

    showForm: function(){
      this.formShowen = !this.formShowen
      this.button == "Remove Form" ? this.button = "Create book" : this.button = "Remove Form"
    }
   

  }

 
}
</script>
