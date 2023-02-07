<template>
    <section class="container">
        <h1>Posts</h1>
        <div class="row g-3" v-if="arrPosts">
            <div
                v-for="post in arrPosts"
                :key="post.id"
                class="col-sm-6 col-md-4"
            >
                <div class="card h-100">
                    <img
                        :src="post.image"
                        class="card-img-top"
                        :alt="post.title"
                    />
                    <div class="card-body d-flex flex-column">
                        <h5 class="card-title">{{ post.title }}</h5>
                        <p class="card-text flex-grow-1">{{ post.excerpt }}</p>
                        <router-link :to="{ name: 'post', params: {slug: post.slug}}" class="btn btn-primary">Read</router-link>
                    </div>
                </div>
            </div>
        </div>
        <div v-else>
            <img class="d-flex m-auto" src="https://media.tenor.com/OTzJy4d4xGMAAAAC/computer-stick-man.gif" alt="gif">
        </div>
    </section>
</template>

<script>
export default {
    data() {
        return {
            arrPosts: null,
            urlApi: "http://localhost:8000/api/posts",
        };
    },
    created() {
        axios.get(this.urlApi).then((axiosResponse) => {
            if (axiosResponse.data.success) {
                this.arrPosts = axiosResponse.data.result;
            }
        });
    },
};
</script>

<style lang="scss" scoped>

</style>
