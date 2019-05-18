<template>
    <div class="title-bar">
        <div class="title-bar-progress" v-bind:style="{ width: progressPer + '%' }"></div>
    </div>
</template>

<script>
export default {
    props: ['per'],
    data: function() {
        return {
            progressPer: this.per
        }
    }
}
</script>

<style lang="scss">
.title-bar {
    width: 90px;
    height: 3px;
    background: rgb(177, 177, 177);
    .title-bar-progress {
        height: 100%;
        background: #000;
    }
}
</style>
