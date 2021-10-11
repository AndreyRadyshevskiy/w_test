<template>
  <div>
    <carousel :perPage="3">
      <slide v-for="slide in sliderData" :key="slide.id">
        <img :src="`${url}${slide.small_photo}`" alt="" />
      </slide>
    </carousel>
    <div>
      <h2>Новости:</h2>
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
    const slides = await this.$axios.$get(
      `https://shop.anyprinter.ru/api/slider`
    );
    this.sliderData = slides;
    const news = await this.$axios.$get(
      `https://shop.anyprinter.ru/api/news?limit=5`
    );
    this.news = news;
  },
  data() {
    return {
      sliderData: null,
      news: null,
      url: "https://shop.anyprinter.ru/",
    };
  },
};
</script>

<style>
</style>
