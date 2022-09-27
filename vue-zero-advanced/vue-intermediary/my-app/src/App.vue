<template>
  <div id="app">
    <h1>Welcome to the first Vue.js project!⭐</h1>
    <User :lastname="lastname" class="text"/>
    <p>Description: {{desc}} </p>
    <button @click="login">LOGIN</button>
  </div>
</template>

<script>
import User from './components/User.vue'
export default {
  name: 'App',
  components: {
    User,

  },
  data() {
    return {
      lastname: '',
      desc: ''
    }
  },
  methods: {
  login(){
    this.lastname = 'Toledo'
    this.desc = 'This is a test project. Welcome! 🙋‍♂️'
  }
 },
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    }

  #app {
    padding: 8px;
    width: 100vw;
    height: 100vh;
    background: #0e0e0e;
    color: whitesmoke;
    }

  h1 {
    padding: 8px 0;
  }

  .text {
    padding-bottom: 8px;
  }

  button {
    margin: 20px 0;
    padding: 12px 60px;
    font-size: 16px;
    font-weight: 600;
    color: whitesmoke;
    background: none;
    border: 2px solid hotpink;
    border-radius: 4px;
  }

  button:hover {
    color: hotpink;
    border: 2px dotted hotpink;

    transition: .7s;
  }
</style>