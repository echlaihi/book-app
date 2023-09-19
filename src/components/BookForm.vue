<template>
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
                  <button class="form-control btn btn-primary" @click.prevent="clickSave">Save</button>
                </fieldset>

    </form>
</template>

<script>
export default{

    name: "BookForm",

    data: function(){
        return {
            book: {
                title: "",
                author: "",
                description: ""
            }
        }
    },


    methods: {
        clickSave: function(){
            this.$.emit("saveClicked", this.book);
        }
    }
}
</script>