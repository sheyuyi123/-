<template>
  <div class="app">
    <my-header title="购物车案例" color="#999" />
    <my-goods v-for="item in goodsList" :key="item.goods_id" :goods="item" />
    <my-footer :goodsList="goodsList" />
  </div>
</template>

<script>
import MyFooter from '@/components/MyFooter.vue'
import MyGoods from '@/components/MyGoods.vue'
import MyHeader from '@/components/MyHeader..vue'
import axios from 'axios'
export default {
  components: { MyHeader, MyGoods, MyFooter },
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
      try {
        const res = await axios({ url: '/api/cart' })
        this.goodsList = res.data.list
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>

<style scope>
.app {
  padding: 50px 0;
}
</style>
