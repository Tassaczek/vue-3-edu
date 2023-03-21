<script setup>
import BasicReactive from './components/BasicReactive.vue';
import BasicRef from './components/BasicRef.vue';
import RefVsReactive from './components/RefVsReactive.vue';
import PropsUsage from './components/PropsUsage.vue';
import Deconstruction from './components/Deconstruction.vue';
</script>

<template>
  <BasicReactive />
  <BasicRef />
  <RefVsReactive />
  <PropsUsage />
  <Deconstruction />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
