<template>
  <section>
    <div class="commentSection">
      <div class="comment-boxes" v-for="comment in comments" :key="comment._id">
        <div :id="`${comment._id}`">
          <div class="commentInfo">
            <p>{{ comment.username }}</p>
            <i class="fas fa-circle"></i>
            <p>{{ comment.postedDate }}</p>
          </div>
          <div class="commentText">
            <p>{{ comment.text }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from "axios";

export default {
  name: "CommentsComponents",
  props: ["postId"],
  data() {
    return {
      comments: []
    };
  },
  async mounted() {
    try {
      const res = await axios.get(
        "http://localhost:3000/posts/" + this.postId + "/comments"
      );
      this.comments = res.data;
    } catch (err) {
      throw new Error(err);
    }
  }
};
</script>

<style>
.comment-boxes {
  margin: 25px;
  background-color: rgb(67, 70, 75);
  text-align: left;
  padding: 1.5rem;
  font-size: 18px;
  border-radius: 4px;
}

.commentInfo,
.commentText {
  display: flex;
  align-items: center;
  margin: 5px;
}

p {
  margin: 0px !important;
}

.fas {
  margin: 0 10px;
  font-size: 5px;
}
</style>
