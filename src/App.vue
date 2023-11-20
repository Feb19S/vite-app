<!--
 * @Author: Blake 473263319@qq.com
 * @Date: 2023-11-13
 * @LastEditors: Blake 473263319@qq.com
 * @LastEditTime: 2023-11-20
 * @FilePath: \vite-app\src\App.vue
 * @Description: 
-->

<template>
  <WaterFallVue :list="list"></WaterFallVue>
  <DefineExpose ref="defineExposea" @click="c" :title="name"></DefineExpose>
  <CustomInput v-model="searchText"></CustomInput> {{ searchText }}
  <Menu @XiaoYu="AAA" :Menu="Menu2"></Menu>
  <Content :contentData="xiaozhao"></Content>
  <waterFall :titleObj="titleObj" :ming="ming" :ming-age="mingAge"></waterFall>
  <watch></watch>
  <computed></computed>
  <HelloWorld msg="Vite + Vue" />
  <setup />
  <!-- <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div> -->
</template>

<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue';
import setup from './components/setup.vue';
import computed from './components/computed.vue';
import watch from './components/watch.vue';
import waterFall from './components/water-fall.vue';
import Menu from './components/Menu.vue';
import Content from './components/Content.vue';
import CustomInput from './components/CustomInput.vue';
import DefineExpose from './components/DefineExpose.vue';
import WaterFallVue from './components/WaterFallVue.vue';
import { reactive, ref } from 'vue';

const titleObj = {
  name: '小明',
};
const ming = 'ming';
const mingAge = 12;

interface A {
  name: string;
  sex: number;
  height?: number;
}

const xiaozhao = reactive<A>({
  name: '小赵',
  sex: 1,
});

const Menu2 = reactive<A>({
  name: '大余',
  sex: 11,
  height: 175,
});

const AAA = (y?: any) => {
  console.log(y, '余');
  if (y[0] === 1) {
    let { name, sex, height } = Menu2;
    name = '小于';
    sex = 12;
    height = 165;
    Menu2.name = name;
    Menu2.sex = sex;
    Menu2.height = height;
  }
};

const searchText = ref('A');

const name: string = 'defineExposeAAA';

const defineExposea = ref<any>(null);

const c = () => {
  console.log(defineExposea.value.name);
  console.log(defineExposea.value.open());
};

const list = [
  {
    height: 300,
    background: 'red',
  },
  {
    height: 400,
    background: 'pink',
  },
  {
    height: 500,
    background: 'blue',
  },
  {
    height: 200,
    background: 'green',
  },
  {
    height: 300,
    background: 'gray',
  },
  {
    height: 400,
    background: '#CC00FF',
  },
  {
    height: 200,
    background: 'black',
  },
  {
    height: 100,
    background: '#996666',
  },
  {
    height: 500,
    background: 'skyblue',
  },
  {
    height: 300,
    background: '#993366',
  },
  {
    height: 100,
    background: '#33FF33',
  },
  {
    height: 400,
    background: 'skyblue',
  },
  {
    height: 200,
    background: '#6633CC',
  },
  {
    height: 300,
    background: '#666699',
  },
  {
    height: 300,
    background: '#66CCFF',
  },
  {
    height: 300,
    background: 'skyblue',
  },
  {
    height: 200,
    background: '#CC3366',
  },
  {
    height: 200,
    background: '#CC9966',
  },
  {
    height: 200,
    background: '#FF00FF',
  },
  {
    height: 500,
    background: '#990000',
  },
  {
    height: 400,
    background: 'red',
  },
  {
    height: 100,
    background: '#999966',
  },
  {
    height: 200,
    background: '#CCCC66',
  },
  {
    height: 300,
    background: '#FF33FF',
  },
  {
    height: 400,
    background: '#FFFF66',
  },
  {
    height: 200,
    background: 'red',
  },
  {
    height: 100,
    background: 'skyblue',
  },
  {
    height: 200,
    background: '#33CC00',
  },
  {
    height: 300,
    background: '#330033',
  },
  {
    height: 100,
    background: '#0066CC',
  },
  {
    height: 200,
    background: 'skyblue',
  },
  {
    height: 100,
    background: '#006666',
  },
  {
    height: 200,
    background: 'yellow',
  },
  {
    height: 300,
    background: 'yellow',
  },
  {
    height: 100,
    background: '#33CCFF',
  },
  {
    height: 400,
    background: 'yellow',
  },
  {
    height: 400,
    background: 'yellow',
  },
  {
    height: 200,
    background: '#33FF00',
  },
  {
    height: 300,
    background: 'yellow',
  },
  {
    height: 100,
    background: 'green',
  },
];
</script>


<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
