<template>
  <div class="child">
    我是Child组件
    {{ num }}
  </div>
</template>

<script>
import {ref} from 'vue'
//外部用了Suspense(异步引入) setup可以用async
export default {
  async setup() {
    const num = ref(0);
    const p = new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve({num})
      }, 5000)
    })
    return await p;
  }
}
</script>

<style scoped>
.child {
  height: 100px;
  width: 100%;
  border: 1px solid red;
}
</style>
