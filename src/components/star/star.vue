<template>
  <div class="star" :class="'star-'+size">
    <span class="star-item" v-for="sc in starClasses" :class="sc"></span>
  </div>
</template>

<script>

  const CLASS_ON = 'on'
  const CLASS_HALF = 'half'
  const CLASS_OFF = 'off'

  // 0-5  3.4 3.5
  export default {
    props: {
      score: Number,
      size: Number
    },

    computed: {
      starClasses () {
        const scs = []

        // 添加 CLASS_ON
        const scoreInteger = Math.floor(this.score)
        for (let i = 0; i < scoreInteger; i++) {
          scs.push(CLASS_ON)
        }
        // 添加 CLASS_HALF
        if(this.score-scoreInteger>=0.5) {
          scs.push(CLASS_HALF)
        }
        // 添加 CLASS_OFF
        while(scs.length<5) {
          scs.push(CLASS_OFF)
        }

        return scs
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixins.styl"
  .star-24
    text-align center
    .star-item
      display inline-block
      width 10px
      height 10px
      background-repeat no-repeat
      background-size 10px 10px
    .on
      bg-star(star24_on)

    .half
      bg-star(star24_half)
    .off
      bg-star(star24_off)

  .star-36
    text-align center
    .star-item
      display inline-block
      width 15px
      height 15px
      background-repeat no-repeat
      background-size 15px 15px
    .on
      bg-star(star36_on)

    .half
      bg-star(star36_half)
    .off
      bg-star(star36_off)

  .star-48
    text-align center
    .star-item
      display inline-block
      width 22px
      height 22px
      background-repeat no-repeat
      background-size 22px 22px
    .on
      bg-star(star48_on)

    .half
      bg-star(star48_half)
    .off
      bg-star(star48_off)

</style>