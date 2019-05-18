<template>
    <div class="wrapper">
        <div class="header">
      <nav>
          <a href="#" class="menu-icon">
              <img src="~assets/black_hamburger.svg">
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
            <div class="card first" @click="$router.push({'path': 'quest/first'})">
                <div class="contents">
                    <div class="title1">짜증나는 상황 발생!</div>
                    <div class="title2">퀘스트 만들기</div>
                </div>
            </div>

            <div class="card margin20 second" @click="$router.push({'path': 'quest/see'})">
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

<style lang="scss" scoped>
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
        color: rgb(30, 30, 30);
        font-size: 20px;
    }
    
    .level {
        margin-top: 12px;
        width:auto;
        height: 20px;
        line-height: 20px;
        color: rgb(30, 30, 30);
        font-size: 30px;
        font-weight: 500;
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
        padding-top:50px;
    }
    .first {
        background-color: rgb(34, 220, 227);
        .title1 {
            text-align: center;
            color: rgb(30, 30, 30);
            font-size: 18px;
        }
        .title2 {
            text-align: center;
            color: rgba(0, 0, 0, 0.72);
            font-size: 36px;
            font-weight: 900;
        }        
    }
    .second {
        background-color: rgb(30, 30, 30);
        .title1 {
            text-align: center;
            color: rgb(189, 189, 189);
            font-size: 18px;
        }        
        .title2 {
            text-align: center;
            color: rgba(255, 255, 255, 0.72);
            font-size: 36px;
            font-weight: 900;
        }        
    }
    .margin20 {
        margin-top: 20px;
    }



    nav {
    margin-top: 24px;
    margin-bottom: 24px;
    height: 80px;
    img {
        height: 100%;
        float: right;
    }
    .second .contents .title1 {
        color: rgb(189, 189, 189)
    }
}
</style>
