<script>
export default {
    props: {
        description: String,
        img: String,
        model: String,
    },

    data() {
        return {

        }
    }
}
</script>

<template>

    <div class="card">
        <img :src="img" alt="">
        <h3>{{ description }}</h3>
        <span>{{ model }}</span>
    </div>

</template>

<style scoped>
.card {
    text-align: center;
    width: calc(20% - 0.8rem);
    background-color: orange;
}

img {
    width: 100%;
}

h3 {
    margin: 0.5rem auto;
}

span {
    margin: 0.5rem auto;
    color: black;
}
</style>