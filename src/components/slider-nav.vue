<template>
  <div class="slider-container">
    <div class="slider-nav" ref="sliderNav">
      <div class="slider" :style="{'left':distance+'px'}"></div>
      <div class="nav-group">
        <div class="nav-item" v-for="(item,index) in navList" :class="{active:index === activeIndex}"
             @click="chooseNav(index)">{{item}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "slider-nav",
    props: {
      navList: {
        type: Array,
        required: true
      },
      callBack: {},
      initIndex: {
        type: Number,
        required: false,
        default: 0,
      }
    },
    data() {
      return {
        distance: '',
        sliderWidth: '',
        activeIndex: '',
      }
    },
    mounted() {
      this.sliderWidth = this.$refs.sliderNav.offsetWidth / this.navList.length;
      this.activeIndex = this.initIndex;
    },
    methods: {
      chooseNav(index) {
        if (index === this.activeIndex) return;
        this.activeIndex = index;
        this.distance = index * this.sliderWidth;
        if (this.callBack) {
          this.callBack(index);
        }
      }
    }
  }
</script>

<style scoped lang="stylus">
.slider-container
  text-align center
  .slider-nav
    box-shadow 0 0 10px rgba(0, 0, 0, .1)
    border-radius 34px
    display inline-block
    position relative
    width auto
    .slider
      width 33.33%
      height 34px
      position absolute
      border-radius 34px
      background #ff5a60
      transition left .3s
    .nav-group
      position relative
      overflow auto
      z-index 1
      .nav-item
        float left
        font-size 14px
        line-height 1
        padding 10px 20px
        transition color .3s
        &.active
          color #fff
</style>
