<template>
  <div class="home">
    <div class="title">
        <HeadProgress per=30 />
        <h1>그 사람은 누구인가요?</h1>
    </div>
    <section class="btns">
        
    </section>
  </div>
</template>

<script>
import HeadProgress from '~/components/HeadProgress.vue'

export default {
    components: {
        HeadProgress
    },
    layout: 'futures'
}
</script>

<style lang="scss">
.home {
    .title {
        h1 {
            margin-top: 19px;
            margin-bottom: 39px;
            color: rgb(138, 137, 137);
            font-weight: 600;
            font-size: 30px;
            letter-spacing: -1.5pt;
        }
    }
    .btns {
        width: 100%;
        .btn {
            
        }
    }
}
</style>
