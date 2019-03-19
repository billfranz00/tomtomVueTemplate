<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
    <h2>TomTom Map</h2>
    <div id="map"></div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      map: {},
      markers: []
    }
  },
  created() {
    // App Info
    tomtom.setProductInfo("tomtomTest", "0.1");
  },
  mounted() {
    // Raplaces div#map with TomTom map
    this.map = new tomtom.L.Map('map', {
      key: "<your_key_here>",
      source: 'vector',
      center: [52.360306, 4.876935],
      zoom: 5,
      basePath: "/sdk"
    });

    this.markers.push(tomtom.L.marker([52.360306, 4.876935], {
      icon: tomtom.L.icon({
        iconUrl: '/sdk/images/ic_map_poi_126-black.png'
      })
    }).addTo(this.map));

    this.markers.push(tomtom.L.marker([50, 0], {
      icon: tomtom.L.icon({
        iconUrl: '/sdk/images/ic_map_poi_125-black.png'
      })
    }).addTo(this.map));

    console.log(this.markers);
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

#map {
  height: 500px;
  width: auto;
  margin-bottom: 100px;
}
</style>
