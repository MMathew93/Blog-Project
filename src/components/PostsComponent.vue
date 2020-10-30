<template>
  <section>
    <div class="columns">
      <div class="column"></div>
      <div class="column is-three-quarters content">
        <div class="post-boxes" v-for="post in posts" :key="post._id">
          <div :id="`${post._id}`" class="article">
            <div class="post tile notification">
              <h1>{{ post.title }}</h1>
              <p>{{ post.text }}</p>
              <p>{{ post.postedDate }}</p>
              <ReadMoreComponent :postId="post._id" />
            </div>
          </div>
        </div>
      </div>
      <div class="column"></div>
    </div>
  </section>
</template>

<script>
import axios from "axios";
import ReadMoreComponent from "@/components/ReadMoreComponent";
import dayjs from "dayjs";

export default {
  name: "PostsComponent",
  components: {
    ReadMoreComponent
  },
  data() {
    return {
      posts: []
    };
  },
  async mounted() {
    try {
      const res = await axios.get("http://localhost:3000/posts/published");
      this.formatDate(res.data);
      this.posts = res.data;
    } catch (err) {
      throw new Error(err);
    }
  },
  methods: {
    formatDate(dataArr) {
      if (dataArr instanceof Array) {
        dataArr.forEach(data => {
          if (data.postedDate) {
            return (data.postedDate = dayjs(data.postedDate).format(
              "MM/DD/YYYY"
            ));
          }
        });
      }
    }
  }
};
</script>

<style>
.post-boxes {
  width: 100%;
}

.article {
  position: relative;
}

.post {
  display: flex;
  flex-direction: column;
  margin: 25px;
  background-color: rgb(248 134 36) !important;
  max-width: 100%;
}
</style>
