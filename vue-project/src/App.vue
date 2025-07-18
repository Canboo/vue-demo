<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import DialogComp from './components/DialogComp.vue'

const users = [
  { name: '林志玲', description: '知名模特兒與演員，優雅知性代表' },
  { name: '周杰倫', description: '亞洲流行音樂天王，擅長混搭多種音樂風格' },
  { name: '蔡依林', description: '流行天后，風格多變且舞台魅力十足' },
  { name: '吳宗憲', description: '資深綜藝主持人與歌手，以幽默風趣著稱' },
  { name: '羅志祥', description: '歌手與主持人，舞蹈實力與綜藝感兼具' },
  { name: '楊丞琳', description: '從偶像劇起家的全方位藝人' },
  { name: '王力宏', description: '創作型歌手，融合中西音樂文化' },
  { name: '柯佳嬿', description: '實力派演員，以戲劇作品打動人心' },
  { name: '吳慷仁', description: '金馬獎影帝，擅長詮釋深層角色' },
  { name: '陳妍希', description: '甜美系女星，以青春形象著稱' },
]
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

      <DialogComp
        v-for="user in users"
        :key="user.name"
        :btnText="user.name"
        :description="user.description"
      />
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
.bg {
  height: 100px;
}
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
