<script lang="ts" setup>
import IPInfo from "./IPInfo.vue";
import IconArrow from "./IconArrow.vue";
import InteractiveMap from "./InteractiveMap.vue";
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
        />
        <button type="button" class="test"><IconArrow /></button>
      </div>
    </header>
    <IPInfo />
    <InteractiveMap />
  </div>
</template>
