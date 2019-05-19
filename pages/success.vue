<template>
    <div class="wrapper">
        <div>
            <img class="home" src="~assets/black_home.svg" @click="goHome">
            <div style="clear: both;"></div>
        </div>

        <div class="top">
            <div class="first">
                퀘스트 성공
            </div>
            <div class="second">
                오늘도 뚝배기를 지켜냈습니다.
            </div>
        </div>

        <div class="backImg">

        </div>
        <img src="~assets/rainbow.png" class="back">
    </div>
</template>

<script>
export default {
    methods: {
        goHome () {
            this.$router.push({'name': 'main'})
        }
    }

}
</script>

<style>
.wrapper {
    width: calc(100% - 40px);
    margin-left:auto;
    margin-right:auto;
    margin-top: 35px;
}
.home {
    width: 35px;
    height: 35px;
    float: right;
}

.top{
    margin-top: 40px;
}

.first{
    font-size: 30px;
    color:rgb(30, 30, 30);
    font-weight: 900;
}

.second {
    font-size: 20px;
    color:rgb(151, 151, 151);
}

.back {
    width: 100%;
    height: 100%;
}
</style>
