<template>
  <footer class="footer">
    <router-link :to="{ name: 'Article', params: { id: `${postId}` } }">
      <span>
        Read More...
      </span>
    </router-link>
  </footer>
</template>

<script>
export default {
  name: "ReadMoreComponent",
  props: ["postId"]
};
</script>

<style>
.footer {
  color: white;
  padding: 0 !important;
  position: absolute;
  top: 75%;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.8) !important;
  align-items: center;
  text-align: center;
  left: 0;
  height: 25%;
  display: flex;
  justify-content: center;
  border-radius: 0 0 4px 4px;
}
</style>
