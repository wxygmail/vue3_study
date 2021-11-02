<template>
  <div>
    <p>名字：{{ name }}</p>
    <button @click="alertMessage">点击弹窗</button>
    <slot name="hello"></slot>
    <button @click="handleClick">触发点击emit</button>
  </div>
</template>

<script>
// import {h} from 'vue';

export default {
  name: 'Test',
  //如果未在这里定义的props，就会存在于attrs（感觉在捡漏）中
  // props: ['address'],
  // emits: ['handleClick'],
  // setup(props, {emit, slots, attrs}) {
  setup(props, context) {
    console.log('---props---', props)
    console.log('---emit---', context)
    const name = '蓝忘机';
    const alertMessage = () => {
      alert('魔道祖师在10月16号完结了！！')
    }
    const handleClick = () => {
      context.emit('handleClick', '点击了')
    }
    //可以返回一个对象，该对象里面的属性可以直接在模板中使用
    return {
      name,
      alertMessage,
      handleClick
    }
    //  也可以返回一个渲染函数该函数会替换掉模板里面的全部内容
    // return () => h('h1', '魏无羡')

  }
}
</script>
