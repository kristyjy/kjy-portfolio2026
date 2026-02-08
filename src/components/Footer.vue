<script setup>
  import IconCodepen from "./icons/IconCodepen.vue";
  import IconEmail from "./icons/IconEmail.vue";
  import IconGithub from "./icons/IconGithub.vue";
  import IconHeart from "./icons/IconHeart.vue";
  import IconLinkedIn from "./icons/IconLinkedIn.vue";
</script>

<template>
  <footer>
    <div class="container">
      <p>Made with <IconHeart class="heart" /> by Kristy Yeaton</p>
      <div class="social">
        <ul>
          <li>
            <a class="icon-link" href="mailto:kristyjy@gmail.com">
              <IconEmail />
            </a>
          </li>
          <li>
            <a class="icon-link" href="http://codepen.io/kristyjy/">
              <IconCodepen />
            </a>
          </li>
          <li>
            <a class="icon-link" href="https://www.linkedin.com/pub/kristy-yeaton/26/6a0/a97">
              <IconLinkedIn />
            </a>
          </li>
          <li>
            <a class="icon-link" href="https://github.com/kristyjy">
              <IconGithub />
            </a>
          </li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<style scoped>
footer {
  background-color: #333;
  color: #fff;
  padding: 2rem 0 4rem;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

p {
  margin: 0;
  text-align: center;
  font-family: var(--font-heading);
}

.heart {
  color: var(--color1);
  width: 1.8rem;
  height: 1.8rem;
}

ul {
  margin: 2rem 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  list-style: none;
}

li {
  margin: 0 .5rem;
}

.icon-link {
  color: var(--color1);
  transition: all .6s ease;
}

.icon-link:hover {
  color: #fff;
}
</style>