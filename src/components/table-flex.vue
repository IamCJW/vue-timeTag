<template>
  <div class="over-container">
    <div class="over" v-over>
      上午10点，习近平同论坛共同主席国南非总统拉马福萨及其他53个论坛非洲成员代表团团长一同步入会场。习近平宣布会议开始。
      这场三个多小时的会议中，与会各方重点就推进中非关系、深化各领域合作、构建更加紧密的中非命运共同体、共建“一带一路”以及共同关心的国际和地区问题发表了看法。
      习近平强调，两天来，北京峰会围绕“合作共赢，携手构建更加紧密的中非命运共同体”这一主题，凝聚合作共识，对接发展战略，再次唱响中非合作共赢、共同发展主旋律。
    </div>
    <button class="show">展开</button>
  </div>
</template>

<script>
  export default {
    name: "table-flex",
    directives: {
      over: {
        inserted: (el) => {
          console.log(el.innerText)
          let s = el.innerText;
          let n = el.offsetHeight;
          for (let i = 0; i < s.length; i++) {
            el.innerHTML = s.substr(0, i);
            if (n < el.scrollHeight) {
              el.style.overflow = 'hidden';
              el.innerHTML = s.substr(0, i - 6) + '...';
              let button = document.createElement('button');
              button.innerText = '展开';
              button.setAttribute('class','show');
              button.setAttribute('style','position:absolute;right:0;bottom:0');
              el.parentNode.appendChild(button);
              button.addEventListener('click',function () {
                console.log('123');
              });
              break;
            }
          }
        }
      }
    },
    mounted() {

    }
  }
</script>

<style scoped lang="stylus">
  .over-container
    position relative
  .over
    width 100%
    height 40px
    overflow hidden
    font-size 14px
  .show
    position absolute
    display block
    background #fff
    bottom 0
    right 0
</style>
