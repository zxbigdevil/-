<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
*{margin: 0;padding: 0;}
html{height: 100%;font-family: PingFangSC-Regular}
body{font-size:.28rem;height: 100%;color: #555555;background: #F5F5F5;}
div{box-sizing: border-box;}
a{text-decoration: none;color: #4A4A4A;}
#app {font-family: 'Avenir', Helvetica, Arial, sans-serif;height: 100%;}
.flex_start{display: flex; justify-content: flex-start;flex-wrap: wrap;}
.flex_center_v{display: flex; justify-content: center;}
.flex_start_v{display: flex; justify-content: flex-start; align-items: center;}
.flex_end{display: flex; justify-content: flex-end;}
.flex_end_v{display: flex; justify-content: flex-end; align-items: center;}
.flex_between{display: flex; justify-content: space-between;}
.flex_between_v{display: flex; justify-content: space-between; align-items: center;}
.flex_around{display: flex; justify-content: space-around;}
.flex_around_v{display: flex; justify-content: space-around; align-items: center;}
.flex_center{display: flex; justify-content: center; align-items: center;}
.vertical_v{display: flex; align-items: center;}
.flex_c{display: flex;flex-direction: column; align-items: center;}

/*弹窗样式*/
.van-toast--text{min-width: 4.4rem !important;font-size: .28rem !important;padding: .24rem !important;}
</style>
