<template>
  <div>
    <base-slider :list="list" :width="520" :height="280">
    </base-slider>
  </div>
</template>

<script>
import BaseSlider from '@/components/baseSlider/baseSlider'

export default {
  components: {
    BaseSlider
  },

  data () {
    return {
      list: [
        {
          img: '//img.alicdn.com/tps/i4/TB1PbnMGMHqK1RjSZFgSuu7JXXa.jpg_240x240q90.jpg',
          img2: '//img.alicdn.com/tps/i4/TB1a.TvSwTqK1RjSZPhSutfOFXa.jpg_240x240q90.jpg',
          img3: 'https://img.alicdn.com/simba/img/TB13_CcP7voK1RjSZFwSuwiCFXa.jpg'
        },
        {
          img: '//img.alicdn.com/tps/i4/TB1N2B5SmzqK1RjSZFpSuukSXXa.jpg_240x240q90.jpg',
          img2: 'https://aecpm.alicdn.com/simba/img/TB1X6uHLVXXXXcCXVXXSutbFXXX.jpg',
          img3: 'https://img.alicdn.com/simba/img/TB16UXzMY2pK1RjSZFsSuuNlXXa.jpg'
        },
        {
          img: '//img.alicdn.com/tps/i4/TB1DHBYLFYqK1RjSZLeSuvXppXa.jpg_240x240q90.jpg',
          img2: '//img.alicdn.com/tps/i4/TB1gyDdOgHqK1RjSZFkSut.WFXa.jpg_240x240q90.jpg',
          img3: '//img.alicdn.com/tfs/TB1pV79SyLaK1RjSZFxXXamPFXa-520-280.jpg_q90_.webp'
        }
      ]
    }
  }
}
</script>

<style lang="less" scoped>
.slie-container {
  width: 490px;
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: #fff;
}
.slide-page {
  width: 520px;
  height: 280px;
}
</style>
