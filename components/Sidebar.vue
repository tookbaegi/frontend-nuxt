<template>
    <aside class="__sidebar">
        <section class="user-profile">
            <div class="user-img-circle">
                <span class="user-img-circle-text">텍</span>
            </div>
            <div class="user-data">
                <div class="name">
                    닉네임
                </div>
            </div>
            <div class="icons" style="display: block">
               <img src="~assets/settings.svg" style="width: 20px;height: 20px;margin-left: 5px;" />
            </div>
        </section>
        <section class="quest-do">
            <h1 style="font-size: 20px;letter-spacing:-1px;">진행중인 퀘스트 <a href="#" class="badge">더보기</a></h1>
            <div class="boxs">
                <div class="box">
                    <h2>으악 이렇게 된 이상 9시 30분까지는 도착한다</h2>
                    <p>시작일 : 2019.03.24</p>
                </div>
                
            </div>
        </section>
        <section class="quest-do">
            <h1 style="font-size: 20px;letter-spacing:-1px;font-weight: 400">최근 완료한 퀘스트</h1>
            <div class="boxs">
                <div class="box">
                    <h2>으악 이렇게 된 이상 9시 30분까지는 도착한다</h2>
                    <p>시작일 : 2019.03.24</p>
                </div>
                
            </div>
        </section>
    </aside>
</template>

<script>
export default {
    transition: 'fade'
}
</script>


<style lang="scss">
.__sidebar {
    display: block;
    position: fixed;
    width: 295px;
    top: 0;
    right: 0;
    height: 100vh;
    background: rgb(162, 161, 161);

    padding: 20px;
    .user-profile {
        display: flex;
        align-items: center;
        margin-bottom: 10px;
        .user-img-circle {
            margin: 10px 0;
            background: rgb(229, 229, 229);
            display: flex;
            justify-content: center;
            align-items: center;
            width: 60px;
            height: 60px;
            border-radius: 100%;
            .user-img-circle-text {
                color: rgb(162, 161, 161);
                font-size: 25px;
                letter-spacing: -1.25px;
                font-weight: 700;
                text-align: center;
            }
        }
        .name {
            margin-left: 10px;
            font-size: 15px;
            letter-spacing: -.75px;
            color: rgb(254,254,254);
            border-bottom: 0.5px solid #fff;
            padding-bottom: 5px;
        }
    }
}
.quest-do {
    h1 {
        color: rgb(254,254,254);
    }
    .badge {
        font-weight: 400;
        float: right;
        margin-top: 5.5px;
        font-size: 9px;
        letter-spacing: -.45px;
        padding: 4px 6.6px;
        border-radius: 5px;
        color: rgb(254,254,254);
        background: rgba(229,229,229, 0.3);
    }
    .boxs {
        .box {
            background: rgb(229, 229, 229);
            padding: 15px;
            margin: 8px 0;
            border-radius: 5px;
            h2 {
                color: rgb(162, 161, 161);
                font-size: 15px;
                letter-spacing: -.75px;
                margin-bottom: 21px;
            }
            p {
                color: rgb(162, 161, 161);
                font-size: 12px;
                letter-spacing: -.6px;
            }
        }
    }
}
/* Animation */
.fade-enter-active, .fade-leave-active {
  transition: opacity .10s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
