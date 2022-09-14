<template>
  <div class="container">
    <h1>Comentarios</h1>

    <hr />
    <div class="list-group">
      <p v-if="comments.length <= 0">Sem comentarios...</p>

      <div class="list-group-item" v-for="(comment, index) in allComments" v-bind:key="index">
        <span>
          Author: <strong>{{comment.author}}</strong>
        </span>

        <p>{{comment.message}}</p>

        <div>
          <a title="Excluir" v-on:click.prevent="deleteComment(index)">Excluir</a>
        </div>
      </div>
    </div>

    <br>

    <CommentForm v-on:add-comment="addComment" />

    <hr />
  </div>
</template>

<script>
import CommentForm from './CommentForm.vue';

export default {
  components: {
    CommentForm
  },
  data() {
    return {
      comments: []
    };
  },
  methods: {
    addComment(comment) {
      this.comments.push(comment);
    },
    deleteComment(index) {
      this.comments.splice(index, 1);
    }
  },
  computed: {
    allComments() {
      return this.comments.map((comment) => ({
        ...comment,
        author: comment.author.trim() === '' ? 'Anônimo' : comment.author
      }));
    },
  },
  watch: {
    comments(comments) {
      console.log(comments)
    }
  }
};
</script>

<style>

</style>