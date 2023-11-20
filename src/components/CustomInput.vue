<!--
 * @Author: Blake 473263319@qq.com
 * @Date: 2023-11-16
 * @LastEditors: Blake 473263319@qq.com
 * @LastEditTime: 2023-11-16
 * @FilePath: \vite-app\src\components\CustomInput.vue
 * @Description: 
-->
<template>
  <div>
    <input :value="modelValue" @click="input" type="text">
    {{ modelValue }}
  </div>
</template>

<script setup lang='ts'>
const emit = defineEmits(['update:modelValue'])
defineProps(['modelValue'])
const input = ($event?: any)=>{
  
  emit('update:modelValue', $event.target.value)
}
</script>

<style scoped>

</style>