<template>
  <g :id="id">
    <path @click="$emit('click')"/>
  </g>
</template>

<script type="text/javascript">
  import * as d3 from "d3";

  export default {
    name: 'CircleSector',
    props: {
      id: {
        required: true,
        type: String,
      },
      r: {
        type: Number,
        default: 50,
      },
      cx: {
        type: Number,
        default: 50,
      },
      cy: {
        type: Number,
        default: 50,
      },
      startAngle: {
        type: Number,
        default: 0,
      },
      endAngle: {
        type: Number,
        default: 0.5,
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
      startAngle() {
        this.updateSector()
      },
      endAngle() {
        this.updateSector()
      },
      r() {
        this.updateSector()
      },
    },
    mounted() {
      d3.select(`g#${this.id}`)
        .attr('transform', `translate(${this.cx}, ${this.cy})`);
      d3.select(`g#${this.id} > path`)
        .datum({
          innerRadius: 0,
          outerRadius: this.r,
          startAngle: 2 * Math.PI * this.startAngle,
          endAngle: 2 * Math.PI * this.endAngle,
        })
        .attr('d', this.arc)
        .attr('fill', this.fill)
        .attr('fill-opacity', this.fillOpacity)
        .attr('stroke', this.stroke)
        .attr('stroke-opacity', this.strokeOpacity)
        .attr('stroke-width', `${this.strokeWidth}px`);
    },
    data() {
      return {
        arc: d3.arc()
      }
    },
    methods: {
      arcTween({r=null, start=null, end=null, degrees=false, shift=0}) {
        let self = this;
        return function(d) {
          if (r === null) r = d.outerRadius
          if (start === null) {
            start = d.startAngle
          } else if (degrees) {
            start = Math.radians(start)
          }
          if (end === null) {
            end = d.endAngle
          } else if (degrees) {
            end = Math.radians(end)
          }
          start += shift
          end += shift

          var interRadius = d3.interpolate(d.outerRadius, r),
          interStartAngle = d3.interpolate(d.startAngle, start),
          interEndAngle = d3.interpolate(d.endAngle, end)
          return function(t) {
            d.outerRadius = interRadius(t)
            d.startAngle = interStartAngle(t)
            d.endAngle = interEndAngle(t)
            return self.arc(d)
          }
        }
      },
      updateSector() {
        d3.select(`g#${this.id} > path`)
          .transition()
          .duration(500)
          .attrTween('d', this.arcTween({
            r: this.r,
            start: 2 * Math.PI * this.startAngle,
            end: 2 * Math.PI * this.endAngle,
          }));
      }
    }
  }
</script>
