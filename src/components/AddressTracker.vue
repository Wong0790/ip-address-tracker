<script setup>
import { ref, watch, onMounted } from "vue";
import IPInfo from "./IPInfo.vue";
import IconArrow from "./IconArrow.vue";
import InteractiveMap from "./InteractiveMap.vue";

let ipAddress = ref("");
let loadMap = ref(false);
const info = ref({
  ipAddres: "",
  latitud: 0,
  longitud: 0,
  location: "",
  timezone: "",
  isp: "",
});

const getIPInfo = (ipAddress) => {
  if (ipAddress !== "") {
    loadMap.value = false;
    fetch(
      `https://geo.ipify.org/api/v2/country,city?apiKey=at_CV1BQn1Rlg9oGlZSoItEqaRk995Qc&ipAddress=${ipAddress}`
    )
      .then((response) => response.json())
      .then((data) => {
        info.value.ipAddres = data.ip;
        info.value.latitud = data.location.lat;
        info.value.longitud = data.location.lng;
        info.value.location = `${data.location.city}, ${data.location.region} ${data.location.postalCode}`;
        info.value.timezone = data.location.timezone;
        info.value.isp = data.isp;
        loadMap.value = true;
      });
  }
};

onMounted(() => {
  fetch("https://api.ipify.org?format=json")
    .then((response) => response.json())
    .then((data) => {
      getIPInfo(data.ip);
    });
});
</script>

<template>
  <div>
    <header class="header-wrapper">
      <h1>IP Address Tracker</h1>
      <div class="input-wrapper">
        <input
          type="text"
          class="ip-input"
          placeholder="Search for any IP address or domain"
          v-model="ipAddress"
        />
        <button type="button" class="find-btn" @click="getIPInfo(ipAddress)">
          <IconArrow />
        </button>
      </div>
    </header>
    <IPInfo :info="info" />
    <InteractiveMap
      :latitud="info.latitud"
      :longitud="info.longitud"
      v-if="loadMap"
    />
  </div>
</template>
