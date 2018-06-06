<template>
  <div id="app">
    <h1>Witaj w systemie do zapisó na zajęęa</h1>
     <div v-show="!isAuthenticated">
      <login-form @login="login($event)"></login-form>
   </div>
    <div v-show="isAuthenticated">
    
       <page @logout="logout" :username="authenticatedUsername"> </page>
    </div> 
</div>

 
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import Page from "./Page";

export default {
  components: { LoginForm, Page},
  name: "app",

  data() {
    return {
      email: "",
      isAuthenticated: false,
      authenticatedUsername:""
    };
  },
  methods: {
    login(username) {
      this.isAuthenticated = true;
      this.authenticatedUsername = username;
    },
    logout() {
      this.authenticatedUsername = "";
      this.isAuthenticated = false;
    }
    
  }
};
</script>


<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #6b717f;
  margin: 40px auto;
  max-width: 90%;
}
.app-title {
  text-align: center;
}
h1, h2 {
  font-weight: normal;
}
ul {
  padding: 0;
}
a {
  color: #42b983;
}
hr {
  margin: 1rem 0;
}
</style>