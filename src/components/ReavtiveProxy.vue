<script setup>
import { reactive, onMounted } from 'vue';

const raw = {};
const proxy = reactive(raw);

// proxy is NOT equal to the original.
console.log(proxy === raw); // false

// calling reactive() on the same object returns the same proxy
console.log(reactive(raw) === proxy); // true

// calling reactive() on a proxy returns itself
console.log(reactive(proxy) === proxy); // true

// It only works for object types (objects, arrays, and collection types such as Map and Set).
// It cannot hold primitive types such as string, number or boolean.

onMounted(() => {
  setTimeout(() => {
    state.count++;
    deepState.foo.count++;
  }, 2000);
});
</script>
<template>
  <h3>Basic Reavtivity</h3>
  <p>{{ state.count }}</p>
  <p>{{ deepState.foo.count }}</p>
</template>

<style scoped></style>
