<template>
  <div class="container">
    <div v-for="article in articles" :key="article.slug">
      <nuxt-link :to="article.path">
        {{ article.slug }}
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const articles = await $content('articles')
      .limit(5)
      .fetch()
    return {
      articles
    }
  }
}
</script>
