<script setup>
import { ref } from 'vue'

import mineSweeperArt from '../assets/images/minesweeper.jpg';
import vicesIncCom from '../assets/images/vicesinc-com.jpg';
import vicesIncShop from '../assets/images/vicesinc-shop.jpg';
import Project from './Project.vue'

const projects = ref([
  {
    title: 'Vices Inc Dot Com',
    description: "A marketing website for the band Vices Inc built with the static site generator Hugo.",
    link: "https://vicesinc.com",
    github: "https://github.com/kristyjy/vicesinc",
    image: vicesIncCom
  },
  {
    title: 'Vices Inc Merch Shop',
    description: "An online store for the band Vices Inc built in Shopify.",
    link: "https://vicesinc.myshopify.com/collections/all",
    image: vicesIncShop
  },
  {
    title: 'Minesweeper',
    description: "A Minesweeper clone built in Vue 3.",
    link: "https://kristyyeaton.com/minesweeper",
    github: "https://github.com/kristyjy/minesweeper",
    image: mineSweeperArt
  }
])
</script>

<template>
  <section class="projects">
    <h2>My Projects</h2>
    <div class="projects-grid">
      <Project
        v-for="project in projects"
        :key="project.title"
        :title="project.title"
        :description="project.description"
        :link="project.link"
        :github="project.github"
        :image="project.image"
      />
    </div>
  </section>
</template>

<style scoped>
.projects {
  background-color: #fff;
  padding-bottom: 10vh;
  position: relative;
}

.projects:after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 0 0 10vh 100vw;
  border-color: transparent transparent #333 transparent;
}

h2 {
  text-align: center;
  font-size: 2.5rem;
  color: var(--color1);
  margin: 0 0 2rem;
}

@media (min-width: 768px) {
  h2 {
    font-size: 3rem;
  }
}

@media (min-width: 1100px) {
  h2 {
    font-size: 4rem;
  }
}

.projects-grid {
  display: grid;
  gap: 30px;
  grid-template-columns: repeat(auto-fit, minmax(min(300px, 100%), 1fr));
  max-width: 1400px;
  margin: 0 auto;
  padding: 30px;
}
</style>
