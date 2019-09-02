<template>
  <div id="app">
    <h1>Demo for Triangle Component</h1>
    <hr/>
    <h2>Basics</h2>
    <p>
      Draw a simple triangle using:
    </p>
    <code>
      <pre>

        &lt;!-- A unique id attribute is required --&gt;
        &lt;svg height="100" width="100"&gt;
          &lt;Triangle id="triangle-a" /&gt;
        &lt;svg/&gt;
      </pre>
    </code>
    <p>
      This gives the following:
    </p>
    <svg height="100" width="100">
      <Triangle id="triangle-a"/>
    </svg>
    
    <hr/>
    <h2>Optional Properties</h2>
    <p>
      You can also specify the following attributes/props, with their respective default values:
    </p>
    <ul>
      <li>
        <code>&lt;Array&gt; v=[[-25, 0], [25, 0], [0, -50]]</code> - vertices of the triangle
      </li>
      <li>
        <code>&lt;Number&gt; x=50</code> - x-coordinate of triangle's origin (<code>[0, 0]</code>)
      </li>
      <li>
        <code>&lt;Number&gt; y=50</code> - y-coordinate of triangle's origin (<code>[0, 0]</code>)
      </li>
      <li>
        <code>&lt;Number&gt; angle=0</code> - rotation angle about origin (<code>[0, 0]</code>)
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
          &lt;Triangle
            id="triangle-b"
            :v="[[-30, 0], [25, 0], [10, -30]]"
            :angle="45"
            :x="75"
            :y="75"
            fill="#41b883"
            stroke="#2c3e50"
            :stroke-width="3"
            /&gt;
        &lt;svg/&gt;
      </pre>
    </code>
    <svg height="150" width="150">
      <Triangle
        id="triangle-b"
        :v="[[-30, 0], [25, 0], [10, -30]]"
        :angle="45"
        :x="75"
        :y="75"
        fill="#41b883"
        stroke="#2c3e50"
        :stroke-width="3"
        />
    </svg>

    <svg height="200" width="200">
      <EqTriangle
        id="triangle-c"
        :x="100"
        :y="180"
        :length="150"
        fill="#2c3e50"
        />
      <EqTriangle
        id="triangle-d"
        :x="100"
        :y="137"
        :length="100"
        fill="#41b883"
        />
      <EqTriangle
        id="triangle-e"
        :x="100"
        :y="94"
        :length="50"
        fill="#ff9494"
        />
    </svg>
    <!-- <svg height="100" width="100">
      <Triangle
        id="sector-a"
        :v="v"
        @click="test"
        style="cursor: pointer;"
        />
    </svg> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Triangle from '../components/Triangle.vue'
import EqTriangle from '../components/EqTriangle.vue'

export default {
  name: 'app',
  components: {
    Triangle,
    EqTriangle
  },
  data() {
    return {
      v: [
            [-25, 0],
            [25, 0],
            [0, -25],
          ],
      len: 50,
    }
  },
  methods: {
    test() {
      if (this.v[2][1] === 25) {
        this.v = [
          [-25, 0],
          [25, 0],
          [0, -25],
        ]
      } else {
        this.v = [
          [-25, 0],
          [25, 0],
          [0, 25],
        ]
      }
    },
    double() {
      if (this.len === 25) this.len = 50;
      else this.len = 25;
    }
  }
}
</script>

<style>
</style>
