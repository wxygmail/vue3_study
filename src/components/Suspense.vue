<template>
  <div>
    Suspense!!!
    <Suspense>
      <template #default>
        <Child/>
      </template>
      <template #fallback>
        数据加载中
      </template>
    </Suspense>
  </div>
</template>

<script>
//正常引入
// import Child from './other/child.vue';

/**
 * 异步加载组件
 * 问题：组件为渲染的时候会让人以为无内容
 * 解决：vue3提供了一个Suspense组件
 */
import {defineAsyncComponent} from 'vue';

const Child = defineAsyncComponent(() => import('./other/child.vue'))

export default {
  components: {Child},
  component: {
    Child
  }
}
</script>

<style scoped>

</style>
