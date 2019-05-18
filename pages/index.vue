<template>
  <div class="title">
    뚝배기대신퀘스트
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

<style>
  .title {
    width: calc(100% - 80px);
    margin-left:auto;
    margin-right:auto;
    text-align:center;
    margin-top:280px;
    font-size:30px;
    font-weight: 500;
  }
</style>
