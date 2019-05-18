<template>
  <div class="home">
    <div class="title">
        <HeadProgress per=30 />
        <h1>그 사람은 누구인가요?</h1>
    </div>
    <section class="btns">
        <a href="#" class="btn">
            대중교통
        </a>
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
            width: 50%;
            float: left;
            font-size: 18pt;
            text-align: center;
            font-weight: 600;
            color: rgb(107, 105, 105);
            letter-spacing: -.9px;
            padding: 73px 50px;
        }
    }
}
</style>
