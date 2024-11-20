<template>
  <div class="container">
    <div class="box">
      <div class="msg">
        <p class="error-code">404</p>
        <p class="error-message">Not Found</p>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "not-found-view"
}
</script>

<style scoped>
.container {
  display: grid;
  place-items: center;
  height: 50vh;
}

.box {
  background: rgb(217, 170, 245);
  background: linear-gradient(90deg, rgba(217, 170, 245, 1) 0%, rgba(159, 130, 239, 1) 35%, rgba(139, 136, 239, 1) 100%);
  width: 700px;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: white;
  font-weight: bold;
}

.msg {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.error-code {
  font-size: 150px;
  margin: 0;
}

.error-message {
  font-size: 30px;
  margin: 0;
}
</style>