<template>
  <div class="home">
    <!--<img alt="Vue logo" src="../assets/logo.png">-->
    <GamesList msg="Games Opinion"/>
  </div>
</template>

<script>
import GamesList from '@/components/GamesList.vue'

export default {
  name: 'HomeView',
  components: {
    GamesList
  }
}
</script>
