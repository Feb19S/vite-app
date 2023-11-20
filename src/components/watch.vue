<!--
 * @Author: Blake 473263319@qq.com
 * @Date: 2023-11-14
 * @LastEditors: Blake 473263319@qq.com
 * @LastEditTime: 2023-11-14
 * @FilePath: \vite-app\src\components\watch.vue
 * @Description: 
-->
<template>
  <div>
    case1：<input v-model="message1" type="text">
    <hr>
    case2：<input v-model="message2" type="text">
    <hr>
    case3：<input v-model="message3" type="text">
    <hr>
    case3：<input v-model="message4.nav.bar.name" type="text">
  </div>
  <!-- <h1>{{ tom }}</h1> -->
</template>

<script setup lang='ts'>
import { ref, watch } from 'vue'
let message1 = ref<string>('小明')
let message2 = ref<string>('小王')
let message3 = ref<string>('小李')
let message4 = ref({
  nav: {
    bar: {
      name: '吃饭'
    }
  }
})
// 监听第一个参数：侦听的数据源（sources） 第二个参数 回调函数 cb （newVal, oldVal）
watch(message1, (newVal, oldVal)=>{
  console.log('新值===>', newVal)
  console.log('旧值===>', oldVal)
})
watch([message2,message3], (newVal, oldVal)=>{
  console.log('新值===>', newVal)
  console.log('旧值===>', oldVal)
})
watch(message4, (newVal, oldVal)=>{
  console.log('新值===>', newVal)
  console.log('旧值===>', oldVal)
}, {deep:true})
</script>

<style scoped>

</style>