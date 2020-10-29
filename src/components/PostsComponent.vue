<template>
  <section class="posts">
    <div class="columns">
      <div class="column"></div>
      <div class="column is-three-quarters content">
        <div class="post-boxes" v-for="post in posts" :key="post._id">
          <div class="post tile notification">
            <h1>{{ post.title }}</h1>
            <p>{{ post.text }}</p>
            <p>{{ post.postedDate }}</p>
          </div>
        </div>
      </div>
      <div class="column"></div>
    </div>
  </section>
</template>

<script>
import axios from "axios";
export default {
  name: "Posts",
  data() {
    return {
      posts: []
    };
  },
  mounted() {
    axios
      .get("http://localhost:3000/posts/published")
      .then(res => {
        this.posts = res.data;
        console.log(res.data);
      })
      .catch(err => {
        console.log(err);
      });
  }
};
</script>

<style>
.post {
  display: flex;
  flex-direction: column;
  margin: 25px;
  background-color: rgb(248 134 36) !important;
}
</style>
