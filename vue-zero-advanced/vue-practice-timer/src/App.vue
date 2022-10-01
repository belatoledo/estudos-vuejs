<template>
  <div id="app">
    <img class="img" src="./assets/cronometro.png" alt="Timer">
    <a class="timer">{{ number }}</a>

    <div class="area-btn">
      <button class="btn" @click="start">{{ btnStart }}</button>
      <button class="btn" @click="clean">CLEAN</button>
    </div>

  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      number: '0',
      timer: null,
      btnStart: 'START',
      ss: 0,
      mm: 0,
      hh: 0,
    }
  },
  methods: {
    start() {
      if(this.timer !== null) { 
        clearInterval(this.timer) 
        this.timer = null 
        this.btnStart = 'START'
      } else {
        this.timer = setInterval(() => { 
          this.initTimer();
        }, 1000);
        this.btnStart = 'PAUSE'
      }
    },
    clean() {

    },
    initTimer() {
      this.ss++
      if(this.ss === 59) {
      // 59 seconds
        this.ss  = 0
        this.mm++
      }
      if(this.mm === 59) {
      //59 minutes
        this.mm = 0
        this.hh++
      }

      let formatNumber = 
      (this.hh < 10 ? '0' + this.hh : this.hh) + ':' 
      + (this.mm < 10 ? '0' + this.mm : this.mm) + ':' 
      + (this.ss < 10 ? '0' + this.ss : this.ss)

      return this.number = formatNumber;
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Ubuntu:wght@400;500&display=swap');
#app {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-family: 'Ubuntu', sans-serif;
}

.img {
  height: 480px;
  width: 420px;
  padding-top: 100px;
}

.timer {
  margin-top: -245px;
  font-size: 70px;
  font-weight: 500;
  color: white ;
}

.area-btn {
  margin-top: 200px;
  display: flex;
}

.btn {
  width: 150px;
  margin: 0 15px;
  padding: 10px;
  background: transparent;
  border: 2px solid lightseagreen;
  border-radius: 4px;
  font-size: 20px;
  color: aliceblue;
  text-align: center;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
}

.btn:hover {
  background: lightseagreen;
  transition: .4s ease-in-out;
}
</style>
