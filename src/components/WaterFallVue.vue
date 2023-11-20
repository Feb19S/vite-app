<!--
 * @Author: Blake 473263319@qq.com
 * @Date: 2023-11-20
 * @LastEditors: Blake 473263319@qq.com
 * @LastEditTime: 2023-11-20
 * @FilePath: \vite-app\src\components\WaterFallVue.vue
 * @Description: 
-->
<template>
  <div class="wraps">
    <div :style="{height: item.height+'px', background: item.background, top: item.top+'px', left: item.left+'px'}"
      v-for="item in waterList" class="items"
    ></div>
  </div>
</template>

<script setup lang='ts'>
import { reactive, onMounted } from 'vue'

const props = defineProps<{list: any[]}>()

const waterList = reactive<any[]>([]) // 数据进行响应式处理

const init = () => {
  const heightList: any[]= [] // 这是形成新的大方块，作用是套住两个同一列方块
  const width = 130; // 定义宽度，我们方块的宽度为120，这边为130就能够让方块之间产生缝隙
  const x = document.body.clientWidth //获取可视区域的距离（就是你浏览器的最大宽度）
  const column = Math.floor( x/ width )

  for( let i = 0; i < props.list.length; i++) {
    if( i < column ) { // 数量要小于浏览器能承受的最大范围
      props.list[i].top = 10; // 方块距离上方的距离
      props.list[i].left = i * width; // 横向排列放入刚好（能放下的最大数量）的方块（第一排）
      heightList.push(props.list[i].height + 10) // 形成的大方块的高度
      waterList.push(props.list[i]) // 向响应式数据传入方块，并返回新的长度
    } else {
      let current = heightList[0] //默认第一个是最小的
      let index = 0; //默认索引
      heightList.forEach((h, inx)=>{ //找到真正最小的单位，对数组内的每个方块都执行一次判断
        if(current > h) { //不停的去进行筛选，每次筛选出来最小的那个方块，冒泡排序
          current = h;
          index = inx;
        }
      })
      console.log('c', current);
      props.list[i].top = (current + 20); // 定义新方块相对浏览器上方的距离（同列上方的方块+20）
      console.log('top', props.list[i].top, i);
      props.list[i].left = index * width // 通过索引定位到该位置
      heightList[index] = (heightList[index] + props.list[i].height + 20) //找到最小的之后回重新计算最小的并将上下间距拉开20
      waterList.push(props.list[i]) //将方块添加进去
    }
  }
}
onMounted(() => {
  window.onresize = ()=>init()
  init()
})
</script>

<style scoped lang="less">
.wraps {
  position: relative;
  height: 100%;

  .items{
    position: absolute;
    width: 120px;
  }
}
</style>