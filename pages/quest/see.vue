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
                        댓글 ({{item.comments.length}})
                    </div>
                    <div class="commentItem">
                        <template v-for="(sub, idx) in item.comments">
                            <div class="commentContent"  :key="idx" v-if="idx < 2">
                                <div class="userImage">
                                    {{ sub.user.titleName }} 
                                </div>
                                <div class="commentContainer">
                                    <div style="height: 8px;">
                                        <div class="commentUsername">{{sub.user.name}}</div>
                                        <div class="commentDay"> {{ getDate(sub.user.createdAt) }}</div>
                                    </div>
                                    <div class="commentReal">
                                        {{ sub.content }}
                                    </div>
                                </div>
                                <div style="clear: both;"></div>
                            </div>                            
                        </template>
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
        getDate ( val ){
            let date = new Date(val)
            let result = `${date.getFullYear()}.${date.getMonth()+1}.${date.getDate()}`
            return result
        },
        sendComment (item) {
            if(item.userComment !== ''){
                let body = {
                    content: item.userComment,
                    questId: item.id,
                    userId: this.user.id                
                }
                item.userComment = ''
                axios.post('https://ttukbaegi.herokuapp.com/api/comments', body)
                .then((response) => {
                    this.getData()
                })
            }
            else{
            }

        },
        getData() {
            axios.get('https://ttukbaegi.herokuapp.com/api/quests')
            .then((response) => {
                console.log(response)
                for(let item of response.data){
                    item.userComment = ''
                    for(let sub of item.comments){
                        if(sub.user.name.length > 0 ){
                            sub.user.titleName = sub.user.name.slice(0, 1)
                        }
                    }
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
        border-radius: 5px;
        margin-bottom: 20px;
        background-color: black;
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
        color: white;
    }

    .commentItem {
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
    .commentContent {
        padding-top: 13px;
        padding-bottom: 13px;
        border-top: 1px solid white;
    }
    .userImage {
        width: 25px;
        height: 25px;
        border-radius: 50%;
        background-color: rgb(93, 93, 93);
        color: white;
        text-align: center;
        line-height: 25px;
        float: left;
    }

    .commentContainer{
        float: left;
        width: calc(100% - 35px);
    }

    .commentUsername {
        font-size: 8px;
        height: 8px;
        line-height: 8px;
        float: left;
        margin-left: 8px;
        color: white;
    }

    .commentDay {
        font-size: 6px;
        height: 8px;
        line-height: 8px;
        color: rgb(179, 179, 179);
        float: left;
        margin-left: 4px;
    }

    .commentReal {
        line-height: 12px;
        margin-top: 9px;
        margin-left: 8px;
        font-size: 8px;
        color: white;
        width:  calc(100% -  33px);
    }

</style>
