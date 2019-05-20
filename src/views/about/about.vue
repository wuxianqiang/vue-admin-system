<template>
  <div class="about">
    <base-select v-model="value">
      <base-option
        v-for="(item, index) in options"
        :key="index"
        :label="item.label"
        :value="item.value">
      </base-option>
    </base-select>

    <base-collapse-wrapper>
      <base-collapse title="选项1">
        <div>
          <div>与现实生活一致：与现实生活的流程、逻辑保持一致，遵循用户习惯的语言和概念；</div>
          <div>在界面中一致：所有的元素和结构需保持一致，比如：设计样式、图标和文本、元素的位置等。</div>
        </div>
      </base-collapse>
      <base-collapse title="选项2">
        <div>
          <div>与现实生活一致：与现实生活的流程、逻辑保持一致，遵循用户习惯的语言和概念；</div>
          <div>在界面中一致：所有的元素和结构需保持一致，比如：设计样式、图标和文本、元素的位置等。</div>
        </div>
      </base-collapse>
    </base-collapse-wrapper>
  </div>
</template>

<script>
import BaseSelect from '@/components/baseSelect/baseSelect'
import BaseOption from '@/components/baseSelect/baseOption'
import BaseCollapse from '@/components/baseCollapse/baseCollapse'
import BaseCollapseWrapper from '@/components/baseCollapse/baseCollapseWrapper'

export default {
  components: {
    BaseSelect,
    BaseOption,
    BaseCollapse,
    BaseCollapseWrapper
  },
  data () {
    return {
      options: [{
        value: '选项1',
        label: '黄金糕'
      }, {
        value: '选项2',
        label: '双皮奶'
      }, {
        value: '选项3',
        label: '蚵仔煎'
      }, {
        value: '选项4',
        label: '龙须面'
      }, {
        value: '选项5',
        label: '北京烤鸭'
      }],
      value: '选项5'
    }
  },
  methods: {
    handleClick () {
    }
  }
}
</script>

<style lang="less" scoped>
.about-title {
  line-height: 36px;
  font-size: 18px;
}
</style>
