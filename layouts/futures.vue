<template>
  <div style="padding: 20px;" v-bind:class="{ sidebaropen: sideShow }">
      <nav>
          <a href="#" class="menu-icon" @click="sideShow = !sideShow">
              <img src="~assets/bar.svg">
          </a>
      </nav>
    <nuxt />
    <Sidebar v-if="sideShow" />
  </div>
</template>

<script>
import Sidebar from '~/components/Sidebar.vue'

export default {
  data() {
    return {
      sideShow: false
    }
  },
  components: {
    Sidebar
  }
}
</script>

<style lang="scss">
nav {
    margin-top: 24px;
    margin-bottom: 24px;
    height: 27.5px;
    img {
        height: 100%;
        float: right;
    }
}
.sidebaropen {
    margin-right: 295px;
    margin-left: -295px;
}
</style>
