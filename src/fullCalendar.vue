<template>
  <div class="comp-full-calendar">
    <!-- header pick month -->
    <fc-header :current-date.sync="currentDate" :title-format="titleFormat">

      <div slot="header-right">
        <slot name="fc-header-right">
        </slot>
      </div>
    </fc-header>
    <!-- body display date day and events -->
    <fc-body :current-date="currentDate" :events="events" :month-names="monthNames" :week-names="weekNames">
      <div slot="body-card">
        <slot name="fc-body-card">
        </slot>
      </div>
    </fc-body>
  </div>
</template>
<script type="text/babel">

  export default {
    props : {
      events : { // events will be displayed on calendar
        type : Array,
        default : []
      },
      titleFormat : {
        type : String,
        default : 'yyyy年MM月'
      },
      monthNames : {
        type : Array,
        default () {
          return ['1月','2月','3月','4月','5月','6月','7月','8月','9月','11月','12月']
        } 
      },
      weekNames : {
        type : Array,
        default () {
          return ['周一','周二','周三','周四','周五','周六','周日']
        }
      }
    },
    created () {
    },
    data () {
      return {
        currentDate : new Date()
      }
    },
    components : {
      'fc-body'   : require('./components/body'),
      'fc-header' : require('./components/header')
    }
  }
  
</script>
<style lang="scss">
  .comp-full-calendar{
    // font-family: "elvetica neue", tahoma, "hiragino sans gb";
    padding:20px;
    background: #fff;
    width: 960px;
    ul,p{
      margin:0;
      padding:0;
      font-size: 14px;
    }
  }
</style>