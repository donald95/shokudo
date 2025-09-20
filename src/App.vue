<template>
  <main>
    <h1>NIGIRI - にぎり</h1>
    <div class="grid-container">
      <v-card
        class="flex-grow-1 d-flex flex-column"
        v-for="menuItem in sushiItems"
        :key="menuItem.id"
      >
        <v-img height="260" :src="menuItem.photo" cover></v-img>

        <v-divider class="mx-4 mb-1"></v-divider>

        <v-card-item>
          <v-card-title style="display: flex; justify-content: space-between; flex-wrap: wrap">
            <h4>{{ menuItem.title }}</h4>
            <div>{{ menuItem.price }}円</div>
          </v-card-title>

          <v-card-subtitle>
            <span class="me-1">{{ menuItem.calories }}kcal</span>
            <v-icon color="error" icon="mdi-fire-circle" size="small"></v-icon>
          </v-card-subtitle>
        </v-card-item>

        <v-card-text class="flex-grow-1">
          <div>{{ menuItem.description }}</div>
          <small style="color: rgba(0, 0, 0, 0.5)">{{ menuItem.translatedDescription }}</small>
        </v-card-text>

        <v-divider class="mx-4 mb-1"></v-divider>

        <v-card-actions>
          <button class="btn-reserve" @click.prevent="reserve">よやくする</button>
        </v-card-actions>
      </v-card>
    </div>
    <h1>COMPLEMENTOS - サイドメニュー</h1>
    <div class="grid-container">
      <v-card
        class="flex-grow-1 d-flex flex-column"
        v-for="menuItem in complementItems"
        :key="menuItem.id"
      >
        <v-img height="260" :src="menuItem.photo" cover></v-img>

        <v-divider class="mx-4 mb-1"></v-divider>

        <v-card-item>
          <v-card-title style="display: flex; justify-content: space-between; flex-wrap: wrap">
            <h4>{{ menuItem.title }}</h4>
            <div>{{ menuItem.price }}円</div>
          </v-card-title>

          <v-card-subtitle>
            <span class="me-1">{{ menuItem.calories }}kcal</span>
            <v-icon color="error" icon="mdi-fire-circle" size="small"></v-icon>
          </v-card-subtitle>
        </v-card-item>

        <v-card-text class="flex-grow-1">
          <div>{{ menuItem.description }}</div>
          <small style="color: rgba(0, 0, 0, 0.5)">{{ menuItem.translatedDescription }}</small>
        </v-card-text>

        <v-divider class="mx-4 mb-1"></v-divider>

        <v-card-actions>
          <button class="btn-reserve" @click.prevent="reserve">よやくする</button>
        </v-card-actions>
      </v-card>
    </div>
    <h1>BEBIDAS - 飲み物</h1>
    <div class="grid-container">
      <v-card
        class="flex-grow-1 d-flex flex-column"
        v-for="menuItem in drinkItems"
        :key="menuItem.id"
      >
        <v-img height="260" :src="menuItem.photo" cover></v-img>

        <v-divider class="mx-4 mb-1"></v-divider>

        <v-card-item>
          <v-card-title style="display: flex; justify-content: space-between; flex-wrap: wrap">
            <h4>{{ menuItem.title }}</h4>
            <div>{{ menuItem.price }}円</div>
          </v-card-title>

          <v-card-subtitle>
            <span class="me-1">{{ menuItem.calories }}kcal</span>
            <v-icon color="error" icon="mdi-fire-circle" size="small"></v-icon>
          </v-card-subtitle>
        </v-card-item>

        <v-card-text class="flex-grow-1">
          <div>{{ menuItem.description }}</div>
          <small style="color: rgba(0, 0, 0, 0.5)">{{ menuItem.translatedDescription }}</small>
        </v-card-text>

        <v-divider class="mx-4 mb-1"></v-divider>

        <v-card-actions>
          <button class="btn-reserve" @click.prevent="reserve">よやくする</button>
        </v-card-actions>
      </v-card>
    </div>
    <footer
      style="
        text-align: center;
        padding: 10px;
        background-color: #f5f5f5;
        font-family: Arial, sans-serif;
      "
    >
      <p>© <span id="year">{{ year }}</span> Hecho con ❤️ por Donald Munguía</p>
    </footer>
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import sushiData from '@/assets/data/nigiri.json' with { type: 'json' }
import complementData from '@/assets/data/complement.json' with { type: 'json' }
import drinkData from '@/assets/data/drinks.json' with { type: 'json' }

const year = ref(new Date().getFullYear())

const sushiItems = ref(
  sushiData.map((item) => ({
    ...item,
    photo: new URL(`/src/assets/images/nigiri/${item.photo}`, import.meta.url).href,
  })),
)

const complementItems = ref(
  complementData.map((item) => ({
    ...item,
    photo: new URL(`/src/assets/images/complement/${item.photo}`, import.meta.url).href,
  })),
)

const drinkItems = ref(
  drinkData.map((item) => ({
    ...item,
    photo: new URL(`/src/assets/images/drinks/${item.photo}`, import.meta.url).href,
  })),
)

function reserve() {
  alert('よやくしました')
}
</script>

<style scoped>
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
  padding: 10px;
}

.btn-reserve {
  color: white;
  background-color: #673ab7;
  border: 1px solid transparent;
  width: 100%;
  padding: 12px 24px;
  border-radius: 3px;
  cursor: pointer;
  transition: 0.3s;
}

.btn-reserve:hover {
  color: #673ab7;
  background-color: white;
  border: 1px solid #673ab7;
}

.btn-reserve:active {
  background-color: #eeeeee;
}
</style>
