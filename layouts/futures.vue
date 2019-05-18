<template>
  <div style="padding: 20px;">
      <nav>
          <a href="#" class="menu-icon">
              <img src="~assets/bar.svg">
          </a>
      </nav>
    <nuxt />
  </div>
</template>

<style lang="scss">
*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}
body {
  font-family: 'Spoqa Han Sans', sans-serif;
}
nav {
    margin-top: 24px;
    margin-bottom: 24px;
    height: 27.5px;
    img {
        height: 100%;
        float: right;
    }
}
</style>
