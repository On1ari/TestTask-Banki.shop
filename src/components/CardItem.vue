<template>
  <div class="card__item" :class="{ sold: isSold }" @click="$emit('click')">
    <button @click="handleClick">
      <img :src="image" :alt="title" class="card__image" />
      <div class="card__title">
        <h2>«{{ title }}»</h2>
        <h2>{{ author }}</h2>
      </div>
    </button>
    <div class="container__price-card">
      <!-- Если товар продан -->
      <h3 v-if="isSold">Продана на аукционе</h3>
      <!-- Если товар активный -->
      <template v-else>
        <div class="card__bottom">
          <div class="card__price">
            <h6 v-if="discount" class="card__discount">{{ discount }}$</h6>
            <h3 class="card__price-text">{{ price }}$</h3>
          </div>
          <button
            @click="toggleState"
            :class="{ inBasket: isActive, button__primary: true }"
          >
            <span v-if="isLoading" class="loader__parent">
              <div class="loader"></div>
            </span>
            <template v-else>
              <span v-if="isActive" :class="{ isActiveButton: isActive }">
                <img
                  src="../assets/img/feather_check.png"
                  alt="Корзина"
                  width="20"
                  height="20"
                />
                В корзине
              </span>
              <span v-else> Купить </span>
            </template>
          </button>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardItem",
  props: {
    image: String,
    title: String,
    author: String,
    discount: String,
    price: String,
    isSold: Boolean,
    card: Object,
    openModal: Function, // Получаем функцию из родителя
  },
  data() {
    return {
      isActive: false, // начальное состояние
      isLoading: false, // Флаг загрузки
    };
  },
  methods: {
    handleClick() {
      this.openModal(this.card); // Вызываем функцию с переданным объектом
    },
    toggleState() {
      if (this.isLoading) return;

      this.isLoading = true;
      setTimeout(() => {
        this.isActive = !this.isActive;
        this.isLoading = false;
        localStorage.setItem(
          `isActive_${this.title}`,
          JSON.stringify(this.isActive)
        ); // Уникальный ключ
      }, 2000);
    },
  },
  created() {
    // При загрузке компонента читаем состояние из localStorage по уникальному ключу
    const savedState = localStorage.getItem(`isActive_${this.title}`);
    if (savedState !== null) {
      this.isActive = JSON.parse(savedState);
    }
  },
};
</script>

<style scoped>
.card__item {
  width: 280px;
  height: 328px;
  box-sizing: border-box;
  border: 1px solid rgb(225, 225, 225);
  white-space: nowrap;
}
.container__price-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 22px 24px 24px 24px;
}
.card__title {
  text-align: start;
  padding: 24px 24px 0px 24px;
}
.card__bottom {
  display: flex;
  justify-content: space-between;
}
.card__price {
  display: flex;
  justify-content: center;
  flex-direction: column;
  white-space: nowrap;
}
.card__discount {
  text-decoration-line: line-through;
  color: #a0a0a0;
}
.sold {
  opacity: 0.5;
  filter: grayscale(100%);
  pointer-events: none;
}

.inBasket {
  background: #5b3a32;
}

.isActiveButton {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
}

.isActiveButton img {
  width: 20px;
  height: 20px;
}

.loader__parent {
  display: flex;
  justify-content: center;
  align-items: center;
}

.loader {
  width: 30px;
  height: 30px;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #ffffff; /* Цвет индикатора */
  border-radius: 50%;
  animation: spin 0.8s linear infinite;
}

@keyframes spin {
  100% {
    transform: rotate(360deg);
  }
}
</style>
