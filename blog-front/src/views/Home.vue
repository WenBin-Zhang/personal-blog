<template>
  <div class="home">
    <img class="bg-img" :class="{searchfocus: isBlur, searchblur: !isBlur}" src="./../assets/page-bg.jpg" alt="网页背景图片">
    <Search @my-focus="blurImage" @my-blur="noBlurImage"></Search>
    <div id="page-down">
      <span class="iconfont icon-arrow-down" style="font-size: 30px;"></span>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Search from './../components/Search.vue'
export default {
  name: 'Home',
  data () {
    return {
      isBlur: false
    }
  },
  methods: {
    blurImage: function () {
      this.isBlur = true
    },
    noBlurImage: function () {
      this.isBlur = false
    }
  },
  components: {
    Search
  }
}
</script>

<style lang="scss">
  .home {
    width: 100%;
    height: 100vh;
  }

  .bg-img{
    width: 100vw;
    height: 100vh;
  }

  .searchfocus {
    filter: blur(3px);
    -webkit-filter: blur(3px);
    transition: all 1s;
  }

  .searchblur {
    filter: blur(0px);
    -webkit-filter: blur(0px);
    transition: all 1s;
  }

  #page-down {
    position: absolute;
    bottom: 100px;
    transform: translateX(50vw) translateX(-50%);
    // background-color: black;
    width: 50px;
    height: 50px;
    color: white;
    animation: mymove 2s ease-in-out infinite;

    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }

  #page-down:hover {
    cursor: pointer;
  }

  @keyframes mymove {
    0% {bottom: 100px;}
    50% {bottom: 150px;}
    100% {bottom: 100px;}
  }
</style>
