<template>
  <div>
    名字：<input type="text" v-model="person.name">
    <br>
    年龄：<input type="text" v-model="person.age">
    <br>
    <!--    <p>{{ person.fullName }}</p>-->
    <input type="text" v-model="person.fullName">
  </div>
</template>

<script>
import {reactive, computed} from "vue";

export default {
  name: "Test",
  // computed: {
  //   fullName: () => {
  //     return this.person.name + '---' + this.person.age
  //   }
  // },
  setup() {
    const person = reactive({
      name: '蓝忘机',
      age: 18,
      fullName: ''
    });
    //仅仅考虑到读的情况
    person.fullName = computed(() => {
      return `${person.name} -- ${person.age}`
    });
    //读写兼顾
    person.fullName = computed({
      get: () => {
        return `${person.name}:${person.age}`;
      },
      set: (value) => {
        const arr = value.split(':');
        person.name = arr[0];
        person.age = arr[1];
      }
    })
    return {
      person,
    }
  }
}
</script>

<style scoped>

</style>
