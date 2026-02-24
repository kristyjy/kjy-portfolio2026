<script setup>

defineProps({
  description: {
    type: String,
    default: null
  },
  image: {
    type: String,
    required: true
  },
  github: {
    type: String,
    default: null
  },
  link: {
    type: String,
    required: true
  },
  title: {
    type: String,
    required: true
  }
})
</script>

<template>
  <article class="project">
    <a :href="link" target="_blank">
      <img :src="image" :alt="`Open Project: ${title}`" />
    </a>
    <h3><a :href="link" target="_blank">{{ title }}</a></h3>
    <p>{{ description }}</p>
    <div class="buttons">
      <a
        :href="link"
        target="_blank"
        class="button"
      >View Project</a>
      <a
        v-if="github"
        :href="github"
        target="_blank"
        class="button"
      >View Code</a>
    </div>
  </article>
</template>

<style scoped>
img {
  display: block;
  max-width: 100%;
  height: auto;
  border: 1px solid #333;
  border-radius: 4px;
}

h3 {
  text-align: center;
  font-size: 2.2rem;
  color: #333;
  margin: 1.5rem 0 1rem;
}

p {
  line-height: 1.3;
  text-align: center;
}

a {
  color: inherit;
  transition: color .3s ease;
}

a:hover {
  color: var(--color1);
}

.buttons {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
}

.button {
  border: 2px solid #333;
  display: inline-block;
  color: #333;
  margin: 0 4px 16px;
  font-weight: bold;
  padding: 16px;
  text-decoration: none;
  transition: all .3s ease;
}

.button:hover {
  color: #fff;
  background: #333;
}

</style>

