<!--
 * @Author: Blake 473263319@qq.com
 * @Date: 2023-11-16
 * @LastEditors: Blake 473263319@qq.com
 * @LastEditTime: 2023-11-16
 * @FilePath: \vite-app\src\components\Content.vue
 * @Description: 
-->
<template>
  <div>{{ contentData }}</div>
</template>

<script setup lang='ts'>

type props = {
  contentData: {
    name: string,
    sex: number,
    height?: number
  }
}

withDefaults(defineProps<props>(), {
  contentData: ()=>{
    return {
      name: 'xz',
      sex: 1,
      height: 0
    }
  }
})


</script>

<style scoped>

</style>