<script setup>
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import DialogComp from './components/DialogComp.vue'
import data from './data/data.js'

const arr = ref(data)
const randomItem = () => {
  arr.value.sort(() => Math.random() - 0.5)
}

import axios from 'axios'
const posts = ref([])
const loadData = async () => {
  const response = await axios.get('https://jsonplaceholder.typicode.com/posts')
  // 隨機從 posts 中選擇 10 筆資料
  posts.value = response.data.sort(() => 0.5 - Math.random()).slice(0, 3)
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
      <v-btn text="隨機排列資料" variant="flat" @click="randomItem" color="primary"></v-btn>
      <div v-for="(group, index) in arr" :key="index">
        <h3>{{ group.title }}</h3>
        <DialogComp
          v-for="(item, cindex) in group.items"
          :key="cindex"
          :btnText="item.name"
          :description="item.description"
        />
      </div>
      <div>
        <v-btn text="載入資料" variant="flat" @click="loadData" color="primary"></v-btn>
        <v-data-table :items="posts"></v-data-table>
      </div>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
