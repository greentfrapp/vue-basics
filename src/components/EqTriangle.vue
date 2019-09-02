<template>
  <Triangle
    :id="id"
    :v="v"
    :x="x"
    :y="y"
    :fill="fill"
    :fill-opacity="fillOpacity"
    :stroke="stroke"
    :stroke-opacity="strokeOpacity"
    :stroke-width="strokeWidth"
    @click="$emit('click')"
    />
</template>

<script type="text/javascript">
  import Triangle from '../components/Triangle.vue'

  export default {
    name: 'EqTriangle',
    components: {
      Triangle,
    },
    props: {
      id: {
        required: true,
        type: String,
      },
      length: {
        type: Number,
        default: 50,
      },
      x: {
        type: Number,
        default: 50,
      },
      y: {
        type: Number,
        default: 50,
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
    watch: {},
    mounted() {},
    computed: {
      v() {
        return [
              [-0.5 * this.length, 0],
              [0.5 * this.length, 0],
              [0, -0.866 * this.length],
            ]
      }
    },
    data() {
      return {}
    },
    methods: {}
  }
</script>
