<template>
  <div>
    <p>名字：{{ name }}</p>
    <button @click="alertMessage">点击弹窗</button>
  </div>
</template>

<script>
// import {h} from 'vue';

export default {
  name: 'Test',
  setup() {
    const name = '蓝忘机';
    const alertMessage = () => {
      alert('魔道祖师在10月16号完结了！！')
    }
    //可以返回一个对象，该对象里面的属性可以直接在模板中使用
    return {
      name,
      alertMessage
    }
    //  也可以返回一个渲染函数该函数会替换掉模板里面的全部内容
    // return () => h('h1', '魏无羡')

  }
}
</script>
