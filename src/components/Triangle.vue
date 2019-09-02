<template>
  <g :id="id">
    <path @click="$emit('click')"/>
  </g>
</template>

<script type="text/javascript">
  import * as d3 from "d3";

  export default {
    name: 'Triangle',
    props: {
      id: {
        required: true,
        type: String,
      },
      x: {
        type: Number,
        default: 50,
      },
      y: {
        type: Number,
        default: 50,
      },
      v: {
        type: Array,
        default: function() {
          return [
            [-25, 0],
            [25, 0],
            [0, -50],
          ]
        }
      },
      angle: {
        type: Number,
        default: 0,
      },
      fill: {
        type: String,
        default: '#000000',
      },
      fillOpacity: {
        type: Number,
        default: 1,
      },
      stroke: {
        type: String,
        default: '#000000',
      },
      strokeOpacity: {
        type: Number,
        default: 1,
      },
      strokeWidth: {
        type: Number,
        default: 1,
      },
    },
    watch: {
      angle() {
        d3.select(`g#${this.id}`)
          .transition()
          .duration(500)
          .attr('transform-origin', `${this.x}, ${this.y}`)
          .attr('transform', `translate(${this.x}, ${this.y}) rotate(${this.angle})`)
      },
      v() {
        d3.select(`g#${this.id} > path`)
          .transition()
          .duration(500)
          .attrTween('d', this.tween(this.v));
      },
    },
    mounted() {
      d3.select(`g#${this.id}`)
        .attr('transform-origin', `${this.x}, ${this.y}`)
        .attr('transform', `translate(${this.x}, ${this.y}) rotate(${this.angle})`)
      d3.select(`g#${this.id} > path`)
        .attr('d', `M ${this.v[0][0]} ${this.v[0][1]} L ${this.v[1][0]} ${this.v[1][1]} L ${this.v[2][0]} ${this.v[2][1]} Z`)
        .attr('fill', this.fill)
        .attr('fill-opacity', this.fillOpacity)
        .attr('stroke', this.stroke)
        .attr('stroke-opacity', this.strokeOpacity)
        .attr('stroke-width', `${this.strokeWidth}px`);
    },
    data() {
      return {}
    },
    methods: {
      tween(v) {
        return function(d, i, a) {
          let val = d3.select(a[0]).attr('d'),
          currentXY1 = val.split('M ')[1].split(' Z')[0].split(' L ')[0].split(' '),
          currentXY2 = val.split('M ')[1].split(' Z')[0].split(' L ')[1].split(' '),
          currentXY3 = val.split('M ')[1].split(' Z')[0].split(' L ')[2].split(' '),
          x1 = d3.interpolate(currentXY1[0], v[0][0]),
          y1 = d3.interpolate(currentXY1[1], v[0][1]),
          x2 = d3.interpolate(currentXY2[0], v[1][0]),
          y2 = d3.interpolate(currentXY2[1], v[1][1]),
          x3 = d3.interpolate(currentXY3[0], v[2][0]),
          y3 = d3.interpolate(currentXY3[1], v[2][1])
          return function(t) {
            return `M ${x1(t)} ${y1(t)} L ${x2(t)} ${y2(t)} L ${x3(t)} ${y3(t)} Z`
          }
        }
      },
    }
  }
</script>
