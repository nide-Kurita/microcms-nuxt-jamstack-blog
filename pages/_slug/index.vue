<template>
  <main class="main">
    <h1 class="title">{{ title }}</h1>
    <p class="publishedAt">{{ new Date(publishedAt).toLocaleDateString() }}</p>
    <p>↓ローカルフォルダから読み込んでる画像</p>
    <img v-bind:src="'/img/'+img" alt="">
    <p v-html="'/img/'+img"></p>

    <p>↓microCMSから読み込んでる画像</p>
    <img :src="photo.url" alt="">
    <p v-html="photo.url"></p>
    <div class="post" v-html="body"></div>
    <div class="boolean" v-html="boolean"></div>
    <p class="category">{{ category && category.name }}</p>
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