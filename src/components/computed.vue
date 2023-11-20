<!--
 * @Author: Blake 473263319@qq.com
 * @Date: 2023-11-14
 * @LastEditors: Blake 473263319@qq.com
 * @LastEditTime: 2023-11-14
 * @FilePath: \vite-app\src\components\computed.vue
 * @Description: 
-->
<template>
  <div>
    <table style="width: 800px;">
      <thead>
        <tr>
          <th>名称</th>
          <th>数量</th>
          <th>价格</th>
          <th>操作</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in data" :key="index">
          <td align="center">{{ item.name }}</td>
          <td align="center">
            <button @click="AddAndSub(item, false)">-</button>
            {{ item.num }}
            <button @click="AddAndSub(item, true)">+</button>
          </td>
          <td align="center">{{ item.num * item.price }}</td>
          <td align="center">
            <button @click="del(index)">删除</button>
          </td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <td></td>
          <td></td>
          <td></td>
          <td align="center">总价：{{ $total }}</td>
        </tr>
      </tfoot>
    </table>
  </div>
</template>

<script setup lang='ts'>
import { ref, reactive, computed } from 'vue'

type shop = {
  name: string,
  num: number;
  price: number
}

let $total = ref<number>(0)
const data = reactive<shop[]>([
  {
    name: '衣服',
    num: 1,
    price: 100
  },
  {
    name: '裤子',
    num: 1,
    price: 200
  },
  {
    name: '围脖',
    num: 1,
    price: 300
  },
  {
    name: '鞋子',
    num: 1,
    price: 400
  }
])

const AddAndSub = (item: shop, type: boolean = false): void => {
  if(item.num > 1 && !type){
    item.num--
  }
  if(item.num <= 99 && type){
    item.num++
  }
}

const del = (index: number) => {
  data.splice(index, 1)
}

$total = computed<number>(()=>{
  return data.reduce((prev, next)=>{
    return prev + (next.num * next.price)
  }, 0)
})

</script>

<style scoped>

</style>