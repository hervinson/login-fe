<template>
  <div id="app">
    <div class="body">
      <div class="container">
        <div class="form">
          <div style="margin: 20px 0; font-size: 20px; font-weight: 600">Login Page</div>
          <form @submit.prevent="login">
            <label for="username">Username: </label>
            <input type="text" id="username" name="username" v-model="username" style="width: 150px">
          <br>
          <br>
            <label for="password">Password: </label>
            <input type="password" id="username" name="password" v-model="password" style="width: 150px">
          <br>
          <br>
            <div style="display: flex; justify-content: center">
              <input type="button" value="Register" @click="register" style="margin-right: 20px"><br>
              <input type="submit" value="Submit">
            </div>
        </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  components: {
  },

  data () {
    return {
      username: '',
      password: ''
    }
  },

  methods: {

    register () {
      axios.post('http://localhost:3000/register',{username: this.username, password: this.password})
      .then(response => {
        alert(response.data)
        console.log(response)
      })
    },

    login () {
      axios.post('http://localhost:3000/login',{username: this.username, password: this.password})
      .then(response => {
        alert(response.data)
        console.log(response)
      })
    }
  }
}
</script>

<style>
html {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.body {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  height: 100%;
}

.form {
  border-radius: 20px;
  padding: 20px;
  background-color: dodgerblue;
  height: 250px;
  width: 250px;
}


</style>
