<template>
  <div>
    <br>
    <h1>Lista de Juegos</h1>
    <div v-if="loading">Cargando...</div>
    <div v-else class="grid-container">
      <div v-for="game in games" :key="game.id" class="game-item">
        <img :src="game.background_image" :alt="game.name" />
        <h2>{{ game.name }}</h2>
        <hr>
        <p>Rating: {{ game.rating }}</p>
        <hr>
        <p>Released: {{ game.released }}</p>
        <hr>
        <p>Update: {{ game.updated }}</p>
        <hr>
        <button class="opinar-button" @click="opinar(game)">Opinar</button>
        <i class="fa-solid fa-heart fa-lg icon-heart" @click="like(game)" style="color: #c10b0b;"></i>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';
  import '@fortawesome/fontawesome-free/css/all.css';


export default {
  name: 'GameList',
  data() {
    return {
      games: [],
      loading: true,
    };
  },
  mounted() {
    this.fetchGames();
  },
  methods: {
    async fetchGames() {
      try {
        const response = await axios.get('https://api.rawg.io/api/games', {
          params: {
            key: '1e1de181277a4c418d5d50d892d3e6da',
            dates: '2024-01-01,2024-10-31',
            platforms: '18,1,7',
          },
        });
        this.games = response.data.results;
      } catch (error) {
        console.error('Error fetching games:', error);
      } finally {
        this.loading = false;
      }
    },
    opinar(game) {
      this.$router.push({ name: 'Opinion', params: { name: game.name, src: game.background_image } });
    },
    like(game) {
      this.$router.push({ name: 'Admin', params: { name: game.name, src: game.background_image } });
    }
  },
}
</script>

<style scoped>

.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
  padding: 20px;
}

.game-item {
  background-color: #202020;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 10px;
  text-align: left;
  color: white;
}

.game-item img {
  width: 100%; 
  height: 150px;
  border-radius: 8px 8px 0 0;
}

.opinar-button {
  background-color: #0d6efd;
  color: white;
  border: none; 
  border-radius: 8px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s;
  margin-right: 3%;
}

.opinar-button:hover {
  background-color: rgb(114, 114, 114);
}

.icon-heart {
    transition: transform 0.3s ease, color 0.3s ease;
}

.icon-heart:hover {
    transform: scale(1.5);
    color: #ff0000;
}
</style>
