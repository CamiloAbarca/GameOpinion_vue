<template>
  <nav>
    <router-link to="/">Home</router-link>
  </nav>
  <router-view/>
</template>

<style>

body{
  background-color: rgb(24, 24, 24);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #6daed0;
}

nav {
  padding: 30px;
  background-color: rgb(66, 66, 66);
}

nav a {
  font-weight: bold;
  color: white;
}

nav a.router-link-exact-active {
  color: #00a7f6;
}
</style>
