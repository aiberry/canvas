<template>
  <div class="app">
    <div class="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/table">Table</router-link> |
      <router-link to="/canvas">Canvas</router-link>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
.app {
  color: #2c3e50;
  font-family: Avenir, Helvetica, Arial, sans-serif;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  text-align: center;
}

.nav {
  padding: 30px;

  a {
    color: #2c3e50;
    font-weight: bold;
  }

  .router-link-exact-active {
    color: #42b983;
  }
}
</style>
