<template>
  <div id="app">
    <h1>{{ country }}</h1>
    <hr/>
    <button id='fly' @click="fly">Fly</button>
    <div id='map'></div>
  </div>
</template>

<script>
const mapboxgl = require('mapbox-gl/dist/mapbox-gl.js');

export default {
  name: 'app',
  components: {},
  data() {
    return {
      country: 'Mapbox Demo',
      map: null,
    }
  },
  mounted() {
    mapboxgl.accessToken = 'pk.eyJ1IjoiZ3JlZW50ZnJhcHAiLCJhIjoiY2ptNGE1cTB1MWV5azNxazg0ODUzdGZydiJ9.lQCreykk_XmjoDgCEyd47w';
    const self = this;
    let hoveredStateId = null;
    let popup = new mapboxgl.Popup({
      closeButton: false,
      closeOnClick: false
    });
    this.map = new mapboxgl.Map({
      container: 'map',
      style: 'mapbox://styles/greentfrapp/cjm4b1aug5ode2slcb2iqy67l',
      center: [103.9616004, 1.3412927],
      zoom: 5
    });
    const map = this.map;
    map.on('load', function () {
      map.addSource('sea', {
        "type": "geojson",
        "data": "./sea.geojson"
      });
      map.addLayer({
        'id': 'sea',
        'type': 'fill',
        'source': 'sea',
        'layout': {},
        'paint': {
          'fill-color': '#088',
          'fill-opacity': ["case",
            ["boolean", ["feature-state", "hover"], false],
            1,
            0.5
          ]
        }
      });
    });
    map.on('mouseenter', 'sea', function (e) {
      map.getCanvas().style.cursor = 'pointer';
      // map.setPaintProperty('sea', 'fill-opacity', 1.);
      self.country = e.features[0].properties.ADMIN;
      if (e.features.length > 0) {
        if (hoveredStateId) {
          map.setFeatureState({source: 'sea', id: hoveredStateId}, { hover: false});
        }
        hoveredStateId = e.features[0].id;
        map.setFeatureState({source: 'sea', id: hoveredStateId}, { hover: true});
      }

      var coordinates = e.features[0].geometry.coordinates[0];
      var description = e.features[0].properties.ADMIN;

      while (coordinates.length !== 2) {
        coordinates = coordinates[0];
      }
       
      // Ensure that if the map is zoomed out such that multiple
      // copies of the feature are visible, the popup appears
      // over the copy being pointed to.
      while (Math.abs(e.lngLat.lng - coordinates[0]) > 180) {
        coordinates[0] += e.lngLat.lng > coordinates[0] ? 360 : -360;
      }
       
      popup.setLngLat(coordinates)
        .setHTML(description)
        .addTo(map);
    });
    map.on('mouseleave', 'sea', function (e) {
      map.getCanvas().style.cursor = '';
      // map.setPaintProperty('sea', 'fill-opacity', .5);
      self.country = 'Mapbox Demo'
      if (hoveredStateId) {
        map.setFeatureState({source: 'sea', id: hoveredStateId}, { hover: false});
      }
      hoveredStateId =  null;
      popup.remove();
    });
  },
  methods: {
    fly() {
      this.map.flyTo({
        center: [103.9616004, 1.3412927],
        zoom: 15,
      });
    }
  }
}
</script>

<style scoped>

#map {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 50vw;
  right: 0;
}

</style>
