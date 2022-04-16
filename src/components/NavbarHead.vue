<template>
  <nav>
    <v-toolbar flat class="blue px-10">
      <v-spacer></v-spacer>
      <v-text-field
        class="mt-3"
        prepend-inner-icon="mdi-magnify"
        v-model="search"
      ></v-text-field>

      <v-btn icon href="/kategori">
        <v-icon>mdi-card-text</v-icon>
      </v-btn>
    </v-toolbar>
  </nav>
</template>
<script>
export default {
  data() {
    return {
      search: (this.$store.state.search = ""),
    };
  },
  methods: {
    categoryNull() {
      this.$store.dispatch("getCategory", "");
      this.search = "";

      this.$router
        .push({
          name: "Home",
        })
        .catch((err) => err);
    },
  },
  watch: {
    search(value) {
      this.$store.dispatch("getSearch", value);
    },
  },
};
</script>
<style scoped>
a {
  cursor: pointer;
  text-decoration: none;
  color: unset !important ;
}
</style>
