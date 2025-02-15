<template>
  <div id="app" class="app">
    <AppHeader :searchQuery="searchQuery" @update-search="updateSearchQuery" />
    <AppMain :searchQuery="searchQuery" />
    <AppFooter />
  </div>
</template>

<script>
import AppHeader from "./components/Header.vue";
import AppMain from "./components/Main.vue";
import AppFooter from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    AppHeader,
    AppMain,
    AppFooter,
  },
  data() {
    return {
      searchQuery: '',
    };
  },
  methods: {
    updateSearchQuery(query) {
      this.searchQuery = query;
    },
  },
};
</script>

<style>
.app {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100vh;
}
</style>
