<template>
  <nav class="navbar bg-body-tertiary">
   <div class="container container-fluid justify-content-end">

    <router-link class="btn btn-outline-success me-2" to="/">Home</router-link>
    <router-link class="btn btn-outline-success me-2" to="/about">About</router-link>

   </div>
  </nav>
  <router-view/>
</template>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
} */
</style>
