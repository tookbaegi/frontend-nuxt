<template>
  <div class="final">
    <div class="title">
        <HeadProgress per=90 />
        <h1>퀘스트명 입력</h1>
    </div>
    <div class="textarea-box">
        <h3>{{ place }} - {{ person }} </h3>
        <textarea rows=4 placeholder="필수입력 (최대 30자)" v-model="message"></textarea>
        <div class="ta-btns">
            <a href="#" class="ta-btn" @click="prev">
                이전으로
            </a>
            <a href="#" class="ta-btn" @click="next">
                완료하기
            </a>
        </div>
        <div class="title">
            <h1>다른 유저의<br>완료된 퀘스트</h1>
        </div>
        <section class="btns">
            <a href="#" class="btn" v-for="(data, i) in listData" :key="i">
                {{ data.string }}
            </a>
        </section>
        <div class="com-btn-box">
            <a href="#" class="btn">
                더 보기
            </a>
        </div>
    </div>
  </div>
</template>

<script>
import HeadProgress from '~/components/HeadProgress.vue'
import axios from 'axios'

export default {
    created () {
        this.user = JSON.parse(localStorage.getItem('user'));   
        this.person = localStorage.getItem('person')
        this.place = localStorage.getItem('place')     
    },
    methods: {
        prev () {
            this.$router.push({'path': 'second'})
        },
        next () {
            window.localStorage.setItem('name', this.message);
            let body = {
                "userId": this.user.id,
                "person": this.person,
                "place": this.place,
                "name": this.message,
            } 
            axios.post('https://ttukbaegi.herokuapp.com/api/quests', body)
            .then((response) => {
                console.log(response)
                this.$router.push({'path': 'complete'})
            })
        }
    },
    data () {
        return {
            message: '',
            user: {},
            person: '',
            place: ''
        }
    },
    asyncData() {
        const listData = [
            {
                'name': 'snsn',
                'string': '회식자리에서 부장님 모르게 신속히 9시에 빠져나가기'
            },
            {
                'name': 'snsn',
                'string': '대중교통 투머치토커 인내하기'
            },
            {
                'name': 'snsn',
                'string': '썸남썸녀'
            },
            {
                'name': 'snsn',
                'string': '아 졸려'
            }
        ]
        return { listData }
    },
    components: {
        HeadProgress
    },
    layout: 'futures'
}
</script>

<style lang="scss">
.final {
    .title {
        h1 {
            margin-top: 19px;
            margin-bottom: 19px;
            color: rgb(30, 30, 30);
            font-weight: 600;
            font-size: 30px;
            letter-spacing: -1.5pt;
        }
    }
    .textarea-box {
        h3 {
            font-size: 15px;
            font-weight: 400;
            letter-spacing: -0.75px;
            color: rgb(30, 30, 30);
        }
        textarea {
            margin-top: 10px;
            font-family: 'Spoqa Han Sans', sans-serif;
            border: 0;
            border-radius: 5px;
            background: rgb(229, 229, 229);
            padding: 20px;
            font-size: 20px;
            letter-spacing: -1px;
            width: 100%;
            height: 172px;
        }
        .ta-btns {
            display: grid;
            grid-template-columns: 50% 50%;
            justify-items: stretch;
            align-items: stretch;
            .ta-btn {
                background: rgb(30, 30, 30);
                border-radius: 5px;
                text-align: center;
                font-size: 20px;
                color: white;
                padding: 19px 0;
                letter-spacing: -1px;
                margin: 5px;
            }
            margin-bottom: 80px;
        }
        
    }
    .btns {
        width: 100%;
        margin-bottom: 20px;
        display: grid;
        grid-template-columns: 100%;
        justify-items: stretch;
        align-items: stretch;
        .btn {
            font-size: 15pt;
            font-weight: 400;
            color: rgb(107, 105, 105);
            letter-spacing: -.9px;
            padding: 20px;
            border-bottom: 2px solid rgb(247,247,247);
        }
        .btn:last-child {
            border: 0;
        }
        .btn-other {
            background: rgb(243, 237, 237);
        }
    }
    .com-btn-box {
        .btn {
            display: block;
            background: rgba(229,229,229, 0.4);
            width: 100%;
            text-align: center;
            padding: 20px 0;
        }
    }
}
</style>
