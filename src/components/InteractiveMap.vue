<script setup>
import { onMounted } from "vue";

const props = defineProps({
  latitud: Number,
  longitud: Number,
});

onMounted(() => {
  let map = L.map("map").setView([props.latitud, props.longitud], 15);
  L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
    attribution:
      '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
  }).addTo(map);

  L.marker([props.latitud, props.longitud]).addTo(map).openPopup();
});
</script>

<template>
  <div id="map"></div>
</template>
