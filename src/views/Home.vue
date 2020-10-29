<template>
  <div class="home">
    <HeaderComponent />
    <PostsComponent />
  </div>
</template>

<script>
import PostsComponent from "@/components/PostsComponent";
import HeaderComponent from "@/components/HeaderComponent";

export default {
  name: "Home",
  components: {
    PostsComponent,
    HeaderComponent
  }
};
</script>
