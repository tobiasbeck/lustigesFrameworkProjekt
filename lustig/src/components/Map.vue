<template>
<div>
<h1 v:c>Find your grill on our grilling map</h1>
 <gmap-map

    :center="center"
    :zoom="7"
    style="width: 500px; height: 300px"
  >
      <gmap-marker
      v-for="m in markers"
      :position="m.position"
      :clickable="true"
      @click="center=m.position"
    ></gmap-marker>
  </gmap-map>
  </div>
</template>

<script>
import Vue from 'vue';
import * as VueGoogleMaps from 'vue2-google-maps';
import VueResource from 'vue-resource';

  
  Vue.use(VueGoogleMaps, {
    load: {
      key: 'AIzaSyA1OUPKyuJM6J3_IH6IYwpYhMLOK73bGBo',
      v: '',
      // libraries: 'places', //// If you need to use place input 
    }
  });

  Vue.use(VueResource);

  export default {
    state:{
      markers:[]
    },

    created: function(){

      this.$http.get('http://localhost:3000/api/grills').then(response => {
      console.log(response);
      console.log(this);
      var markers=[];
      response.body.forEach(function(e,i,a){
        markers.push({
          position: {lat: e.lat, lng: e.long}
        })
      });
      console.log(markers);
      this.markers=markers;

  });
    
    },

    data () {
      return {
        center: {lat: 10.0, lng: 10.0},
        markers: []
      }
    }
  }
</script>
