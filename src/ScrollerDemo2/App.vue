<template>
  <div id="app">
    <h1>Scroller Demo</h1>
    <hr />
    <div id="section-1">
      <h2>Section 1</h2>
      <p>
        In ut voluptate proident sint et non eu magna sint exercitation reprehenderit dolor velit aliqua voluptate minim non incididunt enim cillum laboris aliquip est ut non occaecat velit ea velit aliquip tempor. Aliquip duis voluptate voluptate nulla nisi amet in deserunt duis ad sunt laborum excepteur id veniam consectetur ad mollit in exercitation est aute sit duis adipisicing.
      </p>
    </div>
    <div id="section-2">
      <div class="title">
        <h2>Section 2</h2>
        <h3>{{ country }}</h3>
      </div>
      <div class="content">
        <div class="step" data="Singapore">
          <h2>Subsection A</h2>
          <p>
            Elit occaecat tempor labore elit deserunt amet sit duis laboris enim tempor exercitation qui ea laborum dolor sit pariatur irure ut sed officia ut sit labore ea proident qui. Sed incididunt ut mollit dolore excepteur veniam aliquip mollit et nulla consequat aute quis cupidatat exercitation sed pariatur minim tempor mollit consequat consectetur est consequat sunt eiusmod dolor nulla. Elit occaecat tempor labore elit deserunt amet sit duis laboris enim tempor exercitation qui ea laborum dolor sit pariatur irure ut sed officia ut sit labore ea proident qui. Sed incididunt ut mollit dolore excepteur veniam aliquip mollit et nulla consequat aute quis cupidatat exercitation sed pariatur minim tempor mollit consequat consectetur est consequat sunt eiusmod dolor nulla.
          </p>
        </div>
        <div class="step" data="Malaysia">
          <h2>Subsection B</h2>
          <p>
            Elit occaecat tempor labore elit deserunt amet sit duis laboris enim tempor exercitation qui ea laborum dolor sit pariatur irure ut sed officia ut sit labore ea proident qui. Dolore cupidatat fugiat in occaecat laboris esse velit nisi cupidatat ut cupidatat cupidatat esse est et cupidatat officia enim voluptate consequat duis velit minim sit ut dolore nisi dolor aliqua commodo laborum.
          </p>
        </div>
        <div class="step" data="Japan">
          <h2>Subsection C</h2>
          <p>
            Elit occaecat tempor labore elit deserunt amet sit duis laboris enim tempor exercitation qui ea laborum dolor sit pariatur irure ut sed officia ut sit labore ea proident qui. Lorem ipsum irure voluptate eu labore ut eiusmod consectetur sed est aute nulla nulla pariatur occaecat voluptate voluptate sint ut ea pariatur amet esse magna elit nisi esse dolor duis proident laboris sunt veniam mollit. Elit occaecat tempor labore elit deserunt amet sit duis laboris enim tempor exercitation qui ea laborum dolor sit pariatur irure ut sed officia ut sit labore ea proident qui. Lorem ipsum irure voluptate eu labore ut eiusmod consectetur sed est aute nulla nulla pariatur occaecat voluptate voluptate sint ut ea pariatur amet esse magna elit nisi esse dolor duis proident laboris sunt veniam mollit.
          </p>
        </div>
      </div>
      <svg>
      </svg>
    </div>
    <div class="parallax">
    </div>
    <div id="section-3">
      <h2>Section 3</h2>
      <p>
        Enim dolor nostrud do exercitation exercitation do dolor officia officia enim laborum sed laboris consectetur ut cupidatat eiusmod est do cupidatat proident elit consectetur veniam nostrud dolore laborum fugiat. Lorem ipsum eu eiusmod ea ad velit culpa aute aliquip id amet ut et eiusmod nisi ullamco amet sed ut laborum ex amet mollit nostrud irure.
      </p>
    </div>
    <div id="section-4">
      <div class="title">
        <h2>Section 4</h2>
        <h3>{{ country }}</h3>
      </div>
      <div class="content">
        <div class="step" data="Singapore">
          <h2>Subsection A</h2>
          <p>
            Elit occaecat tempor labore elit deserunt amet sit duis laboris enim tempor exercitation qui ea laborum dolor sit pariatur irure ut sed officia ut sit labore ea proident qui. Sed incididunt ut mollit dolore excepteur veniam aliquip mollit et nulla consequat aute quis cupidatat exercitation sed pariatur minim tempor mollit consequat consectetur est consequat sunt eiusmod dolor nulla. Elit occaecat tempor labore elit deserunt amet sit duis laboris enim tempor exercitation qui ea laborum dolor sit pariatur irure ut sed officia ut sit labore ea proident qui. Sed incididunt ut mollit dolore excepteur veniam aliquip mollit et nulla consequat aute quis cupidatat exercitation sed pariatur minim tempor mollit consequat consectetur est consequat sunt eiusmod dolor nulla.
          </p>
        </div>
        <div class="step" data="Malaysia">
          <h2>Subsection B</h2>
          <p>
            Elit occaecat tempor labore elit deserunt amet sit duis laboris enim tempor exercitation qui ea laborum dolor sit pariatur irure ut sed officia ut sit labore ea proident qui. Dolore cupidatat fugiat in occaecat laboris esse velit nisi cupidatat ut cupidatat cupidatat esse est et cupidatat officia enim voluptate consequat duis velit minim sit ut dolore nisi dolor aliqua commodo laborum.
          </p>
        </div>
      </div>
      <svg>
      </svg>
    </div>
    <div id="section-5">
      <h2>Section 5</h2>
      <p>
        Enim dolor nostrud do exercitation exercitation do dolor officia officia enim laborum sed laboris consectetur ut cupidatat eiusmod est do cupidatat proident elit consectetur veniam nostrud dolore laborum fugiat. Lorem ipsum eu eiusmod ea ad velit culpa aute aliquip id amet ut et eiusmod nisi ullamco amet sed ut laborum ex amet mollit nostrud irure. Ut magna eu elit ullamco culpa nulla anim cillum dolore commodo ut commodo est occaecat reprehenderit ex laboris laborum excepteur fugiat mollit enim duis nulla fugiat tempor proident eiusmod reprehenderit cupidatat et ut laboris in id commodo.
      </p>
      <p>
        Ut eu culpa anim excepteur sunt exercitation qui tempor ut reprehenderit occaecat pariatur velit ut laborum in esse esse est est adipisicing mollit occaecat sit proident eu. Lorem ipsum nulla mollit esse id laborum quis sed labore anim quis aliqua fugiat consequat officia ullamco in ullamco laborum reprehenderit exercitation ea quis veniam mollit sunt fugiat mollit mollit ut elit culpa est officia.
      </p>
    </div>
    
  </div>
</template>

<script>
import * as d3 from 'd3'
const scrollama = require('scrollama');

export default {
  name: 'app',
  components: {
  },
  mounted() {
    this.setupSvgs();
    const scroller = scrollama();
    scroller
      .setup({
        step: '#section-2 .step',
        offset: 0.5, // when the element is 0.5 shown/hidden, the enter/exit step triggers
      })
      .onStepEnter(this.enterTrigger)
      .onStepExit(response => {
        d3.select(response.element)
          .transition().duration(200)
          .style('opacity', .2)
        if (response.index === 0 && response.direction === 'up') {
          d3.selectAll('image.Singapore')
            .transition().duration(500)
            .attr('y', -100)
        } else if (response.index === 1 && response.direction === 'up') {
          d3.selectAll('image.Malaysia')
            .transition().duration(500)
            .attr('y', -100)
        } else if (response.index === 2 && response.direction === 'up') {
          d3.selectAll('image.Japan')
            .transition().duration(500)
            .attr('y', -100)
        }
      })

    const scroller2 = scrollama();
    scroller2
      .setup({
        step: '#section-4 .step',
        offset: 0.5,
        progress: true,
      })
      .onStepEnter(response => {
        d3.select(response.element)
          .style('opacity', 1)
      })
      .onStepExit(response => {
        d3.select(response.element)
          .style('opacity', 0.2)
      })
      .onStepProgress(response => {
        if (response.index === 0) {
          d3.select('image#meme')
            .attr('x', response.progress < 0.5 ? 400 - 800 * response.progress : -400 + 800 * response.progress)
        }
      })
  },
  data() {
    return {
      country: ''
    }
  },
  methods: {
    setupSvgs() {
      let sections = ['Singapore', 'Malaysia', 'Japan'],
      counts = [3, 2, 4]
      sections.forEach((country, i) => {
        d3.select('#section-2 svg')
          .selectAll(`image.${country}`)
          .data(new Array(counts[i])).enter()
          .append('image')
          .attr('class', country)
          .attr('xlink:xlink:href', './bowl.png')
          .attr('height', 100)
          .attr('width', 100)
          .attr('x', 100 + 100 * i)
          .attr('y', -100)
      })

      d3.select('#section-4 svg')
        .append('image')
        .attr('id', 'meme')
        .attr('xlink:xlink:href', './no.jpg')
        .attr('height', 500)
        .attr('width', 500)
        .attr('x', 400)
        .attr('y', 0)
        .attr('opacity', 0.5)
          
    },
    enterTrigger(response) {
      this.country = d3.select(response.element).attr('data')
      d3.select(response.element)
        .transition().duration(200)
        .style('opacity', 1)

      if (response.index === 0) {
        d3.selectAll('image.Singapore')
          .transition().duration(400)
          .delay((d, i) => 200 * i)
          .attr('y', (d, i) => 375 - 100 * i)
      } else if (response.index === 1) {
        d3.selectAll('image.Malaysia')
          .transition().duration(400)
          .delay((d, i) => 200 * i)
          .attr('y', (d, i) => 375 - 100 * i)
      } else if (response.index === 2) {
        d3.selectAll('image.Japan')
          .transition().duration(400)
          .delay((d, i) => 200 * i)
          .attr('y', (d, i) => 375 - 100 * i)
      }
    }
  }
}
</script>

<style scoped>

#app {
  width: 80vw;
}

#section-2 .title,
#section-4 .title {
  display: inline-block;
  width: 15%;
  vertical-align: top;
  position: sticky;
  top: 100px;
}

#section-2 .content,
#section-4 .content {
  display: inline-block;
  width: 40%;
}

#section-2 .step,
#section-4 .step {
  opacity: 0.2;
  padding: 20px;
  background-color: #ffddb6;
}

#section-4 .step {
  background-color: #d3fff8;
}

#section-2 svg,
#section-4 svg {
  display: inline-block;
  border: none;
  width: 40%;
  height: 100vh;
  vertical-align: top;
  position: sticky;
  top: 0px;
}

.parallax {
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;

  width: 90vw;
  height: 50vh;
  background-image: url("./large.jpg");
}

</style>
