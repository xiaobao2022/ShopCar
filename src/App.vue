<template>
  <div id="app">
    <MyHeader color="#FFF" title="购物车案例" />
    <MyGoods v-for="item in goodsList" :key="item.id" :goods="item"/>
    <MyFooter :goodsList="goodsList"/>
  </div>
</template>

<script>
import MyHeader from '#/MyHeader.vue'
import MyGoods from '#/MyGoods.vue'
import MyFooter from '#/MyFooter.vue'
import axios from 'axios'

export default {
  components: {
    MyHeader,
    MyGoods,
    MyFooter
  },
  data() {
    return {
      goodsList: []
    }
  },
  created() {
    this.getGoods()
  },
  methods: {
    async getGoods() {
      const res = await axios({
        url: '/api/cart'
      })
      console.log(res)
      this.goodsList = res.data.list
    }
  }
}
</script>

<style>
#app {
  box-sizing: border-box;
  padding: 50px 0;
  max-height: 100vh;
  overflow: auto;
}
</style>
