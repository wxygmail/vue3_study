<template>
  <div>
    <p>名字：{{ name }}</p>
    <p>地址：{{ person.address }}</p>
    <p>薪资：{{ person.money }}</p>
    <button @click="changeInfo">改变信息</button>
  </div>
</template>

<script>
//RefImpl:因应对象 -- reference implement
import {ref} from 'vue';

/**
 * ref本质也是reactive，ref(obj)等价于reactive({value: obj})
 */
export default {
  name: "Test",
  setup() {
    let name = ref('蓝忘机');
    const person = ref({
      address: '云深不知处',
      money: 10
    })
    const changeInfo = () => {
      console.log(name) //RefImpl {.....}
      console.log(person)
      //  错误写法
      // name = '魏无羡';
      //  正确写法
      name.value = '魏无羡';
      person.value.address = '莲花坞~~';
    };
    return {
      name,
      person,
      changeInfo
    }
  }
}
</script>
