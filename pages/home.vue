<template>
  <div class="home">
    <div class="title">
        <HeadProgress per=30 />
        <h1>그 사람은 누구인가요?</h1>
    </div>
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
        .title-bar {
            width: 90px;
            height: 3px;
            background: rgb(177, 177, 177);
            .title-bar-progress {
                height: 100%;
                background: #000;
            }
        }
        h1 {
            margin-top: 19px;
            color: rgb(138, 137, 137);
            font-weight: 600;
            font-size: 30px;
            letter-spacing: -1.5pt;
        }
    }
}
</style>
