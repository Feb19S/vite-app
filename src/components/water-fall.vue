<template>
  <div>子集</div>
  <div>值：{{ titleObj }}</div>
  <div>小明：{{ ming }}</div>
  <div>小明今年：{{ mingAge }}岁</div>
</template>

<script setup lang='ts'>

// defineProps({
//   title:{
//     type: String,
//     defult: '这是标题'
//   }
// })
const props = withDefaults(
  defineProps<{
  titleObj: object,
  ming: String,
  mingAge: number,
}>(),{
  titleObj: ()=>{ return {name: '小张'} },
  ming: ()=>'m',
  mingAge: ()=>17,
})
console.log(props.titleObj)

</script>

<style scoped>

</style>