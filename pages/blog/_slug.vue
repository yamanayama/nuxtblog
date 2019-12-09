<template lang='pug'>
  section.slug
    h1.slug_title {{ article.fields.title }}
    p.slug_date {{ article.sys.updatedAt }}
    div
      {{ article.fields.body.content[0].content[0].value }}
</template>

<script>
import { createClient } from '~/plugins/contentful.js'

const client = createClient()

export default {
  props: {
    id: {
      type: String,
      default: ''
    }
  },
  transition: 'slide-right',
  async asyncData({ env, params }) {
    return await client
      .getEntry(params.sys)
      .then((entrie) => {
        return {
          article: entrie
        }
      })
      .catch(console.error)
  }
}
</script>