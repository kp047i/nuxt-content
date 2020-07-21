<template>
  <div class="container">
    <h1>{{ article.title }}</h1>
    <nuxt-content :document="article" />
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content(`articles/${params.slug}`).fetch()
    return {
      article
    }
  }
}
</script>

<style>
.nuxt-content h1 {
  font-size: 20px;
}
</style>
