<script>

export default {
    components: {

    },

    data() {
        return {

        }
    }
}

</script>

<template>

    <header>
        <div class="logo">
            <img src="../assets/Yugioh_anime_logo.webp" alt="">
        </div>

        <div class="title">
            <h1>Yu-Gi-Oh API</h1>
        </div>

    </header>

</template>

<style scoped>
header {
    width: 100%;
    display: flex;
    height: 4rem;
    background-color: white;
    color: black;
}

.logo {
    width: 5%;
    height: 100%;
    padding: 1rem;
}

.logo>img {
    height: 100%;
}

.title {
    width: 20%;
    height: 100%;
    align-content: center;
    padding-left: 2rem;
}
</style>