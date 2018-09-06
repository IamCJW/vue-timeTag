<template>
  <div id="app">
    <timeTag :tag-list="tagList"/>
  </div>
</template>

<script>
  import timeTag from './components/timeTag'

  export default {
    name: 'App',
    components: {
      timeTag
    },
    data(){
      return{
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
    }
  }
</script>

<style>
  html, body {
    margin: 0;
    padding: 0;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
