<template>
  <svg id="generated-svg">
    <title>{{title}}</title>
  </svg>
</template>


<script>
import rough from 'roughjs/bundled/rough.cjs.js';

export default {
  props: ['title', 'nb', 'color'],
  mounted() {
    let svg = document.getElementById('generated-svg')
    const rc = rough.svg(svg);
    for (let i = 0; i < this.nb; i++) {
      let node = rc.rectangle(100 * (i), 10, 80, 80, { fill: this.color });
      svg.appendChild(node);
    }
  }
}
</script>
