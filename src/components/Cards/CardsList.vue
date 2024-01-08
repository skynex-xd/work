<template>
  <div class="list-cards__grid">
    <CardSneacers
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :image-url="item.imageUrl"
      :prices="item.price"
      :onClickFavorite="() => emit('addToFavorite', item)"
      :isFavorite="item.isFavorite"
    />
  </div>
</template>

<script setup>
import CardSneacers from '@/components/Cards/CardSneacers.vue'

defineProps({
  items: Array
})

const emit = defineEmits('addToFavorite')
</script>

<style scoped>
.list-cards__grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 20px;
  padding: 20px 40px;
}
</style>
