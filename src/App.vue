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
    <div style="display: flex"> <img v-if="!showLogos" src="./assets/animation.gif" alt="" class="gif">
      <div style="margin: 0 5%">
        <img class="textsvg" v-if="!showDiscover && !showLogos" src="./assets/текст.svg" />
        <img class="bigbtn" v-if="!showDiscover && !showLogos" @click="showDiscover = true; showBack = true"
          src="./assets/discover.svg" alt="">
      </div>

      <div v-if="showDiscover" class="discover">
        <div class="disc-inner">
            <div v-if="!mint" id="timer"></div>

            <div v-if="!mint" id="timer2"></div>
          <img class="mint" :src="count()" alt="" :disabled="!mint">
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
      showGif: false
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
          '<div>' + d + '<span>Days</span></div>' +
          '<div>' + h + '<span>Hours</span></div>' +
          '<div>' + m + '<span>Minutes</span></div>' +
          '<div>' + s + '<span>Seconds</span></div>';

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
          '<div>' + d + '<span>Days</span></div>' +
          '<div>' + h + '<span>Hours</span></div>' +
          '<div>' + m + '<span>Minutes</span></div>' +
          '<div>' + s + '<span>Seconds</span></div>';

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
  display: flex;
  flex-direction: column;
  position: absolute;
  margin: 10%;
  gap: 10px;
  top: 0;
  right: 0;
}

.logos img {
  width: 100%;
  height: 50px;
}

#timer, #timer2 {
  font-size: 3em;
  font-weight: 100;
  color: white;
  /* padding: 10% 0; */
  width: 550px;
  color: white;

}

#timer div, #timer2 div {
  display: inline-block;
  min-width: 50px;
  padding: 10px;
  background: #020b43;
  border-radius: 10px;
  border: 2px solid #030d52;
  margin: 15px;
}

#timer div span, #timer2 div span {
  color: #ffffff;
  display: block;
  margin-top: 15px;
  font-size: .35em;
  font-weight: 400;
}

.gif {
  width: 400px;
  margin-left: 10%;
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
  margin: 50px;
  flex-direction: column;
}

.discover .disc-inner .mint {
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
</style>
