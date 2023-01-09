<template>
  <h4>當前的x值是: {{x.y}}</h4>
  <button @click="x.y++">點我x+1</button>
  <hr>
  <h4>{{person}}</h4>
  <h2>姓名: {{name}}</h2>
  <h2>年齡: {{age}}</h2>
  <h2>薪資: {{job.j1.salary}}K</h2>
  <button @click="name+='~'">修改姓名</button>
  <button @click="age++">增長年齡</button>
  <button @click="job.j1.salary++">漲薪</button>
</template>

<script>
import { ref, reactive, toRef, toRefs, shallowReactive, shallowRef } from 'vue'

export default {
  name: 'MyDemo',
  setup() {
    // 數據
    // shallowRef: 只處理基本數據類型，不進行對象的響應式處理
    // shallowReactive: 只會修改第一層，第二層以上不會修改
    let person = shallowReactive({
      name: 'Cake',
      age: 18,
      job: {
        j1: {
          salary: 20
        }
      }
    })

    // let x = shallowRef(0)
    let x = ref({
      y: 0
    })
    console.log('***', x);

    // 返回一個對象(常用)
    return {
      x,
      person,
      ...toRefs(person)
    }
  }
}
</script>
