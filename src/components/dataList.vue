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
        { title: '상품1', price: '1000원' },
        { title: '상품2', price: '2000원' },
        { title: '상품3', price: '3000원' }
      ]
    }
  },
  methods: {
    increase() {
      this.clicked++
    }
  }
}
</script>
