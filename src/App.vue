<!--
 * @Author: Mencre
 * @LastEditors: Mencre
 * @email: mencre@163.com
 * @Date: 2020-09-06 17:03:16
 * @LastEditTime: 2020-09-06 17:27:34
 * @Description: Modify here please
-->
<template>
  <div id="app">
    <h1>============Count.vue Demo============</h1>
    <Count></Count>
    <h1>============Dog.vue Demo>============</h1>
    <Dog></Dog>
  </div>
</template>

<script>
import Count from './components/Count.vue'
import Dog from './components/Dog.vue'

export default {
  name: 'App',
  components: {
    Count,
    Dog
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
