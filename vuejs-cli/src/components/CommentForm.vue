<template>
  <div class="comment-form">
    <p>
      <input placeholder="Nome" type="text" name="author" class="form-control" v-model="author">
    </p>

    <p>
      <textarea placeholder="Comentário" name="message" class="form-control" v-model="comment"></textarea>
    </p>

    <button type="submit" class="btn btn-primary" v-on:click="addComment">Comentar</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      author: '',
      comment: '',
    }
  },
  methods: {
    addComment() {
      if (this.comment.trim() === '') {
        return;
      }

      const newComment = {
        author: this.author,
        comment: this.comment,
      };

      this.$emit('add-comment', newComment);

      this.author = '';
      this.comment = '';
    },
  }
}
</script>