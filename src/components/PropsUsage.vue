<script setup>
import { ref, onMounted } from 'vue';

const props = defineProps({
  arr: {
    type: Array,
    default: ['a', 'b', 'c'],
  },
  arr2: {
    type: Array,
    default: [{ a: 'a' }, { b: 'b' }],
  },
});

// if you want to mutate value of prop, but without changing it, you need to do shallow copy.
// mutation Props in vue3 is not allowed

const copyOne = ref(props.arr.slice());

// if you have Array of objects, shallow copy won't do.
// copyTwo.value[0].a = 'A' will also mutated original prop in arr2[0].a
const copyTwo = ref(props.arr2.slice());

// to avoid it, you should do deep copy.
const copyTwoDeep = ref(JSON.parse(JSON.stringify(props.arr2)));

// shallow copy

onMounted(() => {
  setTimeout(() => {
    copyOne.value.push('d');
    copyTwo.value.push({ d: 'd' });
    copyTwo.value[0].a = 'A';
    copyTwoDeep.value[1].b = 'B';
  }, 2000);
});
</script>
<template>
  <h3>Props:</h3>
  <!-- This will not mutate. CopyOne is a deep copy. -->
  <p>Original prop: {{ arr }}</p>
  <p>Copy of a prop: {{ copyOne }}</p>
  <p>Original prop 2: {{ arr2 }}</p>
  <p>Copy of a prop 2: {{ copyTwo }}</p>
  <p>Deep copy of a prop 2: {{ copyTwoDeep }}</p>
</template>

<style scoped>
</style>
