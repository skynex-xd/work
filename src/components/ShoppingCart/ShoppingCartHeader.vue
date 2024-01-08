<template>
  <div class="cart__header">
    <svg width="16" height="14" viewBox="0 0 16 14" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path
        d="M1 7H14.7143"
        stroke="black"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      />
      <path
        d="M8.71436 1L14.7144 7L8.71436 13"
        stroke="black"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      />
    </svg>
    <h2 class="cart__title">Корзина</h2>
  </div>
</template>

<style scoped>
.cart__header h2 {
  font-size: 24px;
  line-height: 32px;
}
.cart__header {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-bottom: 15px;
}
.cart__header svg {
  opacity: 30%;
  cursor: pointer;
  transform: rotate(180deg);
}
.cart__header svg:hover {
  opacity: 100%;
  transition: 0.5s;
  /* transform: translateX(4px); */
}
</style>
