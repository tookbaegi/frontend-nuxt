<template>
  <div class="home">
    <div class="title">
        <HeadProgress per=70 />
        <h1>그 사람은 누구인가요?</h1>
    </div>
    <section class="btns">
        <a class="btn" v-for="(data, i) in listData" :key="i" :class="{'clicked': data.flag}" @click="clickData(data)">
            {{ data.string }}
        </a>
        <a class="btn btn-other">
            직접 입력<br>(20자 제한)
        </a>
    </section>
    <div class="com-btn-box">
        <a class="btn" style="margin-right: 9px;" @click="prev">
            이전으로
        </a>
        <a class="btn" @click="next">
            다음으로
        </a>
        <div style="clear:both;"></div>
    </div>
  </div>
</template>

<script>
import HeadProgress from '~/components/HeadProgress.vue'

export default {
    methods: {
        clickData ( data ) {
            for(let item of this.listData){
                item.flag = false
            }
            data.flag = true;
            window.localStorage.setItem('person', data.string);
        },
        prev () {
            this.$router.push({'name': 'first'});
        },
        next () {
            this.$router.push({'path': 'final'});
        }
    },
    asyncData() {
        const listData = [
            {
                'name': 'snsn',
                'string': '썸남썸녀',
                'flag': false
            },
            {
                'name': 'snsn',
                'string': '애인',
                'flag': false
            },
            {
                'name': 'snsn',
                'string': '오지라퍼',
                'flag': false
            },
            {
                'name': 'snsn',
                'string': '투머치토커',
                'flag': false
            },
            {
                'name': 'snsn',
                'string': '대중교통비매너',
                'flag': false
            },
            {
                'name': 'snsn',
                'string': '괴롭히는 사람',
                'flag': false
            },
            {
                'name': 'snsn',
                'string': '꼰대',
                'flag': false
            },
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
.home {
    .title {
        h1 {
            margin-top: 19px;
            margin-bottom: 29px;
            color: rgb(30, 30, 30);
            font-weight: 600;
            font-size: 30px;
            letter-spacing: -1.5pt;
        }
    }
    .btns {
        width: 100%;
        margin-bottom: 20px;
        display: grid;
        grid-template-columns: 50% 50%;
        justify-items: stretch;
        align-items: stretch;
        .btn {
            font-size: 18px;
            font-weight: 400;
            display: flex;
            color: rgb(30, 30, 30);
            letter-spacing: -.9px;
            background: rgb(229, 229, 229);
            height: 170px;
            margin: 5px;
            padding: 20px;
            border-radius: 5px;
        }
        .clicked {
            background: rgb( 34, 220, 227);
        }        
        .btn-other {
            background: rgb(243, 237, 237);
        }
    }
    .com-btn-box {
        margin-bottom: 76px;
        .btn {
            display: block;
            background: rgb(30, 30, 30);
            color: white;
            width: calc((100% - 12px)/2);
            float:left;
            text-align: center;
            padding: 20px 0;
            border-radius: 5px;
            font-size: 20px;
        }
    }
}
</style>
