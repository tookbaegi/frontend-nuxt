<template>
    <div>
        <!--
            사이드바 테스트 페이지, 실서비스에서는 삭제 요망
            -->
        <button @click="show = !show">
            Toggle render
        </button>
        <Sidebar v-if="show" />
    </div>
</template>

<script>
import Sidebar from '~/components/Sidebar.vue'

export default {
    data() {
        return {
            show: true
        }
    },
    components: {
        Sidebar
    }
}
</script>

<style>
</style>
