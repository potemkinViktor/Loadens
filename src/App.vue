<template>

  <div id="app">
    <img src="./assets/назад.svg" alt="" class="back" v-if="showBack || showLogos"
      @click="showDiscover = false; showBack = false; showLogos = false">


    <div class="buttons">
      <img v-if="!showDiscover && !showLogos" class="logo" src="./assets/loadens.svg" alt="">
      <img class="classik" @click="showLogos = true" v-if="!showDiscover && !showLogos" src="./assets/for creators.svg"
        alt="">
      <img class="classik" @click="showLogos = true" v-if="!showDiscover && !showLogos" src="./assets/launches.svg"
        alt="">


      <img class="connect" style="cursor:pointer" @click="showLogos = true" v-if="!showDiscover && !showLogos"
        src="./assets/connect (1).svg" alt="">
    </div>
    <div style="display: flex" class="content_main">
      <div class="animation_wrapper">
        <img v-if="!showLogos" src="./assets/animation.gif" alt="" class="gif">
        <img v-if="showDiscover" class="mint" :src="count()" alt="" :disabled="!mint">
      </div>
      <div style="margin: 0 5%" class="image_main">
        <img class="textsvg" v-if="!showDiscover && !showLogos" src="./assets/текст.svg" />
        <img class="bigbtn" v-if="!showDiscover && !showLogos" @click="showDiscover = true; showBack = true"
          src="./assets/discover.svg" alt="">
      </div>

      <div v-if="showDiscover" class="discover">
        <div class="disc-inner">
          <div class="timer-wrapper">
            <div class="times">
              <div v-if="!mint" id="timer"></div>
              <div class="timer">
                <img src="./assets/days.svg" alt="days">
                <img src="./assets/hours.svg" alt="days">
                <img src="./assets/minutes.svg" alt="days">
                <img src="./assets/seconds.svg" alt="days">
              </div>
            </div>
            <div class="timer-btn">
              <img src="./assets/public.svg" alt="public">
            </div>
          </div>
          <div class="timer-wrapper">
            <div class="times">
              <div v-if="!mint" id="timer2"></div>
              <div class="timer">
                <img src="./assets/days.svg" alt="days">
                <img src="./assets/hours.svg" alt="days">
                <img src="./assets/minutes.svg" alt="days">
                <img src="./assets/seconds.svg" alt="days">
              </div>
            </div>
            <div class="timer-btn">
              <img src="./assets/whitelist.svg" alt="public">
            </div>
          </div>
        </div>
      </div>
    </div>


    <div v-if="showLogos" class="logos">
      <img class="soon" src="./assets/soon.svg" alt="">
    </div>

    <div v-if="!showLogos" class="side">
      <a href="https://twitter.com/Loadens"> <img src="./assets/twitter.svg" alt=""></a>

      <img src="./assets/etherscan.svg" alt="">
      <img src="./assets/opensea.svg" alt="">

    </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      mint: false,
      showLogos: false,
      showDiscover: false,
      showGif: false,
      showBack: false,
    }
  },
  methods: {
    count() {
      if (this.mint) {
        return 'mint.svg'
      }
      else {
        return 'mint-grey.svg'
      }
    }
  }
  ,
  mounted() {
    let that = this

    function updateTimer() {
      if (that.showDiscover) {
        let future = Date.parse("feb 14, 2023 20:12:00");
        let now = new Date();
        let diff = future - now;

        let days = Math.floor(diff / (1000 * 60 * 60 * 24));
        let hours = Math.floor(diff / (1000 * 60 * 60));
        let mins = Math.floor(diff / (1000 * 60));
        let secs = Math.floor(diff / 1000);

        let d = days;
        let h = hours - days * 24;
        let m = mins - hours * 60;
        let s = secs - mins * 60;
        // console.log(that.mint)
        if (d == 0 && h == 0 && m == 0 && s == 0) {
          d = 0
          h = 0
          m = 0
          s = 0
          that.mint = true
        }
        document.getElementById("timer")
          .innerHTML =
          '<div>' + d + '</div>' +
          '<div>' + h + '</div>' +
          '<div>' + m + '</div>' +
          '<div>' + s + '</div>';

      }

    }

    function updateTimer2() {
      if (that.showDiscover) {
        let future = Date.parse("feb 15, 2023 10:12:00");
        let now = new Date();
        let diff = future - now;

        let days = Math.floor(diff / (1000 * 60 * 60 * 24));
        let hours = Math.floor(diff / (1000 * 60 * 60));
        let mins = Math.floor(diff / (1000 * 60));
        let secs = Math.floor(diff / 1000);

        let d = days;
        let h = hours - days * 24;
        let m = mins - hours * 60;
        let s = secs - mins * 60;
        // console.log(that.mint)
        if (d == 0 && h == 0 && m == 0 && s == 0) {
          d = 0
          h = 0
          m = 0
          s = 0
          that.mint = true
        }
        document.getElementById("timer2")
          .innerHTML =
          '<div>' + d + '</div>' +
          '<div>' + h + '</div>' +
          '<div>' + m + '</div>' +
          '<div>' + s + '</div>';

      }

    }
    window.setInterval(updateTimer, 1000);
    window.setInterval(updateTimer2, 1000);
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: white;
  background-color: #222d40;
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 100%;
  gap: 30px;
}

.textsvg {
  /* margin-left: 5%; */
  margin-bottom: 5%;
  width: 450px;
}

body {
  height: 100%;
  margin: 2%;
  overflow-y: hidden;
  background-color: #222d40;
}

.side,
.buttons {
  display: flex;
  /* margin-top: 1%; */
  justify-content: space-around;
  /* gap: 10px; */
  /* padding: 1% 0; */
  align-items: flex-start;
}

.side img {
  width: 60px;
}

.side {
  position: fixed;
  margin: 0 auto;
  /* margin-top: 5%; */
  bottom: 0;
  left: 44%;
}

.buttons img {

  padding: 0 1%;
  width: 100%;
  height: 50px
}

.buttons .classik {

  cursor: pointer;
}

.wrapper {
  display: flex;
  gap: 15%;
}

.logos {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

}

.logos img {
  max-width: 40vw;
  width: 100%;
  margin: 0 auto;
}


.gif {
  width: 400px;
  height: 400px;
}

.discover {
  display: flex;
}

.discover p {
  width: 50%;
  margin-left: 15px;
}

.discover .disc-inner {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

 .mint {
  width: 400px;
  margin-top: 50px;
  cursor: pointer;
  height: 100px;
}

.back {
  position: fixed;
  top: 3%;
  right: 3%;
  cursor: pointer;
  width: 100px;
  height: 100px;
}

.soon {
  margin-right: 500px;
}

.bigbtn {
  width: 400px;
  cursor: pointer;
  /* padding: 10%; */
}

.content_main {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 75vh;
}

.image_main {
  display: flex;
  flex-direction: column;
}

.timer-wrapper {
  display: flex;
  align-items: center;
}

.timer-btn {
  cursor: pointer;
}

.timer-btn img {
  width: 250px;
  margin-left: 50px;
}
.animation_wrapper{
  display: flex;
  flex-direction: column;
}

#timer,
#timer2 {
  font-size: 3em;
  font-weight: 100;
  color: white;
  /* padding: 10% 0; */
  color: white;
  display: flex;
  justify-content: space-between;

}
#timer2{
  margin-top: 50px;
}
#timer div,
#timer2 div {
  display: inline-block;
  min-width: 50px;
  padding: 10px;
  background: #020b43;
  border-radius: 10px;
  border: 2px solid #030d52;
}

#timer div span,
#timer2 div span {
  color: #ffffff;
  display: block;
  margin-top: 15px;
  font-size: .35em;
  font-weight: 400;
  text-align: center;
}
.times{
width: 400px;
}
.timer{
  display: flex;
  justify-content: space-between;
}
.timer img{
width: 80px;
}
</style>
