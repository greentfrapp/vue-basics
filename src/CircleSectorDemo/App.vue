<template>
  <div id="app">
    <h1>Demo for Circle Sector Component</h1>
    <hr/>
    <h2>Basics</h2>
    <p>
      Draw a circle sector using:
    </p>
    <code>
      <pre>

        &lt;!-- A unique id attribute is required --&gt;
        &lt;svg height="100" width="100"&gt;
          &lt;CircleSector id="sector-a" /&gt;
        &lt;svg/&gt;
      </pre>
    </code>
    <p>
      This gives the following:
    </p>
    <svg height="100" width="100">
      <CircleSector id="sector-a" />
    </svg>
    <hr/>
    <h2>Optional Properties</h2>
    <p>
      You can also specify the following attributes/props, with their respective default values:
    </p>
    <ul>
      <li>
        <code>&lt;Number&gt; r=50</code> - radius of sector's circle
      </li>
      <li>
        <code>&lt;Number&gt; cx=50</code> - x-coordinate of sector's circle center
      </li>
      <li>
        <code>&lt;Number&gt; cy=50</code> - y-coordinate of sector's circle center
      </li>
      <li>
        <code>&lt;Number&gt; startAngle=0</code> - starting angle, by proportion from 0 to 1
      </li>
      <li>
        <code>&lt;Number&gt; endAngle=0.5</code> - ending angle, by proportion from 0 to 1
      </li>
      <li>
        <code>&lt;String&gt; fill=#000000</code> - fill color
      </li>
      <li>
        <code>&lt;Number&gt; fill-opacity=1</code> - fill opacity
      </li>
      <li>
        <code>&lt;String&gt; stroke=#000000</code> - stroke color
      </li>
      <li>
        <code>&lt;Number&gt; stroke-opacity=1</code> - stroke opacity
      </li>
      <li>
        <code>&lt;Number&gt; stroke-width=1</code> - stroke width
      </li>
    </ul>
    <p>
      An example:
    </p>
    <code>
      <pre>

        &lt;svg height="150" width="150"&gt;
          &lt;CircleSector
            id="sector-b"
            :cx="75"
            :cy="75"
            :startAngle="0.25"
            :endAngle="0.75"
            fill="#41b883"
            stroke="#2c3e50"
            :stroke-width="3"
            /&gt;
        &lt;svg/&gt;
      </pre>
    </code>
    <svg height="150" width="150">
      <CircleSector
        id="sector-b"
        :cx="75"
        :cy="75"
        :startAngle="0.25"
        :endAngle="0.75"
        fill="#41b883"
        stroke="#2c3e50"
        :stroke-width="3"
        />
    </svg>
    <hr/>
    <h2>Interactivity</h2>
    <p>
      The component can be made interactive by simply binding and changing the values of the <code>r</code>, <code>startAngle</code> and <code>endAngle</code> attributes.
    </p>
    <p>
      Try clicking on the following sectors!
    </p>
    <svg height="150" width="150">
      <CircleSector
        style="cursor: pointer;"
        id="sector-c"
        :r="r"
        :cx="75"
        :cy="75"
        :startAngle="0.25"
        :endAngle="0.75"
        fill="#41b883"
        stroke="#2c3e50"
        :stroke-width="3"
        @click="changeR"
        />
    </svg>
    <svg height="150" width="150">
      <CircleSector
        id="sector-d"
        :r="50"
        :cx="75"
        :cy="75"
        :startAngle="start"
        :endAngle="end"
        fill="#41b883"
        stroke="#2c3e50"
        :stroke-width="3"
        @click="changeAngle"
        style="cursor: pointer;"
        />
    </svg>
    
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import CircleSector from '../components/CircleSector.vue'

export default {
  name: 'app',
  components: {
    CircleSector
  },
  data() {
    return {
      r: 50,
      start: 0,
      end: 0.5
    }
  },
  methods: {
    changeR() {
      if (this.r === 20) this.r = 50;
      else this.r = 20;
    },
    changeAngle() {
      if (this.start === 0) {
        this.start = 0.5;
        this.end = 1.0;
      }
      else {
        this.start = 0;
        this.end = 0.5;
      }
    }
  }
}
</script>

<style>
</style>
