<template>
  <div id="app">
    <sliderNav :call-back="changeDo" :nav-list="navList"/>
    <tableFlex/>
    <tableFlex :row="3" :size="10"/>
  </div>
</template>

<script>
  import timeTag from './components/timeTag'
  import sliderNav from './components/slider-nav'
  import tableFlex from './components/table-flex'
  export default {
    name: 'App',
    components: {
      timeTag,sliderNav,tableFlex
    },
    data(){
      return{
        navList:['最新音乐','我的最爱','系统消息'],
        tagList:[{
          title:'发布招标日期',
          time:'17/11/08'
        },{
          title:'招标日期',
          time:'17/11/08'
        },{
          title:'发布日期',
          time:'17/11/08'
        },{
          title:'发标日期',
          time:''
        },{
          title:'布招日期',
          time:''
        }]
      }
    },
    methods:{
      changeDo(index){
        console.log(index)
      }
    }
  }
</script>

<style>
  html, body {
    margin: 0;
    padding: 0;
  }
</style>
