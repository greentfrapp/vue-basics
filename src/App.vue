<template>
  <div id="app">
    <svg height="300" width="300" @click="update">
      <CircleSector
        id="a"
        :r="50"
        :cx="50"
        :cy="50"
        :startAngle="a"
        :endAngle="0.5"
        fill="#FF0000"
        />
      <CircleSector
        id="b"
        :r="50"
        :cx="150"
        :cy="50"
        :startAngle="0"
        :endAngle="0.25"
        fill="#0000FF"
        />
    </svg>

  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import CircleSector from './components/CircleSector.vue'

export default {
  name: 'app',
  components: {
    CircleSector
  },
  data() {
    return {
      a: 0,
    }
  },
  methods: {
    update() {
      if (this.a === 0.3) {
        this.a = 0;
      } else {
        this.a = 0.3;
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
