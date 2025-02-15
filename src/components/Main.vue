<template>
  <main class="main">
    <div class="main__container">
      <h1 class="main__title">Картины эпохи Возрождения</h1>
      <div class="card__list">
        <template v-if="filteredCards.length > 0">
          <CardItem
            v-for="(card, index) in filteredCards"
            :key="index"
            :image="card.image[0]"
            :title="card.title"
            :author="card.author"
            :discount="card.discount"
            :price="card.price"
            :isSold="card.isSold"
            :card="card"
            :openModal="openModal"
          />
        </template>
        <p v-else class="not-found-message">Ничего не найдено</p>
      </div>
    </div>
    <div v-if="showModal" class="modal" @click.self="closeModal">
      <div class="modal-content">
        <span class="close" @click="closeModal">&times;</span>

        <div v-if="selectedCard?.image?.length" class="slider">
          <img
            :src="selectedCard.image[currentIndex]"
            alt="Товар"
            class="slide-img"
          />
          <div class="arrow__container">
            <button class="arrow" @click="prevSlide">❮</button>
            <button class="arrow" @click="nextSlide">❯</button>
          </div>

          <div class="slide-indicator">
            {{ currentIndex + 1 }} / {{ selectedCard.image.length }}
          </div>
        </div>

        <h2 style="margin-top: 5px">«{{ selectedCard.title }}»</h2>
        <p><strong>Автор:</strong> {{ selectedCard.author }}</p>
        <p>
          <strong>Цена:</strong>
          {{ selectedCard.price + "$" || "Цена не указана" }}
        </p>
        <p>
          <strong>Скидка:</strong>
          {{
            selectedCard.discount ? `${selectedCard.discount}$` : "Нет скидки"
          }}
        </p>
      </div>
    </div>
  </main>
</template>

<script>
import CardItem from "./CardItem.vue";

export default {
  name: "AppMain",
  components: {
    CardItem,
  },
  props: {
    searchQuery: String,
    isOpen: Boolean, // Флаг для отображения окна
  },
  data() {
    return {
      cards: [
        {
          image: [
            require("@/assets/img/1.png"),
            require("@/assets/img/2.png"),
            require("@/assets/img/3.png"),
            require("@/assets/img/4.png"),
          ],
          title: "Рождение Венеры",
          author: "Сандро Боттичелли",
          price: "1 000 000",
          discount: "2 000 000",
          isSold: false,
        },
        {
          image: [
            require("@/assets/img/2.png"),
            require("@/assets/img/3.png"),
            require("@/assets/img/4.png"),
            require("@/assets/img/1.png"),
          ],
          title: "Тайная вечеря",
          author: "Леонардо да Винчи",
          price: "3 000 000",
          isSold: false,
        },
        {
          image: [
            require("@/assets/img/3.png"),
            require("@/assets/img/4.png"),
            require("@/assets/img/1.png"),
            require("@/assets/img/2.png"),
          ],
          title: "Сотворение Адама",
          author: "Микеланджело",
          price: "5 000 000",
          discount: "6 000 000",
          isSold: false,
        },
        {
          image: [
            require("@/assets/img/4.png"),
            require("@/assets/img/1.png"),
            require("@/assets/img/2.png"),
            require("@/assets/img/3.png"),
          ],
          title: "Урок анатомии",
          author: "Рембрандт",
          isSold: true,
        },
      ],
      currentIndex: 0,
      showModal: false, // Управление отображением модального окна
      selectedCard: null, // Текущая выбранная карточка
    };
  },
  computed: {
    filteredCards() {
      return this.cards.filter((card) => {
        return card.title
          .toLowerCase()
          .includes(this.searchQuery.toLowerCase());
      });
    },
  },
  methods: {
    openModal(card) {
      this.selectedCard = card;
      this.currentIndex = 0;
      this.showModal = true;
    },
    closeModal() {
      this.showModal = false;
      this.selectedCard = null;
    },
    prevSlide() {
      this.currentIndex =
        (this.currentIndex - 1 + this.selectedCard.image.length) %
        this.selectedCard.image.length;
    },
    nextSlide() {
      this.currentIndex =
        (this.currentIndex + 1) % this.selectedCard.image.length;
    },
  },
  watch: {
    selectedCard(newCard) {
      if (newCard?.image?.length) {
        this.currentIndex = 0; // Обнуляем индекс при смене товара
      }
    },
  },
};
</script>

<style>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background: white;
  padding: 20px;
  border-radius: 8px;
  width: 80%;
  max-width: 600px;
}

.close {
  color: white;
  position: absolute;
  top: 30px;
  right: 30px;
  font-size: 40px;
  cursor: pointer;
}

.slider {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
.slide-img {
  width: 100%;
  max-height: 400px;
  object-fit: contain;
  border: 2px solid #f6f3f3;
}

.arrow__container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 100%;
  height: 50px;
}

.arrow {
  width: 50px;
  height: 50px;
  font-size: 32px;
  color: #403432;
}

.arrow:hover {
  color: #776763;
}

.main {
  margin-top: 45px;
  width: 100%;
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
}
.main__title {
  margin-bottom: 40px;
}

.main__container {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
  max-width: 1250px;
  width: 100%;
  margin: 0 auto;
  padding: 0 20px;
}

.card__list {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 16px;
}

@media (max-width: 634px) {
  .card__list {
    justify-content: center;
  }
  .main__title {
    text-align: center;
  }
}
</style>
