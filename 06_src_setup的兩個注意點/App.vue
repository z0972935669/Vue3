<template>
  <Demo @hello="showHelloMsg" msg="你好嗎" school="尚硅谷">
    <template v-slot:qwe>
      <div>
        Allen
      </div>
    </template>
    <template v-slot:asd>
      <div>
        Cake
      </div>
    </template>
  </Demo>
</template>

<script>
import Demo from './components/Demo.vue'

export default {
  name: 'App',
  components: {
    Demo
  },
  setup() {
    function showHelloMsg(...value) {
      alert(`你好啊，你觸發了hello事件，我收到的參數是:${value}!`)
    }

    return {
      showHelloMsg
    }
  }
}
</script>
