<template>
  <div id="app">
    <h1>Witaj w systemie do zapisów na zajęcia</h1>
    
    <div v-show="!isLoggedIn">
      <login-form @login="logMeIn($event)"
      :button-label="'Zaloguj się'"></login-form>
    </div>

    <div v-show="isLoggedIn">
    	<content-page @logOut="logOut" :user="loggedInUser"> </content-page>
    </div>

  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import ContentPage from "./ContentPage";

export default {
  components: {LoginForm, ContentPage},
  data () {
    return {
      email: "",
      isLoggedIn: false,
      loggedInUser:""
    }
  },
  methods: {
    logMeIn(user) {
      this.isLoggedIn = true;
      this.loggedInUser = user;
    },
    logOut() {
      this.isLoggedIn = false;
      this.loggedInUser = '';
    }
  }
}
</script>

<style lang="scss">

</style>
