<template>
  <div class="flex flex-col">
    <!-- :key는 각 태그를 구별하기 위한 속성, 필수 -->
    <div v-for="(item, i) in productsData" :key="i">
      {{ item.title }}
      {{ item.price }}
    </div>
    <button @click="increase" class="border border-slate-200 w-60">
      버튼{{ clicked }}번째 클릭
    </button>
    <button @click="priceSort" class="border border-slate-200 w-60">가격순</button>
  </div>
</template>

<script>
export default {
  name: 'DataList',
  data() {
    return {
      clicked: 0,
      prices: ['1000', '2000', '3000'],
      products: ['상품1', '상품2', '상품3'],
      productsData: [
        { title: '상품1', price: '4000' },
        { title: '상품2', price: '2000' },
        { title: '상품3', price: '9000' },
        { title: '상품4', price: '1000' },
        { title: '상품5', price: '10000' }
      ]
    }
  },
  methods: {
    increase() {
      this.clicked++
    },
    priceSort() {
      // sort는 원본을 변형시킴
      this.productsData.sort(function (a, b) {
        return a.price - b.price
      })
    }
  },
  created() {
    // 마운트 되기 전, 보통 api 통신 요청
  },
  mounted() {
    // 마운트 되고난 후
  }
}
</script>
