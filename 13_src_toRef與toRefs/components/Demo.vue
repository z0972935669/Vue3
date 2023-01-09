<template>
  <h4>{{person}}</h4>
  <h2>姓名: {{name}}</h2>
  <h2>年齡: {{age}}</h2>
  <h2>薪資: {{job.j1.salary}}K</h2>
  <button @click="name+='~'">修改姓名</button>
  <button @click="age++">增長年齡</button>
  <button @click="job.j1.salary++">漲薪</button>
</template>

<script>
import { reactive, toRefs } from 'vue'

export default {
  name: 'MyDemo',
  setup() {
    // 數據
    let person = reactive({
      name: 'Cake',
      age: 18,
      job: {
        j1: {
          salary: 20
        }
      }
    })

    const name1 = person.name
    console.log('%%%', name1);

    // const name2 = toRef(person, 'name')
    // console.log('###', name2);

    const x = toRefs(person)
    console.log('****', x);

    // 返回一個對象(常用)
    return {
      // person,
      // toRef,
      // name: toRef(person, 'name'),
      // age: toRef(person, 'age'),
      // salray: toRef(person.job.j1, 'salary'),
      // ref,
      // name: ref(person.name),
      // age: ref(person.age),
      // salary: ref(person.job.j1.salary),
      // toRefs,
      ...toRefs(person)
    }
  }
}
</script>
