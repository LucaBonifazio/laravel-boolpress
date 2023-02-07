<template>
    <section class="container">
        <div v-if="post">
            <h1>{{ slug }}</h1>
            <img
                :src="post.image"
                class="card-img-top"
                :alt="post.title"
            >
            <h5>{{ post.title }}</h5>
            <p>{{ post.content }}</p>
        </div>
        <div v-else>
            <img class="d-flex m-auto" src="https://media.tenor.com/OTzJy4d4xGMAAAAC/computer-stick-man.gif" alt="gif">
        </div>
    </section>
</template>

<script>
export default ({
    data() {
        return {
            post: null,
            urlApi: ('http://localhost:8000/api/posts/' + this.slug),
        };
    },
    created() {
        axios.get(this.urlApi).then((axiosResponse) => {
            if (axiosResponse.data.success) {
                this.post = axiosResponse.data.result;
            }
        });
    },

    props: [
        'slug',
    ]

})
</script>

<style lang="scss" scoped>

</style>
