<template>
  <div class="complete">
        <div class="title">
            <HeadProgress per=100 />
            <h1>퀘스트 수행</h1>
        </div>
        <div class="talkaboutthis">
            <h2>{{place}} 에서<br>{{person}} 에게<br>{{ name }}</h2>
            <p>{{ getDate() }} </p>
        </div>
        <div class="ta-btns">
            <a href="#" class="ta-btn success" @click="success">
                성공
            </a>
            <a href="#" class="ta-btn fail" @click="fail">
                포기
            </a>
        </div>
  </div>
</template>

<script>
import HeadProgress from '~/components/HeadProgress.vue'
import { POINT_CONVERSION_COMPRESSED } from 'constants';

export default {
    data () {
        return {
            person: '',
            place: '',
            name: ''
        }
    },
    created () {
        this.person = localStorage.getItem('person')
        this.place = localStorage.getItem('place')     
        this.name = localStorage.getItem('name')     
    },
    methods: {
        getDate() {
            let date = new Date()
            let result = ''
            result = `${date.getFullYear()}.${date.getMonth()+1}.${date.getDate()}  ${date.getHours()}:${date.getMinutes()}:${date.getSeconds()}`
            return result
        },
        success () {
            this.$router.push({'name': 'success'})
        }
        ,
        fail () {
            this.$router.push({'name': 'fail'})
        },        
    },
    components: {
        HeadProgress
    },
    layout: 'futures'
}
</script>

<style lang="scss" scoped>
#__layout{
background: rgb(34, 220, 227);

.complete {
    .title {
        h1 {
            margin-top: 14px;
            margin-bottom: 19px;
            color: rgb(30, 30, 30);
            font-weight: 600;
            font-size: 30px;
            letter-spacing: -1.5pt;
        }
    }
    .ta-btns {
        display: grid;
        grid-template-columns: 50% 50%;
        justify-items: stretch;
        align-items: stretch;
        margin-top:14px;
        .ta-btn {
            background: rgba(229, 229, 229, 0.37);
            border-radius: 5px;
            text-align: center;
            font-size: 20px;
            color: rgb(128, 128, 128);
            padding: 19px 0;
            letter-spacing: -1px;
            margin: 5px;
        }
        .success {
            background-color: black;
            color:white;
        }
        .fail{
            background-color: rgb(226, 231, 231);
            color: rgb(30, 30, 30);
        }
    }
    .talkaboutthis {
        padding: 15px;
        background: rgb(229, 229, 229);
        h2 {
            font-weight: 600;
            font-size: 30px;
            margin-bottom: 125px;
            color: rgb(30, 30, 30);
        }
        p {
            color: rgb(128,128,128);
            font-size: 18px;
            letter-spacing: -.9px;
        }
    }
}
}

</style>
