<template>
<div>
<h1>Find your grill on our grilling map</h1>
 <gmap-map
    :center="center"
    :zoom="7"
    style="width: 500px; height: 300px"
  ></gmap-map>
  </div>
</template>

<script>
import * as VueGoogleMaps from 'vue2-google-maps';
  import Vue from 'vue';
 
  Vue.use(VueGoogleMaps, {
    load: {
      key: 'AIzaSyA1OUPKyuJM6J3_IH6IYwpYhMLOK73bGBo',
      v: '',
      // libraries: 'places', //// If you need to use place input 
    }
  });

  export default {
    data () {
      return {
        center: {lat: 10.0, lng: 10.0},
        markers: [{
          position: {lat: 10.0, lng: 10.0}
        }, {
          position: {lat: 11.0, lng: 11.0}
        }]
      }
    }
  }
</script>
