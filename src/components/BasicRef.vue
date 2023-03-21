<script setup>
import { ref, onMounted } from 'vue';

const count = ref(0);

console.log(count); // Proxy of { value: 0 }
console.log(count.value); // 0

count.value++;
console.log(count.value); // 1

// Example 2

const objectRef = ref({ count: 0 });

onMounted(() => {
  setTimeout(() => {
    count.value++; // 2 after 2 sec.
    // this works reactively
    objectRef.value.count++
    // you can also overwrite it. This will remove previous reactivity and create new. 
    // objectRef.value = { count: 1 };
  }, 2000);
});
</script>
<template>
  <h3>Basic Ref</h3>
  <p>Count: {{ count }}</p>
  <p>ObjectRef: {{ objectRef }}</p>
</template>

<style scoped></style>
