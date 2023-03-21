<script setup>
import { ref, toRefs, onMounted } from 'vue';

const deconstructionObject = ref({
  list: ['a', 'b', 'c'],
  count: 0,
  name: 'foo',
});

const { count, ...rest } = toRefs(deconstructionObject.value);

onMounted(() => {
  setTimeout(()=>{
    // Keep in mind, the referece will impact the original variable/ data.
    count.value++;
  }, 2000)
})

</script>
<template>
  <h3>Deconstruction:</h3>
  <p>Original: {{ deconstructionObject.count }}</p>
  <p>Deconstructed count: {{ count }}</p>
  <p>Deconstructed rest.list: {{ rest.list }}</p>
  <p>Deconstructed rest.name: {{ rest.name }}</p>

 
</template>

<style scoped>
</style>
