<template>
  <div id="map"></div>
</template>
<script setup>
import { onMounted } from "vue";

onMounted(() => {
  let map = L.map("map").setView([26.1970047, -80.2461286], 15);
  L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
    attribution:
      '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
  }).addTo(map);

  L.marker([26.1970047, -80.2461286]).addTo(map).openPopup();
});
</script>
