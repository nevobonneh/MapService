<template>
  <div style="height: 80vh">
    <LMap :zoom="zoom" :center="center">
      <LTileLayer :url="url"></LTileLayer>
      <LMarker :lat-lng="[31.425615, 34.753433]" @click="openPopup"/>
      <LMarker :lat-lng="[31.525615, 34.853433]" @click="openPopup"/>
    </LMap>
    <div v-if="openDialog">Hello</div>
  </div>
</template>

<script>
import { LMap, LTileLayer, LMarker } from "vue2-leaflet";
export default {
  name: "Map",
  components: {
    LMap,
    LTileLayer,
    LMarker
  },
  data() {
    return {
      url: "https://{s}.tile.osm.org/{z}/{x}/{y}.png",
      zoom: 10,
      center: [31.425615, 34.753433],
      bounds: null,
      openDialog: false
    };
  },
  methods:{
    openPopup: function () {
      // `this` inside methods point to the Vue instance
      this.openDialog = !this.openDialog;
      // `event` is the native DOM event
    }
  }
};
</script>