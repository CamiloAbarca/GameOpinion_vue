<template>
    <div>
        <h1>Escribe tu opinión para el juego:</h1>
        <br />
        <h2>{{ name }}</h2>
        <div>
            <img :src="src" alt="img_game" />
        </div>
        <form>
            <div>
                <label for="nameOpinion">Nombre</label>
                <input type="text" id="name" v-model="nameOpinion" />
            </div>
            <div>
                <label for="opinion">Opinión</label>
                <textarea placeholder="Tu opinión debe ir aquí..." id="opinion" v-model="opinion"></textarea>
            </div>
            <br />
            <button type="submit" @click.prevent="opinar">Agregar</button>
        </form>
        <br />
        <h1>A continuación podrás ver tu opinión.</h1>
        <br />

        <div role="alert" class="alert" v-if="opinions.length === 0">
            No existen opiniones para mostrar.
        </div>

        <div v-for="(opinionItem, index) in opinions" :key="index" class="collapse-container">
            <div class="collapse-header" @click="toggleCollapse(index)">
                {{ opinionItem.name }}
            </div>
            <div class="collapse-content" v-show="opinionItem.isOpen">
                <label for="">Opinión</label>
                <textarea v-model="opinionItem.text" readonly></textarea>
                <button class="btnDelete" @click="deleteOpinion(index)">Eliminar</button>
                <button class="btnEdit">Editar</button>
            </div>
        </div>


    </div>
</template>

<script>
export default {
    name: "opinion-view",
    props: {
        title: {
            type: String,
            required: true,
        },
    },
    data() {
        return {
            nameOpinion: "",
            opinion: "",
            opinions: [],
            showCollapse: false,
            isOpen: false
        };
    },
    computed: {
        name() {
            return this.$route.params.name;
        },
        src() {
            return this.$route.params.src;
        },
    },
    methods: {
        opinar() {
            if (this.nameOpinion && this.opinion) {
                this.opinions.push({ name: this.nameOpinion, text: this.opinion, isOpen: false });
                this.nameOpinion = "";
                this.opinion = "";
            } else {
                alert("Por favor, completa ambos campos.");
            }
        },
        toggleCollapse(index) {
            this.opinions[index].isOpen = !this.opinions[index].isOpen;
        },
        deleteOpinion(index){
            this.opinions.splice(index, 1);
        }

    }
};
</script>

<style scoped>
img {
    background-color: #202020;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 10px;
    width: 300px;
}

form {
    text-align: left;
    padding: 3%;
}

.accordion {
    padding: 3px;
}

form {
    max-width: 90%;
    margin: 20px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    background-color: #f9f9f9;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

div {
    margin-bottom: 15px;
}

label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

input[type="text"],
textarea {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 16px;
    box-sizing: border-box;
}

button {
    background-color: #0dcaf0;
    color: black;
    border: none;
    padding: 10px 15px;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.btnDelete {
    background-color: #dc3545;
    color: white;
    border: none;
    padding: 10px 15px;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.btnEdit {
    background-color: #ffc107;
    color: black;
    border: none;
    padding: 10px 15px;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s;
    margin-left: 1%;
}

button:hover {
    background-color: #3598ac;
}

.btnDelete:hover {
    background-color: #7a1f1f;
}

.btnEdit:hover {
    background-color: #b3bd27;
}

.alert {
    background-color: #f8d7da;
    color: #721c24;
    border: 1px solid #f5c6cb;
    border-radius: 5px;
    padding: 15px;
    margin: 20px 0;
    font-size: 16px;
    display: flex;
    align-items: center;
}

.alert-icon {
    margin-right: 10px;
}

.alert .close-btn {
    margin-left: auto;
    background: none;
    border: none;
    color: #721c24;
    font-size: 16px;
    cursor: pointer;
}

.collapse-container {
    margin: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    overflow: hidden;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.collapse-header {
    background-color: #e7f1ff;
    color: #5780e7;
    padding: 15px;
    cursor: pointer;
    font-size: 18px;
    text-align: left;
}

.collapse-content {
    padding: 15px;
    background-color: #f9f9f9;
    text-align: left;
    color: #5780e7;
}

.collapse-content textarea {
    width: 100%;
    height: 100px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 16px;
    box-sizing: border-box;
}
</style>