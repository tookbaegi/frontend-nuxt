<template>
    <div class="wrapper">
        <nav>
            <a href="#" class="menu-icon">
                <img src="~assets/bar.svg">
            </a>
        </nav>
    
        <div class="mid">
            <div class="card" v-for="(item, index) in list" :key="index">
                <div class="cardHead">
                    <div class="title">
                        {{item.place}} {{item.person}} {{item.name}}
                    </div>

                    <img src="~assets/heart.red.svg" class="heart">
                </div>

                <div class="cardMid">
                    <div class="commentTitle">
                        댓글({{item.comments.length}})
                    </div>
                    <div class="commentItem">
                        <div class="commentContent">

                        </div>
                    </div>
                </div>

                <input v-model="item.userComment" type="text" class="commentWrite" placeholder="댓글 입력" @keyup.enter="sendComment(item)">
            </div>
        </div>

    </div>

</template>

<script>
import axios from 'axios'
export default {
    data () {
        return {
            list: [],
            heartDeault: '~assets/heart.svg',
            heartRed: '~assets/heart.red.svg',
            user: {}
        }
    },
    created () {
        this.user = JSON.parse(localStorage.getItem('user'));
        this.getData()
    },
    methods: {
        sendComment (item) {
            let body = {
                content: item.userComment,
                questId: item.id,
                userId: this.user.id                
            }
            item.userComment = ''
            axios.post('https://ttukbaegi.herokuapp.com/api/comments', body)
            .then((response) =>{
                console.log(response)
            })
        },
        getData() {
            axios.get('https://ttukbaegi.herokuapp.com/api/quests')
            .then((response) => {
                console.log(response)
                for(let item of response.data){
                    item.userComment = ''
                }
                this.list = response.data
            })
        }
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

    nav {
    margin-top: 24px;
    margin-bottom: 24px;
    height: 27.5px;
    img {
        height: 100%;
        float: right;
    }    
    }

    .mid {
        margin-top:25px;
        width: 100%;

    }
    .card {
        padding: 10px;
        background-color: rgb( 229, 229, 229);
        border-radius: 5px;
        margin-bottom: 20px;
    }

    .cardHead {
        position: relative;
        width: 100%;
        height: 175px;
        background-color: white;
        border-radius: 5px;
        padding-top: 20px;
    }

    .cardHead .title {
        font-size: 25px;
        font-weight: 500;
        width: 205px;
        margin-left: 14px;
        line-height: 33px;
    }

    .cardMid {
        width: 100%;
    }

    .commentTitle {
        color: rgb(138, 137, 137);
        height: 30px;
        line-height: 30px;
        font-size: 9px;
    }

    .commentItem {
        border-top: 1px solid rgb(138, 137, 137);
        padding-top: 11px;
    }

    .commentWrite {
        background-color: white;
        width: 100%;
        height: 35px;
        margin-top: 20px;
        border:none;
        border-radius: 5px;
        font-size: 20px;
        padding-left: 12px;
        font-size: 15px;
        padding-right: 12px;
    }
    .heart{
        width: 25px;
        height:  25px;
        position: absolute;
        top: 14px;
        right: 14px;
    }

</style>
