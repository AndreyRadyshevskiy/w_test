<template>
  <nav>
    <nuxt-link to="/">Главная</nuxt-link>
    <nuxt-link to="/news">Новости</nuxt-link>
    <a v-if="$route.params.id" :to="`/news/${$route.params.id}`">
      Новость {{ $route.params.id }}
    </a>
  </nav>
</template>

<script>
export default {};
</script>

<style>
</style>
