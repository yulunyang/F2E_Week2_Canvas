<template>
  <div class="loading w-full h-screen left-0 top-0 z-50">
    <!-- <div class="py-4 px-6 md:px-28 lg:px-8 hidden xl:block">
      <img src="@/assets/img/logo.png" alt="" class="object-contain block">
    </div> -->
    <div class="loading-text absolute text-xl">
      <div v-if="isSuccess">
        <img src="@/assets/img/success.png" alt="" class="object-contain block mb-5 mx-auto">
        <p class="typing-loading text-center font-semibold text-xl xl:text-2xl proj-text-black whitespace-nowrap">下載成功</p>
      </div>
      <div v-if="!isSuccess">
        <img src="@/assets/img/warning.png" alt="" class="object-contain block mb-5 mx-auto">
        <p class="typing-loading text-center font-semibold text-xl xl:text-2xl proj-text-black whitespace-nowrap">下載失敗，請稍後再試</p>
      </div>
      <!-- <button type="button" class=" py-4 px-28 proj-bg-Gradient text-white rounded-2xl h-auto mt-20">回首頁</button> -->
      <a class="py-4 px-28 proj-bg-Gradient text-white rounded-2xl h-auto mt-20 hidden xl:inline-block cursor-pointer" @click="backIndex">回首頁</a>
    </div>

    <div class="absolute bottom-5 xl:hidden left-1/2 -translate-x-1/2">
      <a class="py-4 px-28 proj-bg-Gradient text-white rounded-2xl h-auto inline-block whitespace-nowrap cursor-pointer" @click="backIndex">回首頁</a>
    </div>
  </div>
</template>

<script>
import { onMounted, onUnmounted, ref } from 'vue'
export default {
  components: {
  },
  props: {
  },
  setup (props, ctx) {
    const isSuccess = ref(true)
    onMounted(() => {
      // random()
    })
    onUnmounted(() => {
    })

    const random = () => {
      let num = Math.floor(Math.random() * 100) + 1
      if (num > 90) {
        isSuccess.value = false
      }

      isSuccess.value = true
    }
    const backIndex = () => {
      ctx.emit('backIndex')
    }
    return {
      backIndex,
      random,
      isSuccess
    }
  }
}
</script>

<style scoped lang="scss">
.loading {
  // background-image: url('@/assets/img/leaf1.png'), url('@/assets/img/leaf2.png');
  // background-position: left bottom, right top;
  // background-repeat: no-repeat;
  background-color: rgb(255, 255, 255, 1);
}
.loading-text {
  left: 50%;
  top: 40%;
  transform: translate(-50%, -50%);
}
</style>
