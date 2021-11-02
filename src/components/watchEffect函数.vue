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
import {reactive, ref, watchEffect} from "vue";

export default {
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
    /**
     *  watchEffect 回调中用到哪个属性就监听那个属性值得变化
     *  ---- 默认开启immediate:true
     */
    watchEffect(() => {
      const sum1 = sum.value;
      const age1 = person.age;
      console.log('watchEffect回调函数执行了')
    })
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
