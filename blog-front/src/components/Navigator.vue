<template>
  <div id="navigator">
    <div id="logo">
      <img src="./../assets/logo.png" alt="网站logo，一双愤怒的眼睛" title="网站logo，一双愤怒的眼睛">
      <span>ACME</span>
    </div>

    <div id="nav" v-if="!mobile">
      <ul>
        <li v-for="item in navList" :key="item"><a href="#">{{ item }}</a></li>
      </ul>

      <div id="login-btn">登录/注册</div>
    </div>

    <div id="nav-mobile" v-if="mobile" :class="{active: btnIsActive,animation: btnIsActive}" @click="test">
      <div class="unfold-btn">
        <div class="line"></div>
        <div class="line"></div>
        <div class="line"></div>
      </div>

      <div class="nav-list" v-show="btnIsActive" :class="{}">
        <div class="nav-list-item" v-for="(item, i) in navList" :key="i">{{ item }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navigator',
  data () {
    return {
      navList: ['HTML', 'CSS', 'JavaScript', 'Vue', 'React'],
      mobile: false,
      screenWidth: document.body.clientWidth,
      btnIsActive: false
    }
  },
  created () {
    this.screenWidth = document.body.clientWidth
    this.mobile = this.screenWidth < 900
  },
  mounted () {
    const that = this
    window.addEventListener('resize', () => {
      that.screenWidth = document.body.clientWidth
      // console.log(that.screenWidth)
    })
  },
  watch: {
    // 监听窗口屏幕变化，小于900像素则显示，移动端的样式
    screenWidth: function () {
      this.mobile = this.screenWidth < 900
    }
  },
  methods: {
    test: function () {
      this.btnIsActive = !this.btnIsActive
    }
  }
}
</script>

<style lang="scss" scoped>
  #navigator {
    width: 100vw;
    height: 58px;
    background-color: #363838;
    color: white;

    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
    align-items: center;
  }

  #logo {
    display: flex;
    flex-direction: row;
    align-items: center;

    span {
      padding-left: 10px;
      font-size: 1.5rem;
      font-weight: 600;
    }
  }

  #nav {
    height: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
  }

  #login-btn {
    margin-left: 10px;
    padding: 0 10px;
    height: 18px;
    line-height: 18px;
    border-radius: 10px;
    font-size: 14px;
    background-color: #6c6d69;
  }

  ul {
    height: 100%;
    list-style: none;
  }

  li {
    padding: 0 10px;
    height: 100%;
    margin: 0 8px;
    float: left;
    line-height: 58px;
  }

  li:hover {
    background: #5c5c5c;
    transition: all .3s;
  }

  a {
    color: white;
    text-decoration: none;
  }

  a:hover {
    color: #F75000;
    transition: color .3s;
  }

  #nav-mobile {
    position: relative;
    top: 0;
    left: 0;
    width: 50px;
    height: 100%;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    .unfold-btn {
      width: 60%;
      height: 26px;
      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
      align-items: center;

      .line {
        width: 70%;
        height: 2px;
        background-color:white;
      }
    }
  }

  .nav-list {
    position: absolute;
    top: 100%;
    margin-top: 6px;
    right: 0;
    width: 120px;
    border-radius: 6px;
    background-color: #363838;
    font-size: 14px;

    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
  }

  .nav-list-item {
    margin: 10px 0px 10px 10px;
  }

  #nav-mobile:hover{
    cursor: pointer;
  }

  .active {
    transition: all .3s;
  }

  .animation {
    background-color: #5c5c5c;
    box-shadow: inset 0px 0px 4px 0px #000000;
  }
</style>
