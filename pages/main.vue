<template>
    <div class="wrapper">
        <div class="header">
      <nav>
          <a href="#" class="menu-icon">
              <img src="~assets/bar.svg">
          </a>
      </nav>
        </div>

        <div class="top">
            <div class="nickname">
                {{ user.name }}님은
            </div>
            <div class="level">
                쇠뚝배기
            </div>
        </div>

        <div class="mid">
            <div class="card" @click="$router.push({'path': 'quest/first'})">
                <div class="contents">
                    <div class="title1">짜증나는 상황 발생!</div>
                    <div class="title2">퀘스트 만들기</div>
                </div>
            </div>

            <div class="card margin20" @click="$router.push({'path': 'quest/see'})">
                <div class="contents">
                    <div class="title1">유저들이 만든</div>
                    <div class="title2">퀘스트 보러가기</div>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    data () {
        return {
            user: {}
        }
    },
    created () {
        this.user = JSON.parse(localStorage.getItem('user'));
        console.log(this.user)
    }
}
</script>

<style lang="scss">
    .wrapper{
        width: calc(100% - 34px);
        margin-left:auto;
        margin-right:auto;
        margin-top: 35px;
    }

    .header {
        width: 100%;
        height: 27px;
    }

    .top{
        width: 100%;
        margin-top: 25px;
    }

    .nickname {
        width:auto;
        height: 20px;
        line-height: 20px;
        color: rgb(138, 137, 137);
        font-size: 20px;
    }
    
    .level {
        margin-top: 12px;
        width:auto;
        height: 20px;
        line-height: 20px;
        color: rgb(138, 137, 137);
        font-size: 30px;
    }

    .mid {
        width: 100%;
        margin-top: 38px;
    }

    .card {
        width: 100%;
        height: 183px;
        border-radius: 5px;
        background-color: rgb(229, 229, 229);
        padding-top:60px;
    }

    .margin20 {
        margin-top: 20px;
    }

    .title1 {
        text-align: center;
        color: rgb(112, 112, 112);
        font-size: 18px;
    }
    .title2 {
        text-align: center;
        color: rgba(0, 0, 0, 0.72);
        font-size: 36px;
        margin-top:14px;
    }
    nav {
    margin-top: 24px;
    margin-bottom: 24px;
    height: 27.5px;
    img {
        height: 100%;
        float: right;
    }
}
</style>
