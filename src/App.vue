<template>
  <div>
    <el-button @click="showPrice">{{buttonText}}</el-button>
    <el-table
      :data="sumPhraseJson"
    >
      <el-table-column label="商品名称" prop="name"></el-table-column>
      <el-table-column label="售价" prop="price" v-show="isShowPrice"></el-table-column>
      <el-table-column label="生产日期" prop="date"></el-table-column>
    </el-table>
  </div>
</template>

<script>
import { computed, ref } from 'vue'
export default {
  name: 'App',
  components: {
  },
  setup() {
    const isShowPrice = ref(false)
    const sumPhraseJson = [
      {
        name: 'Apple',
        price: 10,
        date: '2021-10-21'
      },
      {
        name: 'Banana',
        price: 14,
        date: '2021-10-22'
      },
      {
        name: 'Orange',
        price: 9,
        date: '2021-10-20'
      },
    ]
    const showPrice = () => {
      isShowPrice.value = !isShowPrice.value
    }
    return {
      sumPhraseJson,
      showPrice,
      isShowPrice,
      buttonText: computed(() => isShowPrice.value ? '隐藏售价' : '显示售价')
    }
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
