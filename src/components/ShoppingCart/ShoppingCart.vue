<template>
  <div class="cart">
    <div class="cart__background"></div>
    <div class="cart__contents">
      <HeaderCart />

      <CardsItemList />

      <div class="cart__result">
        <div class="cart__cost">
          <span>Итого</span>
          <div></div>
          <b>12000 ₽</b>
        </div>
        <div class="cart__discount">
          <span>Скидка</span>
          <div></div>
          <b>999 ₽</b>
        </div>
        <button disabled="" class="cart__order order">Оформит заказ</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import HeaderCart from '@/components/ShoppingCart/ShoppingCartHeader.vue'
import CardsItemList from '@/components/Cards/CartItemList.vue'
</script>

<style scoped>
.cart__background {
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  background-color: black;
  z-index: 1;
  opacity: 60%;
}
.cart__contents {
  position: fixed;
  top: 0;
  right: 0;
  height: 100%;
  width: 384px;
  background-color: white;
  z-index: 2;
  padding: 32px;
}
.cart__result {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin: 20px 0;
}

.cart__cost,
.cart__discount {
  display: flex;
  gap: 5px;
  justify-content: space-between;
}
.cart__cost div,
.cart__discount div {
  flex: 1 1 0%;
  border-bottom: 1px dashed black;
  margin-bottom: 4px;
}
.cart__order {
  background-color: rgb(132 204 22);
  width: 100%;
  justify-content: center;
  border-radius: 12px;
  background-size: 100% 100%;
  padding: 12px;
  color: white;
  cursor: pointer;
}
.cart__order:hover {
  transition: 0.3s;
  background-color: rgb(101 163 13);
}
.cart__order:active {
  background-color: rgb(163 230 53);
}
.cart__order:disabled {
  background-color: slategray;
}
.order {
  margin-top: 10px;
}
.cart__discount b {
  color: green;
}
</style>
