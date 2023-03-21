<script setup>
// https://vuejs.org/guide/essentials/reactivity-fundamentals.html#declaring-reactive-state

// We can create a reactive object or array with the reactive() function:

import { onMounted, reactive } from 'vue';

// simple example
const state = reactive({ count: 0 });

// it also supports deep reavtivity

const deepState = reactive({
  foo: { count: 0 },
});


function addOneToState() {
  state.count++;
}

onMounted(() => {
  setTimeout(() => {
    state.count++;
    deepState.foo.count++;
  }, 2000);
});
</script>
<template>
  <h3>Basic Reavtivity</h3>
  <button @click="addOneToState">Add +1 to state</button>
  <p>State: {{ state.count }}</p>
  <p>Nested state: {{ deepState.foo.count }}</p>
</template>

<style scoped></style>
