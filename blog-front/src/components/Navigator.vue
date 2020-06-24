<template>
  <div id="navigator">
    <div id="logo">
      <img src="./../assets/logo.png" class="logo" alt="网站logo，一双愤怒的眼睛" title="网站logo，一双愤怒的眼睛">
      <span>ACME</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navigator',
  data () {
    return {
    }
  }
}
</script>

<style lang="scss" scoped>
  #navigator {
    width: 100vw;
    height: 60px;
    background-color: #363838;

    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }

  #logo {
    margin-left: 3%;

    display: flex;
    flex-direction: row;
    align-items: center;

    span {
      padding-left: 10px;
      font-size: 1.5rem;
      font-weight: 600;
      color: white;
    }
  }
</style>
