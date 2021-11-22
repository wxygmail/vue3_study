<template>
  <div>

  </div>
</template>

<script>
import {isRef, reactive, ref, isReactive, readonly, isReadonly, isProxy} from "vue";

export default {
  setup() {
    const num = ref(0);
    const person = reactive({});
    const read_person = readonly(person);
    const read_num = readonly(num);

    /**
     *
     * isRef : 检查一个值是否为ref对象
     * isReactive : 检查一个值是否为reactive对象
     * isReadonly: 检查值是否有readonly创建的只读对象
     * isProxy: 检查值是否为reactive 或者 readonly创建的对象
     *
     */

    console.log('num is ref ?? ', isRef(num));
    console.log('person is ref ?? ', isRef(person));
    console.log('num is reactive ?? ', isReactive(num));
    console.log('person is reactive ?? ', isReactive(person));
    console.log('read_person is reactive ?? ', isReactive(read_person));
    console.log('read_person isProxy ?? ', isProxy(read_person));
    console.log('person isProxy ?? ', isProxy(person));
    console.log('num  isProxy ?? ', isProxy(num));
    console.log('read_person isReadonly ?? ', isReadonly(read_person));
    console.log('read_num isReadonly ?? ', isReadonly(read_num));

  }

}
</script>
