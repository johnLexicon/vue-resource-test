<template>
  <div class="container-fluid container-md my-5">
    <div v-if="posts" class="m-auto">
      <div v-for="post in posts" :key="post.id" class="card mb-3">
        <div class="card-header">Id: {{ post.id }}</div>
        <div class="card-body">
          <h5 class="card-title">{{ post.title }}</h5>
          <p class="card-text">
            {{ post.body }}
          </p>
          <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      posts: null,
    };
  },
  created() {
    this.$http
      .get("https://jsonplaceholder.typicode.com/posts/")
      .then((response) => {
        this.posts = response.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>
