<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/movie">Search-Movie</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
@import url('../node_modules/nes.css/css/nes.css');
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

* :not(.v-icon) {
  font-family: "Press Start 2P" !important;
}

body {
  padding: 0 2rem;
  margin: 0 2rem;
}

#app {
  font-family: "Press Start 2P";
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
