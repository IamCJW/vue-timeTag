<template>
  <div class="tag-container">
    <div class="tag-group">
      <div class="tag-item" v-for="(item,index) in tagList" :class="{'active':item.time}">
        <div class="tag-title">{{item.title}}</div>
        <div class="tag-up">上节点</div>
        <div class="tag-link">中间节点</div>
        <div class="tag-down">下节点</div>
        <div class="tag-downLink"></div>
        <div class="tag-time">{{item.time}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'timeTag',
  props:{
    tagList:{}
  },
  data () {
    return {

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus">
$main-color = #04a3ee
$inactivation-color = #ddd
.tag-container
  background #fff
  box-shadow 0 0 10px $inactivation-color
  .tag-group
    display flex
    flex-wrap wrap
    justify-content space-around
    .tag-item
      width 20%
      display flex
      flex-direction column
      align-items center
      .tag-title,.tag-time
        font-size 12px
        white-space nowrap
        width 100%
        overflow hidden
        text-overflow ellipsis
      .tag-link
        font-size 0
        height 20px
        width 0
        border-left 1px dashed rgba(221, 221, 221, 0.5)
      &.active
        .tag-link,.tag-downLink:before,.tag-downLink:after
          border-color rgba(4, 163, 238, 0.5)
        .tag-up
          background $main-color
        .tag-down
          background rgba(4, 163, 238, 0.1)
          &:after
            background $main-color
      .tag-downLink
        position relative
        width 100%
        height 1px
        &:after,&:before
          content: ''
          height 1px
          position absolute
          border-top 1px dashed rgba(221, 221, 221, 0.5)
          bottom 14px
        &:before
          left 0
          right 50%
        &:after
          left 50%
          right 0
      .tag-up,.tag-down
        color transparent
        border-radius 100%
        font-size 0
      .tag-up
        margin-top 5px
        width 5px
        height 5px
        background $inactivation-color
      .tag-down
        $cell = 3px
        position relative
        top -6px
        width 15px
        height 15px
        background rgba(221, 221, 221, 0.19)
        z-index 2
        &:after
          content: ''
          position absolute
          left $cell
          right $cell
          top $cell
          bottom $cell
          background $inactivation-color
          border-radius 100%
</style>
