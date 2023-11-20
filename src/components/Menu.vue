<!--
 * @Author: Blake 473263319@qq.com
 * @Date: 2023-11-16
 * @LastEditors: Blake 473263319@qq.com
 * @LastEditTime: 2023-11-16
 * @FilePath: \vite-app\src\components\Menu.vue
 * @Description: 
-->
<template>
  <div>
    <button @click="setMenu">派发</button>
    <p>
      {{ Menu }}
    </p>
  </div>
</template>

<script setup lang='ts'>
import { reactive } from 'vue';
const y:number[] = reactive<number[]>([1])
const emit = defineEmits(['XiaoYu'])
defineProps({Menu:{}})
const setMenu = ()=>{
  emit('XiaoYu', y)
}
</script>

<style scoped>

</style>