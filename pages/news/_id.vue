<template>
  <div>
    <div v-if="singleNews">
      <h2>{{ singleNews.name }}</h2>
      <p>{{ singleNews.full_text }}</p>
    </div>
  </div>
</template>

<script>
export default {
  async fetch() {
    console.log(this.$route.params);
    const singleNews = await this.$axios.$get(
      `https://shop.anyprinter.ru/api/news/${this.$route.params.id}`
    );
    this.singleNews = singleNews;
    console.log(this.singleNews);
  },
  data() {
    return {
      singleNews: null,
    };
  },
};
</script>

<style>
</style>
