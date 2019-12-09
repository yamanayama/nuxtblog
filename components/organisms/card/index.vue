<template lang='pug'>
  article.card
    nuxt-link.wrapper(:to="{ name: 'blog-slug', params: {sys: id}}"
    class="wrapper")
      h1.card_title {{ title }}
      p.card_text {{ text }}
      p.card_date {{ date }}
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: ''
    },
    id: {
      type: String,
      default: ''
    },
    date: {
      type: String,
      default: ''
    }
  }
}
</script>