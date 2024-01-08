<template>
  <div class="carts-item">
    <img src="/sneakers/sneakers-1.jpg" alt="cards-icons" />
    <div class="carts-item__information">
      <p>Кросовки Nike Air Max 270</p>
      <b>12999 руб.</b>
    </div>
    <div class="carts-item__delite">
      <svg
        width="32"
        height="32"
        viewBox="0 0 32 32"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <rect x="0.5" y="0.5" width="31" height="31" rx="7.5" fill="white" stroke="#DBDBDB" />
        <path
          d="M20.0799 18.6155L17.6311 16.1667L20.0798 13.718C21.0241 12.7738 19.5596 11.3093 18.6154 12.2536L16.1667 14.7023L13.7179 12.2535C12.7738 11.3095 11.3095 12.7738 12.2535 13.7179L14.7023 16.1667L12.2536 18.6154C11.3093 19.5596 12.7738 21.0241 13.718 20.0798L16.1667 17.6311L18.6155 20.0799C19.5597 21.0241 21.0241 19.5597 20.0799 18.6155Z"
          fill="#DBDBDB"
        />
      </svg>
    </div>
  </div>
</template>

<script setup></script>

<style scoped>
.carts-item {
  display: flex;
  align-items: center;
  border: 1px solid rgb(241 245 249);
  border-radius: 24px;
  padding: 16px;
  gap: 15px;
  margin-bottom: 15px;
}
.carts-item img {
  max-height: 72px;
  max-width: 72px;
}
.carts-item__information {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
.carts-item__information p {
  font-size: 14px;
}
.carts-item__information b {
  font-size: 14px;
}
.carts-item__delite rect:hover {
  fill: rgb(255, 120, 120);
  transition: 0.5s;
}
</style>
