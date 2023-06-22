<template>
  <div>
    <div
      v-if="open"
      class="fixed z-30 w-screen h-screen overflow-hidden bg-[rgba(0,0,0,0.5)] box-border"
    >
      <div class="absolute left-1/3 top-44 border-box bg-white rounded-lg p-[200px]">
        <h4 class="font-bold relative bottom-32">{{ title }}</h4>
        <p class="relative bottom-20 left-2">{{ content }}</p>
        <button v-if="open" @click="closeState" class="border border-slate-200 bg-white m-0 p-0">
          모달닫기
        </button>
      </div>
    </div>
    <button v-if="!open" @click="openState" class="border border-slate-200 bg-white m-0 p-0">
      모달오픈
    </button>
  </div>
</template>

<script>
export default {
  name: 'DefaultDialog',
  data() {
    return {
      openModal: false
    }
  },

  props: {
    open: Boolean,
    title: String,
    content: String
  },
  methods: {
    openState() {
      this.$emit('modalOpen', true)
    },
    closeState() {
      this.$emit('modalClose', false)
    }
  }
}
</script>

<style></style>
