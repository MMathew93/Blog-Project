<template>
  <div>
    <HeaderComponent />
    <section>
      <div class="columns">
        <div class="column"></div>
        <div class="column is-three-quarters content">
          <div class="article-box">
            <div :id="`${post._id}`">
              <article class="tile notification">
                <div class="article-content">
                  <h1>{{ post.title }}</h1>
                  <span>{{ formattedDate }}</span>
                  <p>{{ post.text }}</p>
                </div>
                <hr />
                <div class="button-box">
                  <b-button> Post a comment! </b-button>
                </div>
                <div>
                  <CommentsComponent :postId="this.id" />
                </div>
              </article>
            </div>
          </div>
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
import dayjs from "dayjs";

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
    } catch (err) {
      throw new Error(err);
    }
  },
  computed: {
    formattedDate() {
      return dayjs(this.post.postedDate).format("MM/DD/YYYY");
    }
  }
};
</script>

<style>
.article-box {
  width: 100%;
}

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
  justify-content: flex-end;
}
</style>
