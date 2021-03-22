<template>
    <div class="container">
        <h1>Comentários</h1>
        <hr/>
        <FormTodo v-on:add-todo="addComment"></FormTodo>
        <hr/>
        <p v-if="comments.length <= 0">Sem comentários</p>
        <div class="list-group">
            <div class="list-group-item" v-for="(comment, index) in allComments" :key="index">
                <span class="comment__author">Autor: <strong>{{ comment.name }}</strong></span>
                <p>{{ comment.message }}</p>
                <div>
                    <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import FormTodo from './FormTodo'

export default {
    components: {
        FormTodo
    },
    data: function() {
        return {
            comments: []
        }
    },
    methods: {
        removeComment(index) {
            this.comments.splice(index, 1);
        },
        addComment(comment) {
            this.comments.push(comment);
        }
    },
    computed: {
        allComments() {
            return this.comments.map(comment => ({
                ...comment,
                name: comment.name.trim() === '' ? "Anônimo" : comment.name
            }))
        }
    },
    watch: {
        comments(value) {
            console.log(`Value: ${JSON.stringify(value)}`);
        }
    }
}
    
</script>