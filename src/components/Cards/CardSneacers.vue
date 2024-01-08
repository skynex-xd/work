<template>
  <div class="cards">
    <div class="cards__card card hover:-translate-y-2 hover:shadow-xl transition">
      <img
        @click="onClickFavorite"
        class="card__img-like"
        :src="!isFavorite ? '/like-1.svg' : '/like-2.svg'"
        alt="like-1"
      />
      <img class="card__img-snekers" :src="imageUrl" alt="sneakers" />
      <p class="card__name">{{ title }}</p>
      <div class="card__options">
        <div class="card__prices">
          <span>Цена:</span>
          <b>{{ prices }}руб.</b>
        </div>
        <img
          @click="onClickAdd"
          class="card__add"
          :src="!isAdded ? '/plus.svg' : 'checked.svg'"
          alt="plus"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  id: Number,
  imageUrl: String,
  title: String,
  prices: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function
})
</script>

<style scoped>
.cards__card {
  padding: 20px;
  position: relative;
  border: 1px solid;
  border-color: rgb(241 245 249);
  border-radius: 24px;
  background-color: white;
  cursor: pointer;
}

.card__img-like {
  position: absolute;
  top: 20px;
  left: 20px;
}

.card__name {
  margin-top: 5px;
}

.card__prices {
  display: flex;
  flex-direction: column;
  margin-top: 15px;
}

.card__prices span {
  color: rgb(148 163 184);
}

.card__options {
  display: flex;
  justify-content: space-between;
}

/* .cards :hover {
  transform: translateY(8px);
  box-shadow:
    0 20px 25px -5px rgb(0 0 0 / 0.1),
    0 8px 10px -6px rgb(0 0 0 / 0.1);
} */
</style>
