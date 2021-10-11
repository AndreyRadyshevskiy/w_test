<template>
  <div>
    <h2>Новости:</h2>
    <div>
      <nuxt-link
        :to="'/news/' + singleNews.id"
        v-for="singleNews in news"
        :key="singleNews.id"
      >
        <h3>{{ singleNews.name }}</h3>
        <p>{{ singleNews.full_text }}</p>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  async fetch() {
    const news = await this.$axios.$get(`https://shop.anyprinter.ru/api/news`);
    this.news = news;
  },
  data() {
    return {
      news: null,
    };
  },
};
</script>

<style>
</style>
