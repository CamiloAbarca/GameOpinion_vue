<template>
  <nav>
    <div>
      <div class="navElements">
        <span><i class="fa-solid fa-headset" style="color: #00a7f6;"></i> Games opinion</span>
      </div>
      <div>
        <router-link to="/"><i class="fa-solid fa-house"></i> Home</router-link>
      </div>
    </div>
  </nav>
  <router-view />
</template>

<style>
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
  text-align: right;
}

.navElements {
  display: flex;
  justify-content: space-between;
}

nav a {
  font-weight: bold;
  color: white;
  text-decoration: none;
}

nav a.router-link-exact-active {
  color: #00a7f6;
}
</style>
