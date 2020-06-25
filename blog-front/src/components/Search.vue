<template>
  <div id="container">
    <div id="header-lv-1">ACME</div>
    <div id="header-lv-2">Your blog respository.</div>
    <div id="search-box">
      <el-input @focus="inputFocus" @blur="inputBlur" style="width: 300px" placeholder="搜索文章/用户" v-model="input3" class="input-with-select" size="small">
        <el-button slot="append" icon="el-icon-search"></el-button>
      </el-input>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Search',
  data () {
    return {
      input3: ''
    }
  },
  methods: {
    inputFocus: function () {
      this.$emit('my-focus')
    },
    inputBlur: function () {
      this.$emit('my-blur')
    }
  }
}

</script>

<style lang="scss" scoped>
  #container {
    position: absolute;
    top: 0;
    width: 100vw;
    height: 100vh;
    color: white;

    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    div {
      margin-bottom: 40px;
    }
  }

  #header-lv-1 {
    font-size: 30px;
  }

  .el-select .el-input {
    width: 130px;
  }

  .input-with-select .el-input-group__prepend {
    background-color: #fff;
  }
</style>
