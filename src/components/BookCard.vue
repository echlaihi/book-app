<template>

    <div class="card">

        <div class="card-head">
            <h5 class="my-2">{{ book.title }}</h5>
        </div>

        <div class="card-body">
            <p>{{ book.description }}</p>
            <p>{{ book.author }}</p>
            <button class="btn btn-danger" @click.prevent="deleteBook">delete book</button>
        </div>


    </div>

</template>

<script>
    export default{
        name: "BookCard",

        props: {
            book: Object
        },

        methods: {
            deleteBook: function(){
                this.$.emit("deleteClicked", this.book.id);
            }
        }
    }
</script>