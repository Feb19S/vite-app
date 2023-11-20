<!--
 * @Author: Blake 473263319@qq.com
 * @Date: 2023-11-13
 * @LastEditors: Blake 473263319@qq.com
 * @LastEditTime: 2023-11-13
 * @FilePath: \vite-app\src\components\setup.vue
 * @Description: 
-->
<template>
  <div>
    <!-- 支持数字运算 -->
    {{ name }} {{ name + 5 }}
  </div>
  <div>
    <!-- 支持三元表达式 -->
    {{ num ? 'true' : 'false' }}
  </div>
  <div>
    <!-- API运算 -->
    {{ _API.map(v => { return v }) }}
  </div>
  <p>
    
    <div>{{ model }}</div>
    <input type="text" v-model="model">
  </p>
  <div>
    <!-- v-on -->
    <button @click="onClick">点击</button>
    <button @[clickName]="dynamicClick">动态事件切换并且简写</button>
  </div>
  <p>
    <div>{{ Man0 }}</div>
    <div>{{ Man1 }}</div>
    <div>{{ Man2 }}</div>
    <div>{{ Man4 }}</div>
    <button @click="changeName()">修改名字</button>
  </p>
  <p>
    <div>Ref:{{ name0 }}</div>
    <div>shallowRef:{{ name1 }}</div>
    <button @click="change()">修改</button>
  </p>
</template>

<script setup lang='ts'>
import { Ref, ref, isRef, shallowRef } from "vue";

const name:string = 'setup 语法糖模式'
const num:number = 1
const _API: number[] = [1, 2, 3, 4, 5]
const onClick = ()=>{
  console.log('点击事件');
}

const clickName:string = 'click'

const dynamicClick = ()=>{
  console.log('动态事件切换并且简写')
}

const model = ref('动态绑定')

type M = {
  name:string
}
const Man0:Ref<M> = ref({name: 'name'})
const Man1 = ref<M>({name: 'name'})
const Man2 = ref({name: 'name'})
const Man4 = ref({name: '小明'})
const changeName = ()=>{
  Man4.value.name = '小王'
  console.log("Man4: ", Man4);
  console.log("isRef(Man4): ", (isRef(Man4)))
}

const name0 = ref({name:'小李'});
const name1 = shallowRef({name:'小王'});
const name2 = {name:'小张'};
const change = ()=>{
  // name0.value.name = '小张1'
  name1.value.name = '小王1'
  console.log(name0)
  console.log('这是小王', isRef(name1));
  console.log('这是小张', isRef(name2));
}
</script>

<style scoped>

</style>