<template>
  <div>
    <p>名字：{{ name }}</p>
    <p>地址：{{ person.address }}</p>
    <p>薪资：{{ person.money }}</p>
    <p>工作性质：{{ person.job.info.name }}</p>
    <button @click="changeInfo">改变信息</button>
  </div>
</template>

<script>
import {reactive} from 'vue';

export default {
  name: "Test",
  setup() {
    /**
     * reactive定义基本类型无法成为响应式
     * warning -->  value cannot be made reactive: 蓝忘机
     */
    const name = reactive('蓝忘机');
    /**
     * 返回一个代理对象（Proxy的实例对象，简称Proxy对象）
     * 内部基于ES6的Proxy实现的，通过代理对象操作源对象内部数据进行操作
     */
    const person = reactive({
      address: '云深不知处',
      money: 10,
      job: {
        info: {
          name: '程序员~~'
        }
      }
    });
    const changeInfo = () => {
      person.address = '莲花坞~~';
      person.job.info.name = '美美哒程序员~~~';
    };
    return {
      name,
      person,
      changeInfo
    }
  }
}
</script>
