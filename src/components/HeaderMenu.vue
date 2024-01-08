<template>
  <header class="header">
    <div class="header__greeting">
      <img src="/logo.png" alt="Logo" class="header__logo" />
      <div class="header__name">
        <h2>Vue Sneakers</h2>
        <p>Магази лучших кросовок</p>
      </div>
    </div>
    <ul class="header__menu">
      <li class="menu__item">
        <img src="/cart.svg" alt="Cart" />
        <b>1205 руб.</b>
      </li>
      <li class="menu__item">
        <img src="/heart.svg" alt="Heart" />
        <b>Закладки</b>
      </li>
      <li class="menu__item">
        <img src="/profile.svg" alt="Profile" />
        <b>Профиль</b>
      </li>
    </ul>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  border-bottom-width: 1px;
  border-color: rgb(226 232 240);
  padding: 24px 40px;
}
.header__logo {
  width: 40px;
}
.header__greeting {
  display: flex;
  align-items: center;
  gap: 16px;
}
.header__name h2 {
  font-size: 20px;
  line-height: 28px;
  font-weight: 700;
  text-transform: uppercase;
  gap: 40px;
}
.header__name p {
  color: rgb(148 163 184);
}
.header__menu {
  display: flex;
  align-items: center;
  gap: 40px;
}
.menu__item {
  display: flex;
  align-items: center;
  gap: 12px;
  color: rgb(148 163 184);
}

.menu__item:hover {
  color: black;
  cursor: pointer;
  transition: 0.8s;
}
</style>
