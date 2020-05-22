<template>
  <div>
    <div class="header">
      <img src="../assets/main.svg" style="width: 100%;position: absolute" />
      <div class="container">
        <h1 class="title">
          Send an anonymous love letter <br />
          and share it !
        </h1>
        <h2 class="subtitle">
          - Free message sending service<br />- No login require <br />- You get
          paid on each story view<br />- Free and premium content
        </h2>
        <nuxt-link to="/write" class="custom-button">
          Let me write my story
        </nuxt-link>
      </div>
    </div>
    <div class="container body">
      <span class="custom-title">
        How to get started
      </span>
      <div class="sub-body">
        <div class="left">
          <img src="../assets/get_started_1.svg" />
        </div>
        <div class="right">
          <img src="../assets/get_started_2.svg" />
        </div>
      </div>
    </div>
    <div class="container body">
      <span class="custom-title">
        Enjoying reading <br />
        love storys ?
      </span>

      <div class="left">
        <div style="margin-top: 35px; margin-bottom: 25px;">
          <nuxt-link to="/write" class="custom-button">
            Let me write my story
          </nuxt-link>
        </div>
        <div>
          <nuxt-link to="/read" class="custom-button">
            Let me read a story
          </nuxt-link>
        </div>
      </div>
      <div class="right">
        <img src="../assets/enjoy.svg" />
      </div>
      <div class="sub-body"></div>
    </div>
    <div class="bottom">
      <span class="bottom-title">Stories 2020</span>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=The+Girl+Next+Door&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');

* {
  user-select: none;
}

.title {
  font-family: 'The Girl Next Door', cursive;
  position: relative;
  font-weight: 100;
  font-size: 60px;
  color: #ffffff;
  padding-top: 50px;
}

.bottom-title {
  position: relative;
  font-family: 'The Girl Next Door', cursive;
  margin: auto;
  color: #ffffff;
  bottom: 0;
}

.subtitle {
  position: relative;
  font-family: 'Roboto', sans-serif;
  font-weight: 300;
  font-size: 22px;
  margin-left: 20px;
  padding-top: 40px;
  color: #f7f7f7;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.custom-button {
  margin: 0 auto;
  user-select: none;
  outline: none;
  position: relative;
  border: 0;
  background: #292929;
  color: #ffffff;
  font-family: 'Thasadith', sans-serif;
  font-size: 20px;
  border-radius: 10px;
  padding-top: 5vh;
  padding-bottom: 10vh;
  padding: 10px 20px 10px 20px;
}

.custom-button:hover {
  background: #151515;
}

.header {
  position: relative;
  height: 90vh;
}

.body {
  position: relative;
  height: 70vh;
}

.custom-title {
  font-family: 'Roboto', sans-serif;
  font-weight: 700;
  color: #313131;
  font-size: 45px;
}

.sub-body {
  position: relative;
  width: 100%;
  display: block;
}

.left {
  float: left;
  margin-top: 10vh;
}

.right {
  float: right;
}

.bottom {
  position: relative;
  line-height: 3vh;
  height: 3.5vh;
  text-align: center;
  background: #d63447;
  bottom: 0;
}
</style>
