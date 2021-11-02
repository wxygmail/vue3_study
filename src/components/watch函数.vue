<template>
  <div>
    <p>数字变化：{{ sum }}</p>
    <button @click="sum++">点我+1</button>
    <p>打招呼：{{ message }}</p>
    <button @click="message+='a'">点我打招呼</button>
    <hr>
    <p>person 个人数据：{{ person }}</p>
    <button @click="person.name+='~'">改变姓名</button>
    <button @click="person.age++">改变年龄</button>
    <button @click="person.work.job1.salary++">改变薪资</button>
  </div>
</template>

<script>
import {reactive, ref, watch} from "vue";

export default {
  name: "Test",
  watch: {
    person() {
      console.log('111')
    }
  },
  setup() {
    const sum = ref(0);
    const message = ref('hello')
    const person = reactive({
      name: '蓝忘机',
      age: 18,
      work: {
        job1: {
          salary: 20
        }
      }
    });
    //-----监听ref定义的一个响应式数据
    // watch(sum, (newVal, oldVal) => {
    //   console.log('sum发生了改变：', newVal, oldVal)
    // }, {immediate: true})

    //-----监听多个ref定义的响应式数据
    // watch([sum, message], (newVal, oldVal) => {
    //   console.log('sum或者message发生了改变：', newVal, oldVal)
    // })

    /**
     * -----监听reactive定义的一个响应式数据
     * 注意点：
     * 1、reactive 定义的数据无法正确获取oldVal
     *  --- 解决办法：可以把需要oldVal的属性拿出来用ref进行定义
     *  --- 单独监听某个不是对象的属性
     * 2、reactive 默认开启深度监听，并且无法关闭，deep:false配置无效
     */
    watch(person, (newVal, oldVal) => {
      console.log('person发生了改变：', newVal, oldVal)
    }, {deep: false})

    //----- 监听reactive定义的一个响应式数据中的某个属性
    // watch(()=>person.name, (newVal, oldVal) => {
    //   console.log('person发生了改变：', newVal, oldVal)
    // })

    //----- 监听reactive定义的一个响应式数据中的某些属性
    // watch([() => person.name, () => person.work], (newVal, oldVal) => {
    //   console.log('person发生了改变：', newVal, oldVal)
    // })

    /**
     *  ----- 监听reactive定义的一个响应式数据中的属性值为对象类型的数据
     *  主意：此时配置的deep有效，监听的数据为reactive定义上的某个对象属性
     */
    // watch(() => person.work, (newVal, oldVal) => {
    //   console.log('person发生了改变：', newVal, oldVal)
    // }, {deep: true})


    return {
      sum,
      message,
      person
    }
  }
}
</script>

<style scoped>

</style>
