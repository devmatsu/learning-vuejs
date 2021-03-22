<template>
    <div>
        <div class="form-todo form-group">
            <p>
                <input type="text" placeholder="Nome" class="form-control" v-model="name">
            </p>
            <p>
                <textarea name="message" placeholder="Comentário" class="form-control" v-model="message"></textarea>
            </p>
            <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
        </div>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            comments: [],
            name: "",
            message: ""
        }
    },
    methods: {
        addComment() {
            console.log(`Name: ${this.name} || Message: ${this.message}`)
            if(this.message.trim() === "") {
                console.log("The message is empty.")
                return;
            }

            this.$emit('add-todo', {
                name: this.name,
                message: this.message
            })

            this.name = '';
            this.message = '';
        }
    }
}
</script>