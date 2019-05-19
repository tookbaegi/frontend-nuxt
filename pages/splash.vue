<template>
  <div class="wrapper">
    <div class="title">
      <div class="word">뚝배기</div>
      <div class="word">대신</div>
      <div class="word">퀘스트</div>
    </div>
  </div>
</template>

<script>
export default {
  created () {
    this.splash()
  },
  methods: {
    splash() {
    setTimeout(() => { 
      this.$router.push({'name': 'login'})
      }, 3000);    

    }
  }
}
</script>

<style scoped>
  body {
    background-color: rgb(34, 220, 227);
  }
  .wrapper {
    background-color: rgb(34, 220, 227);
    width: 100%;
    height: 100vh;
  }
  .title {
    width: calc(100% - 80px);
    margin-top: 110px;
    margin-left:auto;
    margin-right:auto;
    font-size:30px;
    font-weight: 500;
  }
  .word {
    font-size: 40px;
    font-weight:900;
    line-height: 55px;
    color: rgb(42, 42, 42);
  }
</style>
