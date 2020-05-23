<template>
  <div>
    <div class="header red-block">
      <img
        src="../assets/main.svg"
        class="header-img"
        style="width: 100%;position: absolute"
      />
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
    <div class="container body sh">
      <span class="custom-title">
        Enjoying reading love storys ?
      </span>

      <div class="left">
        <div class="buttons">
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
  height: 55vh;
}

.custom-title {
  font-family: 'Roboto', sans-serif;
  font-weight: 700;
  color: #313131;
  font-size: 45px;
  position: absolute;
  float: left;
  margin-bottom: 20px;
}

.sub-body {
  position: relative;
  width: 100%;
  display: block;
}

.right img {
  margin-top: 50px;
  width: 400px;
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
  text-align: center;
  background: #d63447;
  bottom: 0;
}

.header .custom-button {
  float: left;
}

@media screen and (max-width: 1250px) {
  .header-img {
    display: none;
  }

  .red-block {
    background: #d63447;
    display: block;
    height: 80vh;
  }

  .header {
    padding-left: 3%;
  }

  .title {
    font-size: 2.8rem;
  }

  .subtitle {
    text-align: left;
    margin-left: 0;
    font-size: 1.3rem;
  }

  .custom-button {
    position: relative;
    display: block;
    margin-top: 50px;
    width: 240px;
    text-align: center;
  }

  .body {
    margin-top: 5%;
    width: 100%;
    margin-bottom: -100px;
  }

  .custom-title {
    width: 100%;
    font-size: 2.5rem;
    display: block;
    text-align: center;
    float: center;
    margin-top: 30px;
  }

  .sub-body {
    width: 100%;
  }

  .left {
    width: 100%;
  }

  img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 60px;
    padding-left: 5%;
  }

  .right img {
    display: none;
  }

  .custom-button {
    text-align: center;
    float: center !important;
  }

  .buttons {
    margin-top: 50px;
  }

  .bottom {
    opacity: 0;
  }
}
</style>
