<template>
  <div class="hello">
    <img :src="imgUrl" alt="">
    <div>ajs: {{Ajs}}</div>
    <button @click="clickBotton" v-if="Bjs">点击加载B.JS</button>
    <div v-if="Bjs">bjs:{{Bjs}}</div>
  </div>
</template>

<script>
import Ajs from '@/assets/js/a.js'
export default {
  name: 'HelloWorld',
  data () {
    return {
      Ajs: Ajs,
      imgUrl: require('@/assets/img/logo.png'),
      Bjs: {}
    }
  },
  watch: {},
  computed: {},
  methods: {
    clickBotton: function () {
      console.log(this)
      require.ensure([], () => {
        console.log(this)
        this.Bjs = require('@/assets/js/b.js').default
      })
    }
  }
}
</script>

<style scoped>
@import url(../assets/css/b.css);
@import '../assets/css/a.css';
</style>
