<template>
  <div class="ratingselect">
    <div class="rating-type border-1px">
      <span class="block positive">{{desc.all}}
        <span class="count">47</span>
      </span>
      <span class="block positive">{{desc.positive}}
        <span class="count">38</span>
      </span>
      <span class="block negative">{{desc.negative}}
        <span class="count">7</span>
      </span>
    </div>
    <div class="switch">
      <span class="icon-check_circle"></span>
      <span class="text">只看有内容的评价</span>
    </div>
  </div>
</template>

<script type="text/ecamscript-6">
const POSITIVE = 0;
const NEGATIVE = 1;
const ALL = 2;

export default {
  props: {
    ratings: {
      type: Array,
      default() {
        return [];
      }
    },
    selectType: {
      type: Number,
      default: ALL
    },
    onlyContent: {
      type: Boolean,
      default: false
    },
    desc: {
      type: Object,
      default() {
        return {
          all: "全部",
          positive: "满意",
          negative: "不满意"
        };
      }
    }
  }
};
</script>

<style lang="stylus" rel='stylesheets/stylus'>
@import "../../common/stylus/mixin.styl"
  .ratingselect
    .rating-type
      padding 18px 0
      margin  0 18px
      border-1px(rgba(7, 17, 27 ,0.1))
      font-size 0
      .block
          display inline-block
          padding 8px 12px
          margin-right 8px
          line-height 16px
          border-radius 1px
          font-size 12px
          color rgb(77, 85, 93)
          .count
            margin-left 2px
            font-size 8px
          &.positive
            background rgba(0, 160, 220, 0.2)
          &.negative
            background rgba(78, 85, 93, 0.2)  
    // .switch
    //   .icon-check_circle
    //   .text
</style>
