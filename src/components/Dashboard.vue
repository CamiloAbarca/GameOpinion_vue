<template>
    <div class="dashboard">
        <br>
        <div class="fa-solid fa-user fa-xl" style="color: #fcfcfc;"></div>

        <h2>Bienvenid@</h2>
        <h3>{{ nameUser }} {{ lastName }}</h3>
    </div>
</template>

<script>
export default {
    name: "dashboard-component",
    props: {
        nameUser: {
            type: String,
        },
        lastName: {
            type: String,
        }
    }
}
</script>

<style scoped>
.dashboard {
    background-color: rgb(39, 39, 39);
}
</style>