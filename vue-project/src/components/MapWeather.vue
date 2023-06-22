<template>
    <ol-map class="map-view">
      <ol-view
        ref="view"
        :center="center"
        :zoom="zoom"
        :projection="projection"
      />
  
      <ol-tile-layer>
        <ol-source-osm />
      </ol-tile-layer>
  
    </ol-map>
  </template>
  
  <script setup>
  import { ref } from "vue";
  
  const center = ref([20.123123, 40]);
  const projection = ref("EPSG:4326");
  const zoom = ref(8);
  </script>
  
  <style scoped>
  .map-view {
    display: flex;
    height: 100%;
    width: 100%;
  }
  
  @media (max-width: 1024px) {
    .map-view {
      height: 300px;
      width: 100%;
    }
  }
  </style>
  