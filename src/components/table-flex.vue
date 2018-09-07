<template>
  <div class="over-container" :style="containerStyle">
    <div class="over" :data-row="rowValue" :data-size="sizeValue" :data-height="heightValue" v-over>
      上午10点，习近平同论坛共同主席国南非总统拉马福萨及其他53个论坛非洲成员代表团团长一同步入会场。习近平宣布会议开始。
      这场三个多小时的会议中，与会各方重点就推进中非关系、深化各领域合作、构建更加紧密的中非命运共同体、共建“一带一路”以及共同关心的国际和地区问题发表了看法。
      习近平强调，两天来，北京峰会围绕“合作共赢，携手构建更加紧密的中非命运共同体”这一主题，凝聚合作共识，对接发展战略，再次唱响中非合作共赢、共同发展主旋律。
    </div>
  </div>
</template>

<script>
  export default {
    name: "table-flex",
    props: {
      row: {
        type: Number,
        default: 2
      },
      size: {
        type: Number,
        default: 14
      },
      lineHeight: {
        type: Number,
        default: 21,
      }
    },
    data() {
      return {
        rowValue: '',
        sizeValue: '',
        heightValue: '',
        containerStyle: {}
      }
    },
    created() {
      this.rowValue = this.row;
      this.sizeValue = this.size;
      this.heightValue = this.lineHeight;
      this.containerStyle = {
        'font-size': this.sizeValue + 'px',
        'line-height': this.heightValue + 'px'
      };
    },
    directives: {
      over: {
        inserted: (el) => {
          let rowValue = el.dataset.row;
          let heightValue = el.dataset.height;
          let maxText = el.innerText;
          let docHeight = rowValue * heightValue;
          el.style.height = docHeight + 'px';
          for (let i = 0; i < maxText.length; i++) {
            el.innerHTML = maxText.substr(0, i);
            if (docHeight < el.scrollHeight) {
              el.style.overflow = 'hidden';
              let minText = maxText.substr(0, i - 6) + '...';
              el.innerHTML = minText;
              let style = 'position:absolute;right:0;bottom:0;color: #04a3ee;';
              let showButton = document.createElement('span');
              showButton.innerText = '展开';
              showButton.setAttribute('class', 'show');
              showButton.setAttribute('style', style);
              let closeButton = document.createElement('span');
              closeButton.innerText = '收起';
              closeButton.setAttribute('class', 'show');
              closeButton.setAttribute('style', style);
              el.parentNode.appendChild(showButton);
              showButton.addEventListener('click', function (e) {
                el.parentNode.removeChild(showButton);
                el.innerHTML = maxText;
                el.style.height = 'auto';
                el.parentNode.appendChild(closeButton);
              });
              closeButton.addEventListener('click', function () {
                el.parentNode.removeChild(closeButton);
                el.innerHTML = minText;
                el.style.height = docHeight+'px';
                el.parentNode.appendChild(showButton);
              });
              break;
            }
          }
        }
      }
    }
  }
</script>

<style scoped lang="stylus">
  .over-container
    position relative

  .over
    width 100%
    overflow hidden
    position relative
</style>
