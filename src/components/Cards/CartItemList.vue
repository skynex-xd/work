<template>
  <div class="list-cart">
    <CardsItem />
  </div>
</template>

<script setup>
import CardsItem from '@/components/Cards/CartItem.vue'
</script>

<style scoped>
.list-cart {
  display: flex;
  flex-direction: column;
}
</style>
