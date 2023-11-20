<template>
  <div>{{ title }}</div>
</template>

<script setup lang='ts'>
import { ref, defineExpose } from 'vue'
const definePropsTitle = defineProps({title:{}})
const data = ref(definePropsTitle) 
defineExpose({
  name: data.value.title,
  open: ()=>{console.log('defineExpose')}
})
console.log('DATA', data);

</script>

<style scoped>

</style>