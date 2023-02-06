<template>
    <section class="container">
        <h1>Sono il singolo post</h1>
        <div>Sono lo slug: {{ slug }}</div>
    </section>
</template>

<script>
export default ({

    props: [
        'slug',
    ]

})
</script>

<style lang="scss" scoped>

</style>
