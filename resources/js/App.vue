<template>
    <div class="container">
        <header>
            <Navbar/>
        </header>

        <main>
            <router-view></router-view>
        </main>

        <footer>
            <Footer/>
        </footer>
    </div>
</template>

<script>
import Navbar from './components/Navbar';
import Footer from './components/Footer';

export default {
  name: 'App',
  components: {
    Navbar,
    Footer,
  },
  data() {
    return {
        arrPosts: [],
    };
  },
  created() {
    axios.get('/api/posts')
      .then(response => this.arrPosts = response.data.result);
  }
}
</script>

<style lang="scss">
    @import '~bootstrap/scss/bootstrap';

    header,
    footer {
        height: 50px;
    }

    main {
        height: calc(100vh - 100px);
    }
</style>

