<template>
  <div id="listCategory">
    <h1 class="my-5 text-center">Category News</h1>
    <v-layout row class="mx-10 text-center">
      <v-container v-for="category in categoryNews" :key="category.id" flex>
        <v-btn class="secondary" small @click="fetchNews(category.nama)"
          >{{ category.nama }}
        </v-btn>
      </v-container>
    </v-layout>
  </div>
</template>

<script>
export default {
  computed: {
    categoryNews() {
      return this.$store.state.listCategories;
    },
  },
  methods: {
    fetchNews(value) {
      this.$store.dispatch("getCategory", value);
      this.$router.push({
        name: "Satu Kategori Berita",
        params: { category: value },
      });
    },
  },
};
</script>
<style scoped></style>
