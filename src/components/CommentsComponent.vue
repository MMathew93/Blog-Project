<template>
  <div>
    <section>
      <div class="commentSection">
        <div
          class="comment-boxes"
          v-for="comment in comments"
          :key="comment._id"
        >
          <div :id="`${comment._id}`">
            <div class="commentInfo">
              <p class="text">{{ comment.username }}</p>
              <i class="fas fa-circle dot"></i>
              <p class="text">{{ comment.postedDate }}</p>
            </div>
            <div class="commentText">
              <p class="text">{{ comment.text }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import axios from "axios";
import dayjs from "dayjs";

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
        "https://my-personal-blog-api.herokuapp.com/" +
          this.postId +
          "/comments"
      );
      this.formatDate(res.data);
      this.sortComments(res.data);
      this.comments = res.data;
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
    },
    sortComments(dataArr) {
      dataArr.sort((a, b) => {
        if (a.date > b.date) {
          return -1;
        } else {
          return 1;
        }
      });
    }
  }
};
</script>

<style>
.comment-boxes {
  margin: 25px auto;
  background-color: rgb(30, 30, 30);
  text-align: left;
  padding: 1.5rem;
  font-size: 18px;
  border-radius: 4px;
  color: white;
}

.commentInfo,
.commentText {
  display: flex;
  align-items: center;
  margin: 5px;
}

.text {
  margin: 0px !important;
}

.dot {
  margin: 0 10px;
  font-size: 5px;
}
</style>
