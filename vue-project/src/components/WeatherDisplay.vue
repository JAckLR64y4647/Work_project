<template>
  <div class="weather-display">
    <CurrentWeather :selectedCity="selectedCity" />
    <WeeklyWeather :selectedCity="selectedCity" />
  </div>
</template>

<script>
import { ref } from 'vue';
import CurrentWeather from '../components/CurrentWeather.vue';
import WeeklyWeather from '../components/WeeklyWeather.vue';



export default {
  props: ['selectedCity'],
  components: {
    CurrentWeather,
    WeeklyWeather,
  },
  setup(props) {
    return {
      selectedCity: ref(props.selectedCity),
    };
  },
};
</script>

<style scoped>
@import url("https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css");
.weather-display {
  margin-top: 20px;
}
</style>