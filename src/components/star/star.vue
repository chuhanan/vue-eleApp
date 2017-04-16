<template>
  <div class="star" :class="starType">
    <span trace-key="$index" v-for="itemsClass in itemsClass" :class="itemsClass" class="star-item"></span>
  </div>
</template>

<script type="text/ecmascript-6">
  const len = 5
  const clsOn = 'on'
  const clsHalf = 'half'
  const clsOff = 'off'
  export default {
    props:{
      size:{
        type:Number
      },
      score:{
        type:Number
      }
    },
    created () {
      console.log(this.score)
    },
    computed:{
      starType () {
        return 'star-' + this.size
      },
      itemsClass () {
        let result = []
        let score = Math.floor(this.score * 2) / 2
        let hasDecimal = score % 1 !== 0
        let integer = Math.floor(score)
        for (let i = 0; i < integer; i++) {
          result.push(clsOn)
        }
        if (hasDecimal) {
          result.push(clsHalf)
        }
        while (result.length < len) {
          result.push(clsOff)
        }
        return result
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixin.styl"

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
