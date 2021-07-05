<template>
  <main class="main">
    <h1 class="title">{{ title }}</h1>
    <p class="publishedAt">{{ publishedAt }}</p>
    <div class="post" v-html="body"></div>
    <p class="textarea" v-html="textarea"></p>
    <p class="text" v-html="text"></p>
    <div class="boolean" v-html="boolean"></div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://nidecms.microcms.io/api/v1/blog/${params.slug}`,
      {
        headers: { 'X-API-KEY': 'f7406420-f5e7-4121-a039-5ffcc3a658ba' }
      }
    )
    return data
  }
}
</script>