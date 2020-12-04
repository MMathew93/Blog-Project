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
                  <div v-html="post.text">}</div>
                </div>
                <hr />
                <div class="button-box">
                  <b-button @click="toggle = !toggle" :disabled="toggle">
                    Post a comment!
                  </b-button>
                </div>
                <div v-if="toggle" class="postcomment">
                  <CommentModal :postId="this.id" @cancelled="childEvent" />
                </div>
                <CommentsComponent :postId="this.id" />
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
import CommentModal from "@/components/CommentModal";
import axios from "axios";
import dayjs from "dayjs";

export default {
  name: "Article",
  props: { id: String },
  components: {
    HeaderComponent,
    CommentsComponent,
    CommentModal
  },
  data() {
    return {
      post: "",
      toggle: false
    };
  },
  async mounted() {
    try {
      const res = await axios.get(
        "https://my-personal-blog-api.herokuapp.com/posts/" + this.id
      );
      this.post = res.data;
    } catch (err) {
      throw new Error(err);
    }
  },
  computed: {
    formattedDate() {
      return dayjs(this.post.postedDate).format("MM/DD/YYYY");
    }
  },
  methods: {
    childEvent: function() {
      this.toggle = false;
    }
  }
};
</script>

<style>
.article-box {
  width: 100%;
}

h1 {
  color: black !important;
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
  color: black;
}

.button-box {
  display: flex;
  justify-content: flex-end;
}

.postcomment {
  background-color: rgb(30, 30, 30);
  text-align: left;
  padding: 1.5rem;
  font-size: 18px;
  border-radius: 4px;
}
</style>
