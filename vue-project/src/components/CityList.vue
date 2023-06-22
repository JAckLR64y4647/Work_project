<template>
  <div class="city-list">
    <label for="city">Выберите город:</label>
    <select id="city" v-model="selectedCity" class="form-control" @change="handleCityChange">
      <option v-for="city in cities" :value="city.name">{{ city.name }}</option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedCity: '',
      cities: [
      { name: 'Киев', coordinates: { lat: 50.45466, lng: 30.5238 } },
      { name: 'Харьков', coordinates: { lat: 49.988358, lng: 36.232845 } },
      { name: 'Одесса', coordinates: { lat: 46.482526, lng: 30.723309 } },
      { name: 'Днепр', coordinates: { lat: 48.464717, lng: 35.046183 } },
      { name: 'Донецк', coordinates: { lat: 48.015883, lng: 37.80285 } },
      { name: 'Запорожье', coordinates: { lat: 47.8388, lng: 35.1396 } },
      { name: 'Львов', coordinates: { lat: 49.839683, lng: 24.029717 } },
      { name: 'Кривой Рог', coordinates: { lat: 47.910834, lng: 33.37926 } },
      { name: 'Николаев', coordinates: { lat: 46.975033, lng: 31.994583 } },
      { name: 'Мариуполь', coordinates: { lat: 47.097133, lng: 37.543099 } },
      { name: 'Винница', coordinates: { lat: 49.233083, lng: 28.468216 } },
      { name: 'Херсон', coordinates: { lat: 46.635417, lng: 32.616867 } },
      { name: 'Полтава', coordinates: { lat: 49.588266, lng: 34.551416 } },
      { name: 'Чернигов', coordinates: { lat: 51.4982, lng: 31.2890 } },
      { name: 'Черкассы', coordinates: { lat: 49.4444, lng: 32.0598 } },
      { name: 'Житомир', coordinates: { lat: 50.2547, lng: 28.6587 } },
      ],
    };
  },
  methods: {
    handleCityChange() {
      const city = this.cities.find((item) => item.name === this.selectedCity);
      this.$emit('select', city);
    },
  },
};
</script>

<style scoped>

</style>
