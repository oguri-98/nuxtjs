<script>
  export default {
    async asyncData({ $content, params }) {
      // fetch our article here
      const article = await $content('articles', params.slug).fetch()

      return { article }
    }
 
  }

</script>

<template>
  <article>
    <nuxt-content :document="article" />
  </article>
</template>

<pre> {{ article }} </pre>
<p>Post last updated: {{ article.updatedAt }}</p>

methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    }
 }

<p>Article last updated: {{ formatDate(article.updatedAt) }}</p>
