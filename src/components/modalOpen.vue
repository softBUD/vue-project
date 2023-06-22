<script setup>
import DefaultDialog from './modal.vue'
</script>
>
<script>
export default {
  name: 'ModalOpen',
  data() {
    return {
      openModal: false
    }
  },
  setup() {},
  created() {},
  mounted() {},
  unmounted() {},
  methods: {
    openRun(value) {
      console.log(this.openModal)
      this.openModal = value
    },
    closeRun(value) {
      console.log(this.openModal)
      this.openModal = value
    }
  }
}
</script>
<template>
  <div>
    <DefaultDialog
      :open="openModal"
      @modal-close="openRun"
      @modal-open="closeRun"
      title="모달창의 제목"
      content="모달창의 내용"
    />
  </div>
</template>
