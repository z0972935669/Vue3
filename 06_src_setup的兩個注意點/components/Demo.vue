<template>
  <div>
    <h1>{{ msg }}</h1>
    <h1>{{ school }}</h1>
    <slot name="qwe"></slot>
    <slot name="asd"></slot>
    <hr>
    <h1>一個人的信息</h1>
    <h2 v-show="person.name">姓名: {{ person.name }}</h2>
    <h2>年齡: {{ person.age }}</h2>
    <button @click="test">測試觸發一下Demo組件的Hello事件</button>
  </div>
</template>

<script>
import { reactive } from 'vue'

export default {
  name: 'MyDemo',
  props: ['msg', 'school'],
  emits: ['hello'],
  setup(props, context) {
    // console.log('props :>> ', props);
    // console.log('context.attrs :>> ', context.attrs); // 相當於Vue2中的$attrs
    // console.log('context.emit :>> ', context.emit); // 觸發自定義事件
    // console.log('context.slots :>> ', context.slots); // 插槽

    // 數據
    let person = reactive({
      name: 'John',
      age: 18
    })

    // 方法
    function test() {
      context.emit('hello', 888, 666, 222)
    }

    // 返回一個對象(常用)
    return {
      person,
      test
    }
  }
}
</script>
