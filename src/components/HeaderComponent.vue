<template>
  <div class="header" section="header">
    <b-navbar class="nav-bar spaced">
      <template slot="brand">
        <b-navbar-item tag="router-link" :to="{ path: '/' }">
          <img src="@/assets/Blog_pic.png" alt="My happy little blog" />
        </b-navbar-item>
      </template>
      <template slot="end">
        <b-navbar-dropdown label="Info">
          <b-navbar-item tag="router-link" :to="{ path: '/about' }">
            About Me
          </b-navbar-item>
          <b-navbar-item href="https://github.com/MMathew93/Blog-Project">
            Source Code
          </b-navbar-item>
        </b-navbar-dropdown>
      </template>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: "Posts"
};
</script>

<style>
.navbar {
  background-color: rgb(248 134 36) !important;
}

.navbar-item img {
  max-height: 5rem !important;
}
</style>
