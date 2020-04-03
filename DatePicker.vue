<template>
  <div class="date-picker">
    <div class="picker-input">
      <span class="input-prefix">
        <i>xx</i>
      </span>
      <input type="text" />
    </div>
    <div class="picker-panel">
      <div class="picker-arrow" />
      <div class="picker-body">
        <div class="picker-header">
          <span class="picker-btn icon-prev-year" />
          <span class="picker-btn icon-prev-month" />
          <span class="picker-date">
            2020年1月
          </span>
          <span class="picker-btn icon-next-month" />
          <span class="picker-btn icon-next-year" />
        </div>
        <div class="picker-content">
          <div class="picker-weeks">
            <div
              v-for="week in ['日', '一', '二', '三', '四', '五', '六']"
              :key="week"
            >
              {{ week }}
            </div>
          </div>
          <div class="picker-days">
            <div v-for="date in 42" :key="date">
              {{ date }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    date:{
      type:Date,
      default : ()=>{
         new Date()
      }
    }
  },
  mounted(){
    console.log(this.date)
  }
</script>

<style scoped>
@font-face {
  font-family: 'iconfont'; /* project id 1733068 */
  src: url('//at.alicdn.com/t/font_1733068_cqa3o2nt1k.eot');
  src: url('//at.alicdn.com/t/font_1733068_cqa3o2nt1k.eot?#iefix')
      format('embedded-opentype'),
    url('//at.alicdn.com/t/font_1733068_cqa3o2nt1k.woff2') format('woff2'),
    url('//at.alicdn.com/t/font_1733068_cqa3o2nt1k.woff') format('woff'),
    url('//at.alicdn.com/t/font_1733068_cqa3o2nt1k.ttf') format('truetype'),
    url('//at.alicdn.com/t/font_1733068_cqa3o2nt1k.svg#iconfont') format('svg');
}
.iconfont {
  font-family: 'iconfont';
}
.icon-date::before {
  content: '\e64b';
}
</style>
