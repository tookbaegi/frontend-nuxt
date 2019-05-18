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
