<script setup>
import Home from '@/components/home/index.vue'
import autofit from 'autofit.js';
onMounted(() => {
  /*
     * - 传入对象，对象中的属性如下：
     * - el（可选）：渲染的元素，默认是 "body"
     * - dw（可选）：设计稿的宽度，默认是 1920
     * - dh（可选）：设计稿的高度，默认是 1080
     * - resize（可选）：是否监听resize事件，默认是 true
     * - ignore(可选)：忽略缩放的元素（该元素将反向缩放），参数见readme.md
     * - transition（可选）：过渡时间，默认是 0
     * - delay（可选）：延迟，默认是 0
  */
  autofit.init({
    el: '#homeScreen',
    dw: 1920,
    dh: 1080
  })
})
</script>

<template>
  <suspense>
    <Home id="homeScreen"></Home>
  </suspense>
</template>
