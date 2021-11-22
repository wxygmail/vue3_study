<template>
  <div class="home">
    <Test address="11111" @handleClick="handleClick">
      <template v-slot:hello>
        <p>setUp函数里面的插槽内容</p>
      </template>
    </Test>
  </div>
</template>

<script>
import Test from '../components/Suspense.vue'

export default {
  name: 'Home',
  components: {
    Test
  },
  setup() {
    const handleClick = (value) => {
      console.log(value)
    };
    return {
      handleClick
    }
  }
}
</script>
