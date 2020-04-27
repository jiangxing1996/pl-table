<template>
  <div id="app">
    <!--<Header></Header>-->
    <!--<router-view></router-view>-->
    <text-demo/>
  </div>
</template>

<script>
  import Header from './components/Header'
  import textDemo from './testFile/index'
  export default {
    name: 'app',
    components: {
      textDemo,
      Header,
    },
  }
</script>

<style lang="scss">
  body {
    margin: 0;
    padding: 0;
  }

  * {
    box-sizing: border-box;
    font-family: helvetica neue, Helvetica, Arial, sans-serif;;
  }

  #app {
    width: 100%;
    height: 100vh;
    overflow-x: hidden;
    scroll-behavior: smooth;
    &::-webkit-scrollbar{
      display: none;
    }
    -ms-overflow-style: none;
    scrollbar-width: none;
    overflow: -moz-scrollbars-none;
  }
</style>
