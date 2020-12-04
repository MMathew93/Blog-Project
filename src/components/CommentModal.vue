<template>
  <div class="form-box">
    <form class="form">
      <b-field label="Username">
        <b-input v-model="username" />
      </b-field>
      <b-field label="Comment">
        <b-input type="textarea" v-model="text" maxlength="255" />
      </b-field>
      <div class="button-box"></div>
    </form>
    <b-field horizontal>
      <b-button native-type="button" @click="submission">Submit</b-button>
      <b-button @click="cancelSubmission">Cancel</b-button>
    </b-field>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "CommentModal",
  props: ["postId"],
  data() {
    return {
      username: "",
      text: ""
    };
  },
  methods: {
    submission() {
      let newComment = {
        username: this.username,
        text: this.text
      };
      try {
        axios.post(
          "https://my-personal-blog-api.herokuapp.com/" +
            this.postId +
            "/comments/new",
          newComment
        );
        this.username = "";
        this.text = "";
        //this.$emit("submitted", true);
      } catch (err) {
        throw new Error(err);
      }
    },
    cancelSubmission() {
      this.username = "";
      this.text = "";
      this.$emit("cancelled");
    }
  }
};
</script>

<style>
.title {
  color: white;
  text-align: center;
}

.form-box {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form {
  display: flex;
  flex-direction: column;
  width: 66%;
  text-align: left;
}

.label {
  color: rgb(153, 145, 131);
}

.select,
.select select {
  width: 100%;
}

.button-box {
  display: flex;
  justify-content: center;
}

.button {
  margin: 15px;
}
</style>
