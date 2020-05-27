<template>
  <nav
    class="navbar"
    role="navigation"
    aria-label="main navigation"
    style="background: #D63447 "
  >
    <div class="navbar-brand">
      <nuxt-link class="custom-title" to="/">
        Stories
      </nuxt-link>

      <a
        role="button"
        class="navbar-burger burger"
        :class="{ 'is-active': isActive }"
        aria-label="menu"
        aria-expanded="false"
        data-target="navbarBasicExample"
        @click="isActive = !isActive"
      >
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div id="navbarBasicExample" class="navbar-menu">
      <div class="navbar-end">
        <div class="navbar-item">
          <nuxt-link to="/write" class="custom-button">
            Write a story
          </nuxt-link>
        </div>
        <div class="navbar-item">
          <nuxt-link to="/" class="custom-button">
            Home
          </nuxt-link>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isActive: false
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Reenie+Beanie&display=swap');

.navbar-burger {
  color: #ffffff !important;
}

.custom-title {
  font-family: 'Reenie Beanie', cursive;
  font-size: 30px;
  vertical-align: middle;
  color: #ffffff;
  margin-left: 20px;
  margin-top: 5px;
}

.custom-title:hover {
  color: #ffffff;
}

.custom-button {
  font-family: 'Reenie Beanie', cursive;
  font-size: 25px;
  color: #ffffff;
}

.custom-button:hover {
  text-decoration: underline;
}
</style>
