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
                    <span class="content" :class="{'clicked': val.flag}" @click="val.flag = !val.flag">
                        {{ val.name }}
                    </span>
                </li>
            </ul>
        </div>

        <div class="container bottom">
            <p class="title">이 사람들이 날 힘들게 해요</p>
            <ul class="list">
                <li class="list-item" v-for="(val, index) in hardList" :key="index">
                    <span class="content" :class="{'clicked': val.flag}" @click="val.flag = !val.flag">
                        {{ val.name }}
                    </span>
                </li>
            </ul>
        </div>

        <div class="submit" @click="submit">
            입력완료
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data () {
        return{
            nickname: '',
            annoyList: [
                {'name': '지하철/버스에서', 'flag': false },
                {'name': '회사에서', 'flag': false },
                {'name': '식당/거리에서', 'flag': false },
                {'name': '집에서', 'flag': false },
                {'name': '학교/학원에서', 'flag': false },
                {'name': '카페에서', 'flag': false },
            ],
            hardList: [
                {'name': '썸남썸녀', 'flag': false },
                {'name': '애인', 'flag': false },
                {'name': '오지라퍼/투머치토커', 'flag': false },
                {'name': '대중교통 노매너', 'flag': false },
                {'name': '가족', 'flag': false },
                {'name': '괴롭히는 사람', 'flag': false },
                {'name': '상사/꼰대', 'flag': false },
            ]
        }
    },
    methods: {
        submit(){
            let user = JSON.parse(localStorage.getItem('user'));
            axios.patch(`https://ttukbaegi.herokuapp.com/api/users/${user.id}`, {name: this.nickname})
            .then((response) => {
                this.getUser()
            })
        },
        getUser() {
            let user = JSON.parse(localStorage.getItem('user'));
            axios.get(`https://ttukbaegi.herokuapp.com/api/users/${user.id}`)
            .then((response) => {
                console.log(response.data)
                window.localStorage.setItem('user', JSON.stringify(response.data))
                this.$router.push({'path': 'main'})          
            })
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
        font-size: 20px;
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
        background-color: white;
        color: rgb(107, 105, 105);
        border: 1px solid rgb(107, 105, 105);
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
    .clicked {
        background-color: white;
        border: 1px solid rgb(79, 44, 250);
        color: rgb(79, 44, 250);
    }
</style>
