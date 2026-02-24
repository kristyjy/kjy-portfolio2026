<script setup>
  import { onMounted, ref } from 'vue'

  const particles = ref([])
  const tick = ref(0)
  const colors = ref([
    '255, 86, 124',
    '153, 225, 217',
    '255, 255, 255'
  ])
  const width = ref(1080)
  const height = ref(800)
  const canvas = ref(null)

  function createParticles() {
    if (tick.value % 10 == 0 && particles.value.length < 50) {
      particles.value.push({ 
        x: Math.random() * width.value, 
        y: 0,
        speed: 1 + Math.random() * 1.5,
        radius: 5 + Math.random() * 10,
        color: getRandomColor()
      })
    }
  }

  function drawParticles() {
    if (!canvas.value) return
    const c = canvas.value.getContext('2d')
    c.clearRect(0, 0, window.innerWidth, window.innerHeight)
    c.fillStyle = "transparent"
    c.fillRect(0, 0, window.innerWidth, window.innerHeight)

    particles.value.map(function(p) {
      c.beginPath()
      c.arc(p.x, p.y, p.radius, 0, Math.PI * 2)
      c.closePath()
      c.fillStyle = p.color
      c.fill()
    })
  }

  function getRandomColor() {
    return 'rgba(' + colors.value[Math.floor(getRandomNum(0,3))] + ',' + getRandomNum(.2, .8) + ')'
  }

  function getRandomNum(min, max) {
    return Math.random() * (max - min) + min
  }

  function loop() {
    window.requestAnimationFrame(loop) 
    createParticles()
    updateParticles()
    drawParticles()
    tick.value++
  }

  function onResize() {
    width.value = window.innerWidth
    height.value = window.innerHeight
  }

  function updateParticles() {
    particles.value = particles.value.map(function(p) {
      p.y += p.speed
      if (p.y > height.value) { 
        p.y = 0;
        p.x = Math.random() * window.innerWidth
      }
      return p
    })
  }

  onMounted(() => {
    window.requestAnimationFrame(loop)
    onResize()
    window.addEventListener('resize', onResize, false)
  })
</script>

<template>
  <canvas ref="canvas" :width="width" :height="height"></canvas>
</template>

<style scoped>
canvas {
  display: block;
}
</style>
