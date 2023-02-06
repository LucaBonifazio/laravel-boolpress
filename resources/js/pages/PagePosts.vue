<template>
    <section class="container">
        <h1>Sono i Posts</h1>
        <div class="row g-3">
            <div v-for="post in arrPosts" :key="post.id" class="col-sm-6 col-md-4">
                <div class="card h-100">
                    <img :src="post.image" class="card-img-top" :alt="post.title">
                    <div class="card-body d-flex flex-column">
                        <h5 class="card-title">{{ post.title }}</h5>
                        <p class="card-text flex-grow-1">{{ post.excerpt }}</p>
                        <a :href="'/posts/' + post.slug" class="btn btn-primary">Read</a>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default ({
    data () {
    return {
      arrPosts: null,
      urlApi: 'db_posts',
    }
  },
  created() {
    axios.get(this.urlApi)
      .then((axiosResponse) => {
        this.arrPosts = axiosResponse.data.response;
      });
  },
})
</script>

<style lang="scss" scoped>

</style>
