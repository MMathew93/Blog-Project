<template>
  <div>
    <HeaderComponent />
    <section>
      <div class="columns">
        <div class="column"></div>
        <div class="column is-three-quarters content">
          <article>
            <h1>{{ post.title }}</h1>
            <p>{{ post.text }}</p>
            <p>{{ post.postedDate }}</p>
          </article>
        </div>
        <div class="column"></div>
      </div>
      <b-button> Post a comment! </b-button>
      <div class="commentSection"></div>
    </section>
  </div>
</template>

<script>
import HeaderComponent from "@/components/HeaderComponent";
import axios from "axios";

export default {
  name: "Article",
  props: { id: String },
  components: {
    HeaderComponent
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
}
</style>
