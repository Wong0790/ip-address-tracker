<script setup>
defineProps({
  info: Object,
});
</script>

<template>
  <div class="ip-info-wrapper">
    <div class="content-wrapper">
      <div class="section-wrapper">
        <span>IP Address</span>
        <h2>{{ info.ipAddres }}</h2>
      </div>
      <div class="section-wrapper">
        <span>Location</span>
        <h2>{{ info.location }}</h2>
      </div>
      <div class="section-wrapper">
        <span>Timezone</span>
        <h2>UTC {{ info.timezone }}</h2>
      </div>
      <div class="section-wrapper">
        <span>ISP</span>
        <h2>{{ info.isp }}</h2>
      </div>
    </div>
  </div>
</template>
