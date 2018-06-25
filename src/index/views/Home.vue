<template>
  <div class="home">
    <img src="@/assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  components: {
    HelloWorld
  },
  mounted() {
    console.log(`这个是默认页面的主页：${this.$store.state.myname}`)
  }
}
</script>
