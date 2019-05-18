<template>
    <div class="wrapper">
        <div class="top">
            <p class="title">닉네임</p>
            <input class="input" type="text" v-model="nickname">
        </div>

        <div class="container mid">
            <p class="title">이 장소에서 짜증나고</p>
            <ul class="list">
                <li class="list-item" v-for="(val, index) in annoyList" :key="index">
                    <span class="content">
                        {{ val }}
                    </span>
                </li>
            </ul>
        </div>

        <div class="container bottom">
            <p class="title">이 사람들이 날 힘들게 해요</p>
            <ul class="list">
                <li class="list-item" v-for="(val, index) in hardList" :key="index">
                    <span class="content">
                        {{ val }}
                    </span>
                </li>
            </ul>
        </div>

        <div class="submit">
            입력완료
        </div>
    </div>
</template>

<script>
export default {
    data () {
        return{
            nickname: '',
            annoyList: [
                '지하철/버스에서',
                '회사에서',
                '식당/거리에서',
                '집에서',
                '학교/학원에서',
                '카페에서',
            ],
            hardList: [
                '썸남썸녀',
                '애인',
                '오지라퍼/투머치토커',
                '대중교통 노매너',
                '가족',
                '괴롭히는 사람',
                '상사/꼰대'
            ]
        }
    }
}
</script>

<style>
    .wrapper{
        width: calc(100% - 34px);
        margin-left:auto;
        margin-right:auto;
        margin-top:118px;
        margin-bottom: 46px;
    }
    .title {
        font-size: 27px;
        color: rgb(107, 105, 105);
    }
    .input {
        background-color: rgb(229, 229, 229);
        width: 100%;
        height: 61px;
        margin-top: 20px;
        border:none;
        border-radius: 5px;
    }
    .list {
        width: 100%;
        margin-top: 17px;
    }
    .list-item{
        list-style: none;
        margin-bottom: 9px;
    }
    .content {
        border-radius: 5px;
        display: inline-block;
        width: auto;
        height: 57px;
        padding-left: 17px;
        padding-right: 42px;
        line-height: 57px;
        color: rgb(107, 105, 105);
        background-color: rgb(229, 229, 229);
    }
    .mid {
        margin-top: 93px;
    }
    .bottom {
        margin-top: 76px;
    }
    .submit {
        margin-top: 97px;
        height: 56px;
        line-height: 56px;
        color: rgb(107, 105, 105);
        width: 100%;
        background-color: rgba(229, 229, 229, 0.32);
        border-radius: 5px;
        text-align: center;
    }
</style>
