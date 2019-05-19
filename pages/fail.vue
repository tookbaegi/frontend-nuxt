<template>
    <div class="wrapper">
        <div>
            <img class="home" src="~assets/black_home.svg" @click="goHome">
            <div style="clear: both;"></div>
        </div>

        <div class="top">
            <div class="first">
                퀘스트 포기
            </div>
            <div class="second">
                내 뚝배기... 안녕...
            </div>
        </div>

        <div class="backImg">

        </div>
        <img src="~assets/crying.png" class="back">
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
