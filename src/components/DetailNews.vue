<template>
  <v-container>
    <v-img :src="news.media" max-width="100%" class="rounded-lg mb-3" />
    <h2>{{ news.title }}</h2>
    <h4>{{ news.author }} -</h4>
    <h5>
      {{ moment(news.publishedAt).locale("id").format("LLLL") }}
    </h5>
    <p class="mt-3">{{ news.summary }}</p>
    <v-btn class="secondary mr-5" @click="$router.back()">Kembali</v-btn>
    <v-btn :href="news.link" target="_blank" class="red darken-4 white--text"
      >Baca selengkapnya</v-btn
    >
  </v-container>
</template>
<script>
export default {
  name: "DetailNews",
  props: {
    news: Object,
  },
};
</script>
<style scoped></style>
