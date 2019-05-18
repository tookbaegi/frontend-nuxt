<template>
  <div class="home">
    <div class="title">
        <HeadProgress per=90 />
        <h1>퀘스트명 입력</h1>
    </div>
    <div class="textarea-box">
        <h3>대중교통 - 투머치토커</h3>
        <textarea rows=4 placeholder="필수입력 (최대 30자)"></textarea>
        <div class="ta-btns">
            <a href="#" class="ta-btn">
                이전으로
            </a>
            <a href="#" class="ta-btn">
                완료하기
            </a>
        </div>
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
        h1 {
            margin-top: 19px;
            margin-bottom: 19px;
            color: rgb(138, 137, 137);
            font-weight: 600;
            font-size: 30px;
            letter-spacing: -1.5pt;
        }
    }
    .textarea-box {
        h3 {
            font-size: 15px;
            font-weight: 400;
            letter-spacing: -0.75px;
            color: rgb(128, 128, 128);
        }
        textarea {
            margin-top: 10px;
            font-family: 'Spoqa Han Sans', sans-serif;
            border: 0;
            border-radius: 5px;
            background: rgb(229, 229, 229);
            padding: 20px;
            font-size: 20px;
            letter-spacing: -1px;
            color: rgb(194, 194, 194);
            width: 100%;
            height: 172px;
        }
        .ta-btns {
            display: grid;
            grid-template-columns: 50% 50%;
            justify-items: stretch;
            align-items: stretch;
            .ta-btn {
                background: rgb(229, 229, 229);
                text-align: center;
                font-size: 20px;
                color: rgb(128, 128, 128);
                padding: 19px 0;
                letter-spacing: -1px;
            }
            margin-bottom: 80px;
        }
        
    }
}
</style>
