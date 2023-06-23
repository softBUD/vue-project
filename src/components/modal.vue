<template>
  <div>
    <transition>
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
    </transition>
    <button v-if="!open" @click="openState" class="border border-slate-200 bg-white m-0 p-0">
      모달오픈
    </button>
  </div>
  <button
    v-if="!slideOpen"
    @click="openSlideState"
    class="border border-slate-200 bg-white m-0 p-0"
  >
    슬라이드 토스트
  </button>
  <transition name="slide">
    <div
      v-if="slideOpen"
      class="absolute left-1/3 top-44 border-box border border-slate-200 bg-white rounded-lg pr-[200px] pl-[200px] pb-[100px]"
    >
      <button v-if="slideOpen" @click="closeSlideState">토스트 닫기</button>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'DefaultDialog',
  data() {
    return {
      openModal: false,
      slideOpen: false
    }
  },

  props: {
    open: Boolean,
    title: String,
    content: String
  },
  methods: {
    openState() {
      this.$emit('modal-open', true)
    },
    closeState() {
      this.$emit('modal-close', false)
    },

    openSlideState() {
      this.slideOpen = true
    },

    closeSlideState() {
      this.slideOpen = false
    }
  }
}
</script>

<style>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.slide-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-enter-active {
  transition: all 0.3s ease-out;
}

.slide-enter-from,
.slide-leave-to {
  transform: translateX(20px);
  opacity: 0;
}
</style>
