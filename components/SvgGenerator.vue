<template>
  <svg id="generated-svg">
    <title>{{title}}</title>
    <path v-for="path in paths" v-bind="path"/>
  </svg>
</template>


<script>
import rough from 'roughjs/bundled/rough.cjs.js';

export default {
  props: ['title', 'nb', 'color'],
  computed: {
    paths() {
      let generator = rough.generator();
      let paths = []
      for (let i = 0; i < this.nb; i++) {
        let rectangle = generator.rectangle(100 * i, 10, 80, 80, {fill: this.color});
        paths.push(generator.toPaths(rectangle))
      }
      return paths.flat()
    }
  }
}
</script>
