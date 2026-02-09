<script setup>
  import * as d3 from 'd3'
  import { onMounted, ref } from 'vue'

  const svg = ref(null)

  const skills = ref({
    children: [
      {
        label: 'HTML5',
        size: 550,
        color: 'rgba(255, 86, 124, 1)'
      },
      {
        label: 'CSS3',
        size: 600,
        color: '#85c6bf'
      },
      {
        label: 'JavaScript',
        size: 500,
        color: '#777'
      },
      {
        label: 'Storybook',
        size: 300,
        color: '#777'
      },
      {
        label: 'VueJS',
        size: 400,
        color: '#cc4562'
      },
      {
        label: 'ReactJS',
        size: 400,
        color: '#cc4562'
      },
      {
        label: 'Vite',
        size: 300,
        color: 'rgba(255, 86, 124, 1)'
      },
      {
        label: 'TypeScript',
        size: 200,
        color: '#cc4562'
      },
      {
        label: 'Pinia',
        size: 200,
        color: 'rgba(255, 86, 124, 1)'
      },
      {
        label: 'Webpack',
        size: 150,
        color: '#85c6bf'
      },
      {
        label: 'Figma',
        size: 150,
        color: '#777'
      },
      {
        label: 'SCSS',
        size: 150,
        color: '#77ada7'
      },
      {
        label: 'Git',
        size: 100,
        color: '#85c6bf'
      },
      {
        label: 'Hugo',
        size: 100,
        color: '#77ada7'
      },
      {
        label: 'D3',
        size: 100,
        color: 'rgba(255, 86, 124, 1)'
      },
      {
        label: 'jQuery',
        size: 100,
        color: '#85c6bf'
      }
    ]
  })

  let width = ref(300)
  let height = ref(300)

  function renderChart() {
    var bubble = d3.pack(skills.value)
      .size([width.value, height.value])
      .padding(2)

    const selection = d3.select(svg.value)

    selection
      .html("")
      .attr("width", width.value)
      .attr("height", height.value)
      .attr("class", "bubble")

    var nodes = d3.hierarchy(skills.value)
      .sum(function(d) { return d.size; })

    var node = selection.selectAll(".node")
      .data(bubble(nodes).descendants())
      .enter()
      .filter(function(d){
        return !d.children
      })
      .append("g")
      .attr("class", "node")
      .attr("transform", function(d) {
        return "translate(" + d.x + "," + d.y + ")"
      })

    node.append("title")
      .text(function(d) {
        return d.data.label
      })

    node.append("circle")
      .attr("r", function(d) {
          return d.r
      })
      .style("fill", function(d) {
          return d.data.color
      })

    node.append("text")
      .attr("dy", ".4em")
      .style("text-anchor", "middle")
      .text(function(d) {
        return d.data.label.substring(0, d.r / 3)
      })
      .attr("font-family",  "Open Sans")
      .attr("font-size", function(d){
          return d.r/3
      })
      .attr("fill", "white")

    d3.select(self.frameElement)
      .style("height", height.value + "px")
  }

  function onResize() {
    width.value = window.innerWidth;
      if (window.innerWidth < window.innerHeight * .8) {
        height.value = window.innerWidth
      }
      else {
        height.value = window.innerHeight * .8
      }
      renderChart()
  }

  onMounted(() => {
    onResize()
    window.addEventListener('resize', onResize, false)
  })

</script>

<template>
  <svg ref="svg"></svg>
</template>

<style scoped>
svg {
  width: 100%;
  height: auto;
  display: block;
}
</style>
