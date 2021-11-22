<template>
  <div>
<!--    <p>person 个人数据：{{ person }}</p>-->
    <p>name:{{ name }}</p>
    <p>age:{{ age }}</p>
    <p>薪资:{{ work.job1.salary }}</p>
    <button @click="name+='~'">改变姓名</button>
    <button @click="age++">改变年龄</button>
<!--    <button @click="salary++">改变薪资</button>-->
    <button @click="work.job1.salary++">改变薪资</button>
  </div>
</template>

<script>
import {reactive, toRefs, toRef, ref} from "vue";

export default {
  setup() {
    const person = reactive({
      name: '蓝忘机',
      age: 18,
      work: {
        job1: {
          salary: 20
        }
      }
    });
    console.log(person)
    return {
      // person,
      // name: person.name, //相当于 name ： '蓝忘机'，重新定义了一个属性，并且没有响应式
      // name: ref(person.name), //数据分家了 相当于 const name = ref('person.name')
      // name: toRef(person, 'name'), //关联源对象
      // age: person.age,
      // salary: person.work.job1.salary,
      // age: toRef(person, 'age'),
      // salary: toRef(person.work.job1, 'salary'),
      //  多个属性时
      // ...toRefs(person)
      ...person
    }
  }
}
</script>

<style scoped>

</style>
