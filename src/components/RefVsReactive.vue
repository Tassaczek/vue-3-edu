<script setup>
import { ref, reactive, onMounted } from 'vue';

const reactiveObject = reactive({ count: 0 });
const refObject = ref({ count: 10 });

const reactiveArr = reactive([{ a: 'a' }, { b: 'b' }, { c: 'c' }]);
const refArr = ref([{ a: 'a' }, { b: 'b' }, { c: 'c' }]);

onMounted(() => {
  setTimeout(() => {
    reactiveObject.count++;
    // you need to drill into .value with a Ref()
    refObject.value.count++;

    // deep mutation
    reactiveArr.push({ d: 'd' });
    refArr.value.push({ d: 'd' });
  }, 2000);
});
</script>
<template>
  <h3>Ref vs Reactive</h3>
  <p>Reactive Object: {{ reactiveObject.count }}</p>
  <p>Ref Object: {{ refObject.count }}</p>
  <p><strong>Arrays</strong></p>
  <p>Reactive Arr {{ reactiveArr }}</p>
  <p>Ref Arr {{ refArr }}</p>
</template>

<style scoped>
</style>
