<template>
  <div id="app">
    <p>{{testProp}}</p>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Button type="success" @click="messageTip">测试弹框</Button>
  </div>
</template>

<script>
import Vue from 'vue'
// import 'element-ui/lib/theme-chalk/index.css'
// import 'element-ui/lib/theme-chalk/index.css';
import HelloWorld from './components/HelloWorld.vue'
import { Button, Message } from 'element-ui'
import axios from 'axios'
Vue.prototype.$message = Message;
export default {
  name: 'app',
  props: ['testProp'],
  components: {
      HelloWorld,
      Button
  },
  methods: {
    messageTip () {
      axios.post('http://rap2api.taobao.org/app/mock/85572/account/list', {
        "page": 1,
        "status": 2
      })
      .then(res => {
        this.$message({
          type: 'success',
          message: res.data.code
        })
      })
    }
  }
}
</script>

<style>
@import 'https://unpkg.com/element-ui/lib/theme-chalk/index.css';
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
