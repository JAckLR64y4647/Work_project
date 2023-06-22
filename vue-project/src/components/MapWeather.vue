<template>
  <ol-map class="map-view">
    <ol-view ref="view" :center="center" :zoom="zoom" :projection="projection" />

    <ol-tile-layer>
      <ol-source-osm />
    </ol-tile-layer>

    <CityList @select="handleCitySelect" />

  </ol-map>
</template>

<script setup>
import { ref } from "vue";

const center = ref([30.5234, 50.4501]);
const projection = ref("EPSG:4326");
const zoom = ref(8);

const handleCitySelect = (city) => {
  if (city && city.coordinates) {
    center.value = [city.coordinates.lng, city.coordinates.lat];
  }
};
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
  