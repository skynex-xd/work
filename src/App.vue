<template>
  <!-- <ShoppingCart /> -->
  <div class="wrapper">
    <HeaderMenu />
    <div class="list-cards">
      <h2>Все кросовки</h2>
      <div class="list-cards__interaction">
        <select @change="onChangeSelect" class="list-cards__filter">
          <option value="name">По названию</option>
          <option value="price">По возрастанию цены</option>
          <option value="-price">По убыванию цены</option>
        </select>
        <div class="list-cards__search">
          <img src="/search.svg" alt="!" />
          <input
            @input="onChangeSearchInput"
            class="list-cards__search-line"
            type="text"
            placeholder="Поиск"
          />
        </div>
      </div>
    </div>
    <CardsList :items="items" @addToFavorite="addToFavorite" />
  </div>
</template>

<script setup>
import { onMounted, ref, reactive, provide, watch } from 'vue'
import axios from 'axios'
import HeaderMenu from '@/components/HeaderMenu.vue'
import CardsList from '@/components/Cards/CardsList.vue'
import ShoppingCart from '@/components/ShoppingCart/ShoppingCart.vue'

const items = ref([])

const filters = reactive({
  sortBy: 'title',
  searchQuery: ''
})

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}

const onChangeSearchInput = (event) => {
  filters.searchQuery = event.target.value
}
const feachFavorites = async () => {
  try {
    const { data: favorites } = await axios.get('https://e6e7fe8de447202a.mokky.dev/favorites')

    items.value = items.value.map((item) => {
      const favorite = favorites.find((favorite) => favorite.parentId === item.id)
      if (!favorite) {
        return item
      }
      return {
        ...item,
        isFavorite: true,
        favoriteId: favorite.id
      }
    })
  } catch (err) {
    console.log(err)
  }
}

const addToFavorite = async (item) => {
  try {
    if (!item.isFavorite) {
      const obj = {
        parantId: item.id
      }

      item.isFavorite = true
      const { data } = await axios.post(`https://e6e7fe8de447202a.mokky.dev/favorites`, obj)

      item.favoriteId = data.id
    } else {
      item.isFavorite = false
      await axios.delete(`https://e6e7fe8de447202a.mokky.dev/favorites/${item.favoriteId}`)
      item.favoriteId = null
    }
  } catch (err) {
    console.log(err)
  }
}
const fatchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy
    }
    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }

    const { data } = await axios.get('https://e6e7fe8de447202a.mokky.dev/items', {
      params
    })
    items.value = data.map((obj) => ({
      ...obj,
      isFavorite: false,
      favoriteId: null,
      isAdded: false
    }))
  } catch (err) {
    console.log(err)
  }
}

onMounted(async () => {
  await fatchItems()
  await feachFavorites()
})

watch(filters, fatchItems)

provide('addToFavorite', addToFavorite)
</script>

<style>
.wrapper {
  max-width: 1370px;
  width: 80%;
  margin: auto;
  background-color: white;
  border-radius: 12px;
  box-shadow:
    0 20px 25px -5px rgb(0 0 0 / 0.5),
    0 8px 10px -6px rgb(0 0 0/0.1);
  margin-top: 56px;
}

.list-cards {
  display: flex;
  justify-content: space-between;
  padding: 30px 40px 20px 40px;
}

h2 {
  font-size: 30px;
  line-height: 36px;
  font-weight: 700;
}

.list-cards__search-line {
  border: 1px solid rgb(241 245 249);
  border-radius: 16px;
  padding: 8px 16px 8px 40px;
  outline: none;
}

.list-cards__search {
  position: relative;
}

.list-cards__search img {
  position: absolute;
  left: 14px;
  top: 12px;
}

.list-cards__search-line:focus {
  border-color: gray;
  transition: 0.5s;
}
.list-cards__interaction {
  display: flex;
  gap: 12px;
}
.list-cards__filter {
  border: 1px solid rgb(241 245 249);
  border-radius: 16px;
  padding: 0px 10px;
  color: gray;
  outline: none;
}
.list-cards__filter:focus {
  border-color: gray;
  transition: 0.5s;
}
</style>
