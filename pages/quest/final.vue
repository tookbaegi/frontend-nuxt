<template>
  <div class="home">
    <div class="title">
        <HeadProgress per=70 />
        <h1>그 사람은 누구인가요?</h1>
    </div>
    <section class="btns">
        <a href="#" class="btn" v-for="(data, i) in listData" :key="i">
            {{ data.string }}
        </a>
        <a href="#" class="btn btn-other">
            직접 입력<br>(20자 제한)
        </a>
    </section>
    <div class="com-btn-box">
        <a href="#" class="btn">
            입력완료
        </a>
    </div>
  </div>
</template>

<script>
import HeadProgress from '~/components/HeadProgress.vue'

export default {
    asyncData() {
        const listData = [
            {
                'name': 'snsn',
                'string': '썸남썸녀'
            },
            {
                'name': 'snsn',
                'string': '썸남썸녀'
            },
            {
                'name': 'snsn',
                'string': '썸남썸녀'
            },
            {
                'name': 'snsn',
                'string': '썸남썸녀'
            },
            {
                'name': 'snsn',
                'string': '썸남썸녀'
            },
            {
                'name': 'snsn',
                'string': '썸남썸녀'
            },
            {
                'name': 'snsn',
                'string': '썸남썸녀'
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
            margin-bottom: 39px;
            color: rgb(138, 137, 137);
            font-weight: 600;
            font-size: 30px;
            letter-spacing: -1.5pt;
        }
    }
}
</style>
