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
          <nuxt-link to="/read" class="custom-button">
            Read a story
          </nuxt-link>
        </div>
        <div class="navbar-item">
          <nuxt-link to="/write" class="custom-button">
            Write a story
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
  },
  metaInfo() {
    return {
      title: 'Stories',
      meta: [
        {
          name: 'description',
          content:
            'Stories is a simple way to send an anonymous love letter, and get paid for it'
        },
        {
          property: 'og:title',
          content: 'Stories - Its time to love more'
        },
        { property: 'og:site_name', content: 'Stories' }
      ]
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
  font-size: 45px;
  color: #ffffff;
  margin-left: 20px;
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
