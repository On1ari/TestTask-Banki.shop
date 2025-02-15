<template>
  <header class="header">
    <div class="container">
      <nav class="nav">
        <ul class="nav-links">
          <li>
            <a href="#"><span>Каталог</span></a>
          </li>
          <li>
            <a href="#"><span>Доставка</span></a>
          </li>
          <li>
            <a href="#"><span>Оплата</span></a>
          </li>
          <li>
            <a href="#"><span>Контакты</span></a>
          </li>
          <li>
            <a href="#"><span>О компании</span></a>
          </li>
        </ul>
      </nav>
      <div class="search">
        <input
          v-model="inputQuery"
          type="text"
          placeholder="Поиск по названию картины"
        />
        <button class="button__primary" @click="updateSearchQuery">
          Найти
        </button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
  props: {
    searchQuery: String,
  },
  data() {
    return {
      inputQuery: this.searchQuery,
    };
  },
  methods: {
    updateSearchQuery() {
      this.$emit("update-search", this.inputQuery);
    },
  },
};
</script>

<style>
a span {
  font-weight: 400;
  font-size: 14px;
}
.header {
  max-width: 1920px;
  width: 100%;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-sizing: border-box;
  border: 1px solid rgb(225, 225, 225);
}

.container {
  max-width: 1200px;
  width: 100%;
  min-height: 96px;
  margin: 0 auto;
  padding: 0 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-right: 15px;
}

.nav-links {
  display: flex;
  justify-content: space-between;
  gap: 15px;
  width: 100%;
  max-width: 542px;
  white-space: nowrap;
}

.search {
  display: flex;
  align-items: center;
  justify-content: space-between;
  max-width: 416px;
  width: 100%;
  max-height: 48px;
  box-sizing: border-box;
  border: 1px solid rgb(225, 225, 225);
}

.search input {
  margin: 0 15px 0 15px;
  min-width: 218px;
  width: 100%;
  font-weight: 400;
  font-size: 14px;
  background: rgb(246, 243, 243);
}

.search button {
  max-width: 122px;
  width: 100%;
}

@media (max-width: 910px) {
  .container {
    flex-direction: column;
    justify-content: center;
  }

  .nav {
    justify-content: center;
    margin: 15px 0 15px 0;
  }

  .search {
    max-width: 100%;
    margin-bottom: 15px;
  }
}

@media (max-width: 480px) {
  .nav-links {
    flex-direction: column;
    align-items: center;
  }
}

@media (max-width: 413px) {
  .search input {
    margin: 0 5px 0 5px;
    min-width: 218px;
  }
}
</style>
