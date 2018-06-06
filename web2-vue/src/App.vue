<template>
  <div id="app">
    <h1>Witaj w systemie!</h1>
     <div v-if="!isAuthenticated">
      <login-form @login="logMeIn($event)"></login-form>
   </div>
    <div v-else>
    <h2>Witaj {{email}}!</h2>
       <main-page @logout="logOut" :username="authenticatedUsername"> </main-page>
    </div> 
</div>
  
 
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";

export default {
  components: { LoginForm},
  name: "app",

  data() {
    return {
      email: "",
      isAuthenticated: false,
      authenticatedUsername:""
    };
  },
  methods: {
    login() {
      this.isAuthenticated = true;
      this.authenticatedUsername = username;
    },
    logout() {
      this.isAuthenticated = false;
      this.authenticatedUsername = "";
    },
    logMeIn(username) {
      this.authenticatedUsername = username;
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: black;
  margin-top: 60px;
}

h1 {
  font-weight: bold;
}
h2 {
  font-weight: normal;
  font-size: large;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
