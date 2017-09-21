<template>
  <div class="star" :class="starType">
    <span v-for="itemClass in itemClasses" :class="itemClass" class="star-item" track-by="$index"></span>
  </div>
</template>

<script type="text/ecamscript-6">
const LENGTH = 5;
const CLS_ON = 'on'
const CLS_HALF = 'half'
const CLS_OFF = 'off'

export default {
  props: {
    size: {
      type: Number
    },
    score: {
      type: Number
    }
  },
  computed: {
    starType() {
      return 'star-' + this.size;
    },
    itemClasses() {
      let result = []
      let score = Math.floor(this.score * 2) / 2  // Math.floor(x)返回小于等x的最小整数
      let hasDecimal = score % 1 !== 0  // hasDecimal 类型为 boolean
      let integer = Math.floor(score)
      for (let i = 0; i < integer; i++) {
        result.push(CLS_ON)
      }
      if (hasDecimal) {             // 只会出现一次半星
        result.push(CLS_HALF)
      }
      while (result.length < LENGTH) {      // 不满的用OFF补齐
        result.push(CLS_OFF)
      }
      return result
    }
  }
};
</script>

<style lang="stylus" rel='stylesheets/stylus'>
  @import "../../common/stylus/mixin.styl";
  .star
    font-size 0
    .star-item
      display inline-block
      background-repeat no-repeat  
    &.star-48
      .star-item
        width 20px
        height 20px
        margin-right 22px
        background-size 20px 20px
        &:last-child
          margin-right 0
        &.on
          bg-image('star48_on')
        &.half
          bg-image('star48_half')
        &.off
          bg-image('star48_off')                    
    &.star-36
      .star-item
        width 15px
        height 15px
        margin-right 6px
        background-size 15px 15px
        &:last-child
          margin-right 0
        &.on
          bg-image('star36_on')
        &.half
          bg-image('star36_half')
        &.off
          bg-image('star36_off')   
    &.star-24
      .star-item
        width 10px
        height 10px
        margin-right 3px
        background-size 10px 10px
        &:last-child
          margin-right 0
        &.on
          bg-image('star24_on')
        &.half
          bg-image('star24_half')
        &.off
          bg-image('star24_off')  
</style>
