<template>
    <div>
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
