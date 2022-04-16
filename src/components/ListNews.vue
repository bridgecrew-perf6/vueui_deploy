<template>
  <div id="listNews">
    <h1 class="my-5" style="color: white">Berita Terkini</h1>
    <v-layout row class="mx-10">
      <v-container v-for="berita in listNews" :key="berita.id" flex xs12 sm6>
        <v-card>
          <v-img :src="berita.media" max-height="150" />

          <v-card-subtitle>
            <b>{{ berita.author }}</b>
            <p>
              {{ moment(berita.published_date).locale("id").format("LLLL") }}
            </p>
          </v-card-subtitle>
          <h4 class="text-center px-3">{{ berita.title }}</h4>
          <v-card-text>
            {{ berita.excerpt }}
          </v-card-text>
          <v-btn
            class="secondary mb-5"
            small
            :to="{
              name: 'Detail Berita',
              params: { slug: toSlug(berita.title) },
            }"
            >Lihat selengkapnya
          </v-btn>
        </v-card>
      </v-container>
    </v-layout>
  </div>
</template>

<script>
export default {
  computed: {
    search() {
      return this.$store.state.search;
    },
    listNews() {
      return this.$store.state.listNews.filter((item) => {
        return item.title.toLowerCase().match(this.search.toLowerCase());
      });
    },
  },

  methods: {
    fetchNews(value) {
      this.$store.dispatch("fetchListNews", value);
    },

    toSlug(value) {
      value = value
        .toLowerCase() // LowerCase
        .replace(/\s+/g, "-") // space to -
        .replace(/&/g, `-and-`) // & to and
        .replace(/--/g, `-`);
      return value;
    },
  },
  mounted() {
    this.fetchNews(this.$store.state.category);
  },
};
</script>
<style scoped>
#listNews {
  text-align: center;
  background-color: rgb(87, 140, 255);
}
</style>
