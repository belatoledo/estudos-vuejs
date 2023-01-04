<template>
  <div id="app">
    <img class="img" src="./assets/cronometro.png" alt="Timer">
    <a class="timer">{{ number }}</a>

    <div class="area-btn">
      <button class="btn" @click="start">{{ btnStart }}</button>
      <button class="btn" @click="clean">CLEAN</button>
    </div>

    <div class="history" v-show="history.length > 0">
      <h4>History</h4>
      <ul>
        <li v-for="item in history" :key="item">Timer paused in {{item}}</li>
      </ul>
      <button @click="history = []">Clean history</button>
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
      history: []
    }
  },
  methods: {
    start() {
      if(this.timer !== null) { 
        clearInterval(this.timer) 
        this.timer = null 
        this.btnStart = 'START'
        
        if(this.ss !== 0) {
        this.history.push(this.number)
        }
      } 
      else {
        this.timer = setInterval(() => { 
          this.initTimer();
        }, 100);
        this.btnStart = 'PAUSE'
      }
    },
    clean() {
      if(this.timer !== null) {
          clearInterval(this.timer)
          this.timer = null
      }
      this.ss = 0
      this.mm = 0
      this.hh = 0
      this.number = 0
      this.btnStart = 'START'
      this.history = []
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
  padding: 6px 12px;
  background: lightseagreen;
  border: none;
  border-radius: 4px;
  font-size: 20px;
  color: aliceblue;
  text-align: center;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
}

.btn:hover {
  background: rgba(32, 178, 171, 0.914);
  transition: .4s ease-in-out;
}

.history {
  margin-top: 30px;
}

ul {
  text-align: left;
  padding: 0;
}

h4 {
  color: white;
}

ul li  {
  margin-top: 4px;
  padding: 12px 48px;
  background-color: rgba(156, 156, 156, 0.1);
  border-radius: 4px;
  list-style: none;
  color: lightseagreen ;
}

.history button {
  padding: 6px 12px;
  border: 0;
  border-radius: 4px;
  background-color: aliceblue;
  font-size: 14px;
  font-weight: bold;
  float: right;
  

}
</style>
