<template>
  <div>
    <HeaderComponent />
    <section>
      <div class="columns">
        <div class="column"></div>
        <div class="column is-three-quarters content">
          <article>
            <div class="article-content">
              <h1>{{ post.title }}</h1>
              <p>{{ post.postedDate }}</p>
              <p>{{ post.text }}</p>
            </div>
            <hr />
            <div class="button-box">
              <b-button> Post a comment! </b-button>
            </div>
            <CommentsComponent :postId="this.id" />
          </article>
        </div>
        <div class="column"></div>
      </div>
    </section>
  </div>
</template>

<script>
import HeaderComponent from "@/components/HeaderComponent";
import CommentsComponent from "@/components/CommentsComponent";
import axios from "axios";

export default {
  name: "Article",
  props: { id: String },
  components: {
    HeaderComponent,
    CommentsComponent
  },
  data() {
    return {
      post: ""
    };
  },
  async mounted() {
    try {
      const res = await axios.get("http://localhost:3000/posts/" + this.id);
      this.post = res.data;
      console.log(this.post)
    } catch (err) {
      throw new Error(err);
    }
  }
};
</script>

<style>
article {
  display: flex;
  flex-direction: column;
  margin: 25px;
  background-color: rgb(248 134 36) !important;
  max-width: 100%;
  padding: 5rem;
}

.article-content {
  text-align: left;
}

.button-box {
  display: flex;
  justify-content: end;
}
</style>
