<template>
  <div class="main-container" :nameUser="nameUser" :lastName="lastName">
    <Dashboard class="dashboard" :nameUser="nameUser" :lastName="lastName" v-if="showDashboard"></Dashboard>
    <div class="content">
      <div v-if="reqData">
        <h1>Para ver la información ingresa tus datos:</h1>

        <button class="addData-button" @click="datos">Ingresa Datos</button>
      </div>

      <div v-if="showInfo">
        <div class="resume">
          <h1>Resumen de tu cuenta</h1>
          <h3>Le diste Me Gusta al juego: <span style="font-size: 20px; text-shadow: 2px 2px 4px gray;">{{ name }}</span></h3>
          <br>
          <div class="coins">
            <h3>¿Deseas comprar coins para este juego?</h3>
            <br>
            <div class="spaceCoin">
              <h3 style="color: red;" v-if="progreso === 50">No se pueden agregar mas Coin's</h3>
              <button class="addCoin-button" @click="addCoin" v-if="progreso < 50"> <i class="fa-solid fa-coins"
                  style="color: #000000;"></i> Agregar
                coins</button>
            </div>
            <div class="line"></div>
            <h1>Cantidad de coins comprados</h1>
            <div id="progressBar">
              <div id="progress">
                <span id="coinCount">${{ progreso }}</span>
              </div>
            </div>
            <p v-if="progreso === 50">Llegaste al máximo de tu crédito.</p>
          </div>
        </div>
        <br><br><br><br>
        <div class="container">
          <div class="box yellow">
            <h2>% de finalización de juego</h2>
            <h2>17% <i class="fa-regular fa-star-half fa-xl"></i></h2>
          </div>
          <div class="box green">
            <h2>Logros en el juego</h2>
            <h2>166 <i class="fa-solid fa-trophy fa-xl" style="color: #ffffff;"></i></h2>
          </div>
          <div class="box blue">
            <h2>Recompensas</h2>
            <h2>200 <i class="fa-solid fa-award fa-xl" style="color: #000000;"></i></h2>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Dashboard from '@/components/Dashboard.vue';

export default {
  name: "Admin-view",
  components: {
    Dashboard
  },
  data() {
    return {
      nameUser: '',
      lastName: '',
      showInfo: false,
      reqData: true,
      showEnd: false,
      progreso: 0,
    };
  },
  computed: {
    name() {
      return this.$route.params.name;
    }
  },
  methods: {
    datos() {
      const nombre = prompt("Por favor ingresa tu nombre:");
      const apellido = prompt("Por favor ingresa tu apellido:");

      if (nombre && apellido) {
        this.nameUser = nombre;
        this.lastName = apellido;
        this.showInfo = true;
        this.reqData = false;
        this.showDashboard = true
      } else {
        alert("Por favor, asegúrate de ingresar tanto el nombre como el apellido.");
      }
    },
    addCoin() {
      if (this.progreso < 50) {
        this.progreso += 1;
        console.log(this.progreso);

        this.updateProgressBar();

        if (this.progreso <= 20) {
          this.setProgressColor('green');
        } else if (this.progreso > 20 && this.progreso <= 30) {
          this.setProgressColor('#f7bb07');
        } else if (this.progreso > 30 && this.progreso <= 50) {
          this.setProgressColor('red');
        }
      }
    },
    updateProgressBar() {
      const progressElement = document.getElementById("progress");
      const percentage = (this.progreso / 100) * 100;
      progressElement.style.width = percentage + '%';
    },
    setProgressColor(color) {
      const progressElement = document.getElementById("progress");
      progressElement.style.backgroundColor = color;
    }
  }
}
</script>

<style>
body {
  background-color: white;
}

.main-container {
  display: flex;
  height: 100vh;
}

.dashboard {
  width: 200px;
}

.addData-button {
  background-color: #04a71f;
  color: white;
  border: none;
  border-radius: 8px;
  padding: 10px 20px;
  font-size: 20px;
  cursor: pointer;
  transition: background-color 0.3s;
  margin-right: 3%;
}

.addData-button:hover {
  background-color: rgb(114, 114, 114);
}

.addCoin-button {
  background-color: #f7bb07;
  color: black;
  border: none;
  border-radius: 8px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s;
  margin-right: 3%;
  width: 200px;
}

.addCoin-button:hover {
  background-color: rgb(114, 114, 114);
  color: white;
}

.content {
  flex: 1;
  padding: 20px;
  color: black;
}

.resume {
  text-align: left;
  margin-left: 150px;
}

.container {
  display: flex;
  justify-content: star;
  margin-left: 150px;

}

.coins {
  display: block;
  border: 1px solid grey;
  padding: 1%;
  width: 600px;
  box-sizing: border-box;
}

.spaceCoin {
  display: grid;
  justify-content: center;
}

.line {
  border: 1px solid grey;
  margin-top: 5%;
  width: 100%;
}

.box {
  width: 400px;
  height: 150px;
  display: grid;
  align-items: center;
  justify-content: left;
  text-align: left;
}

.yellow {
  background-color: #f7bb07;
  color: black;
}

.green {
  background-color: #188351;
  color: white;

}

.blue {
  background-color: #0dc4e8;
  color: black;
}

#progressBar {
  width: 100%;
  background-color: #f3f3f3;
  border: 1px solid #ccc;
  border-radius: 5px;
  height: 20px;
  margin-top: 10px;
}

#progress {
  height: 100%;
  width: 0%;
  transition: width 0.3s;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}
</style>