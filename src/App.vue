<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style>
html {
  height: 100%;
}

body {
  min-height: 100%;
  background-color: rgb(67, 70, 75);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  background-color: rgb(67, 70, 75);
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
