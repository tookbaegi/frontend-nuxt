<template>
  <div class="complete">
        <div class="title">
            <HeadProgress per=100 />
            <h1>생성 완료!!!</h1>
        </div>
        <div class="talkaboutthis">
            <h2>지하철 투머치토커<br>조심스레<br>자리 피하기</h2>
            <p>2019.04.02. 14:20:34</p>
        </div>
        <div class="ta-btns">
            <a href="#" class="ta-btn">
                성공
            </a>
            <a href="#" class="ta-btn">
                포기
            </a>
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
.complete {
    .title {
        h1 {
            margin-top: 19px;
            margin-bottom: 19px;
            color: rgb(138, 137, 137);
            font-weight: 600;
            font-size: 30px;
            letter-spacing: -1.5pt;
        }
    }
    .ta-btns {
        display: grid;
        grid-template-columns: 50% 50%;
        justify-items: stretch;
        align-items: stretch;
        .ta-btn {
            background: rgba(229, 229, 229, 0.37);
            border-radius: 5px;
            text-align: center;
            font-size: 20px;
            color: rgb(128, 128, 128);
            padding: 19px 0;
            letter-spacing: -1px;
            margin: 5px;
        }
    }
    .talkaboutthis {
        padding: 15px;
        background: rgb(229, 229, 229);
        h2 {
            font-weight: 600;
            font-size: 30px;
            margin-bottom: 125px;
            color: rgb(138,137,137);
        }
        p {
            color: rgb(128,128,128);
            font-size: 18px;
            letter-spacing: -.9px;
        }
    }
}
</style>
