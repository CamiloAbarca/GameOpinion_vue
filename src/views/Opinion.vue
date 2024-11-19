<template>
    <div>
        <h1>Escribe tu opinión para el juego:</h1>
        <br>
        <h2>{{ name }}</h2>
        <div>
            <img :src="src" alt="img_game">
        </div>
        <form>
            <div class="mb-3">
                <label for="name" class="form-label">Nombre</label>
                <input type="text" class="form-control" id="name">
            </div>
            <div class="form">
                <label for="opinion">Opinión</label>
                <textarea class="form-control" placeholder="Tú opinión debe ir aquí..." id="opinion"></textarea>
            </div>
            <br>
            <button type="submit" class="btn btn-primary">Opinar</button>
        </form>
        <br>
        <h1>A continuación podrás ver tu opinión.</h1>
        <br>
        
        
        

        <div class="alert alert-danger" role="alert">
            No existen opiniones para mostrar.
        </div>

    </div>
</template>

<script>
export default {
    name: "opinion-view",
    computed: {
        name() {
            return this.$route.params.name;
        },
        src() {
            return this.$route.params.src;
        }
    }
}
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
</style>